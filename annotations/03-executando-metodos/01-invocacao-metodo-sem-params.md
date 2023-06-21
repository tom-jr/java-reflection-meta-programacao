# Invocação de Métodos sem parâmetros

Utilizaremos a class Method para recuperar os métodos de 
uma class.

## Method
- Pode listar os tipos de exceptions que podem ser lançadas
- Tipos de parâmetros que recebe
- Tipo de retorno
- Invocar o método

Com a class Class<?> conseguimos obter o Method. Para obtermos uma instância de
Method podemos usar os métodos da Class<?>

- getMethods():
retorna todos os métodos públicos da class, superclass e interfaces


- getMethod(String nome, Objects...): retorna um método público da class, superclass
 ou interface de acordo com seu nome e tipos de argumentos


- getDeclaredMethods(): retorna todos os métodos públicos ou privados de uma 
class, desconsiderando a superclass e interfaces


- getDeclaredMethod(String nome, Objects...):  retorna um método público ou privado da class
desconsiderando a superclass e interface. De acordo com seu nome e tipos de
argumentos. 

Nas opções declared, quando instanciarmos Method que é de acessibilidade privada
utilizamos **setAccessible(true)**

Para **invocarmos** o method em questão utilizamos o method **invoke()** do Method
passando como arg o construtor da class e um varArg com as class que representam
os parâmetros do método.
