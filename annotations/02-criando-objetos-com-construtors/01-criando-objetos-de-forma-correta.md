# Criando objetos de forma correta

nas Aulas anteriores usamos o method __*newInstante()*__ da classe Class<T>. Mas esse method foi depreciado.
O newInstante lança exceções (checked). Exceptions lançadas sem tratamentos obrigatório. O que prejudica nosso trabalho.

## Constructor<T>
Usaremos o Constructor<T> para fazer instancias das nossas classes
Com o constructor podemos:
- Listar todos os tipos de exceções que podem ser lançadas
- Listar todos os tipos de parâmetros do construtor que estamos representando
- Listar quantidade de parâmetros
- Criar o objeto da class em questão

## Como recuperar um tipo constructor?
com a classe Class
- getConstructors() : retorna todos os construtores públicos da class em questão
- getConstructor(Class<?> ...varArgs) varArgs representa os tipos dos parâmetros do construtor da class em questão: 
retornando apenas construtores públicos que tenham o tipo de parâmetros que informamos, não considerando constructors de 
superClass
- getDeclaredConstructors(): retorna todo e qualquer construtor da class em questão independente do modificador de acesso do
construtor (**_public, private, protected, default_**)
- getDeclaredConstructor(Class<T> ... varArgs): retorna o Constructor da class em questão que tenha parâmetros igual a que 
informamos nos args seja de qualquer modificador de acesso e desconsiderando superClass

Caso tentarmos manipular construtores privados será lançado exceções de AccessIlegal. Usaremos o método setAccessible(true)
para poder liberar acesso ao constructor em questão

o constructor tbm tem seu método **_newInstance_** ele que usaremos para criar instancias.