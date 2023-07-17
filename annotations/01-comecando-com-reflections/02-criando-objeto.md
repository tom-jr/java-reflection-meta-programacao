# Criando Objeto

Como estudado anteriormente, queremos poder instanciar um objeto, com base na entrada dinâmica recebida em uma 
requisição por uma aplicação externa.

## Como criar um objeto de acordo com uma entrada dinâmica?

## Class<T>
Usaremos a Class<t> para criar objetos de acordo com um dado dinâmico.

**Propriedades da Class<T>**
- Lista atributos (privados ou não)
- Lista métodos (privados ou não)
- Lista constructors (privados ou não)
- Cria objetos da class em questão

Para seguir com nossa solução, iremos precisar de uma instancia da classe Class. Para conseguirmos essa instancia, 
usaremos a classe **Object** do java.util. A class Object é dita como a mãe de todo objeto Java e ela tem métodos que
retornam **Class**

### Métodos da classe Object que retornam class: 
- Object.getClass: retorna um Class<T>
Neste exemplo temos o retorno de uma class usando o getClass(). a classe MyObject tem o método getClass devido ela ser 
- um objeto, logo ela herda esse método da class mãe Object. Então o method getClass retorna um Class<T> onde T é o tipo
- do objeto que chamou o getClass()

~~~ java
MyObject myObject = new MyObject();
Class<? extends MyObject> = myObject.getClass();
~~~

- Sintaxe.class(class literal)
Na class literal nos chamamos o *.class* de um objeto, o mesmo retornará um Class<T>, onde T será o tipo de objeto em 
questão. Exemplo classLiteral:

~~~ java
Class<MyObject> myObjectClass =  MyObject.class;
~~~

- class.forName()
O Class.forName("fullQualifyName"), onde fullQualifyName é o pacote da class em questão concatenado com seu nome. Ela retorna
uma Class<?>, onde '?' é o tipo do Objeto, que pode ser any objeto, dependendo do fullQualifyName descrito

~~~ java
Class<?> myObject = Class.forName("package.MyObject");
~~~
para criar uma instancia do objeto desejado usamos o method newInstance do Class
usando o literal tem em seu retorno Class<T>, onde T é do tipo do objeto em questão, logo ao usar o newInstance podemos
Tipar o retorno conforme a class em questão

~~~ java
Class<MyObject> myObjectClass =  MyObject.class;

Object obj1 = myObjectClass.newInstance();
      //ou
MyObjectClass obt2 = myObjectClass.newInstance();
~~~

O mesmo seria possível para o Object.getClass() ja que retorna uma Class<? extends T> onde '?' é qualquer objeto que extends
nosso objeto em questão. Isso inclui o proprio objeto.

~~~ java
MyObject myObjectClass = new MyObject();
Class<? extends MyObject> myObjectClass =  myObject.getClass();

Object obj1 = myObjectClass.newInstance();
                //ou
MyObjectClass obt2 = myObjectClass.newInstance();
~~~

~~~ java
//exemplo de instanciação do Class usando o literal Object.class
        Class<Controller> controllerClassLiteral = Controller.class;

        //exemplo de instanciação do Class usando o literal Object.getClass()
        Controller controller =  new Controller();
        Class<? extends Controller> controllerGetClass =  controller.getClass();

        //exemplo de instanciação do Class usando o literal Class.forName("full_qualify_name")
        Class<?> controllerFullQualifierName = Class.forName("br.com.alura.alurator.playground.controle.Controller");
        
        Controller c1 =  controllerClassLiteral.newInstance();
        Controller c2 =  controllerGetClass.newInstance();
        Object c3 =  controllerFullQualifierName.newInstance();

        System.out.println(c1 instanceof Controller);
        System.out.println(c2 instanceof Controller);
        System.out.println(c3 instanceof Controller);
~~~
