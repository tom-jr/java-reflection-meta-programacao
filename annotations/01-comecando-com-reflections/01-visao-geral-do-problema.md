# Visão geral do Problema

## Cenário de Atuação

Vamos simular uma Interação client-servidor. Onde se realiza uma requisição para nossa web API e nos retornamos dados 
referente ao solicitando no forma XML || JSON.

O problema que vamos resolver em nosso sistema simulado tem soluções existentes na web. De exemplo o professor cita
Xtream, VRaptor e Spring. Nos vamos realizar a nossa própria implementação nesse curso para entender como que por debaixo
dos panos isso funciona. 

### Casos:
1. Determinar a class e o método a ser executado a cada requisição
 Uma solução seria quebrar a string da requisição de tal modo que tenhamos cada parte verificada e assim conseguir determinar
qual serviço de nossa API está designado a tal requisição.

Exemplo de como ficaria essa verificação da URL de requisição. Podemos claramente reparar que esse meio gera um ciclo de
verificações imensa pois o processamento de verificação de paths e subPaths aumenta em função exponencial. Quanto mais paths
e subPaths existirem. Mais demorado será essa verificação. Chamamos essa situação de __*complexidade ciclomática*__ 
~~~ java
String path = "/produto/1";
String[] subPaths = path.replaceFirst("/", "")
                    .split("/");

if (subPaths[0].equals("produto")) { // /produto
    ProdutoController pc = new ProdutoController();

    if (subPaths[1].equals("filtra")) {
        pc.filtra();
    } else if (subPaths[1].equals("lista")) {
        pc.lista();
    } //outro else-if
} else if (subPaths[0].equals("cliente")) { // /cliente
    // ifs aninhados para descobrir o método
} // outros else-if
~~~


2. Determinar o formato de retorno dos recursos solicitados. Precisamos definir como montar nosso XML ou JSON de retorno
que no caso para cada tipo de objeto de retorno um tipo de formação de retorno será necessário. Assim gerando o mesmo 
problema de complexidade ciclomática


Exemplo de verificação para formatar o retorno do objeto. Neste exemplo está sendo gerado um retorno em XML.
~~~ java
Object objeto = // obtenho o objeto
String xml = "";

if (objeto instanceof Produto) {
    Produto produto = (Produto)objeto;
    String nome = produto.getNome();
    double valor = produto.getValor();
    String marca = produto.getMarca();

    xml = "<produto>" +
            "<nome>" + nome + "</nome>" +
            "<valor>" + valor + "</valor>" +
            "<marca>" + marca + "</marca>" +
        "</produto>";

    } else if (objeto instanceof Cliente) {
    // lógica para gerar o XML
} //outros else-if
~~~

Generalizando nosso problema. Nos temos uma entrada na API de dados dinâmicos e temos um retorno de dados dinâmicos.
Nos queremos um serviço que verifique as informações dos dados para tratar seus dados e retornos.

Nos temos no Java a API de reflection para nos auxiliar nesse caso
