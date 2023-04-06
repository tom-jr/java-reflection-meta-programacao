# Criando Objeto

De acordo com  o que estudamos anteriormente queremos poder instanciar um objeto de acordo com um entrada dinâmica fornecida por uma aplicação externa.

## Class<T>
- Lista atributos (privados ou não)
- Lista métodos (privados ou não)
- Lista constructors (privados ou não)
- Cria objetos da class em questão

A Class será usado no desenvolvimento da nossa solução.
Nos vamos precisar obter o objeto do tipo Class e para isso usaremos métodos da class Object(mother of all classes)
- Object.getClass: retorna um Class<T> 
- Sintaxe.class(class literal)
- class.forName()

Baixando o projeto iremos class teste instancia de objeto e testaremos os meios de se obter um Class<T>

exemplo classLiteral:
~~~ java
Class<Controller> controllerClassLiteral =  Controle.class;
~~~

exemplo do getClass:
~~~ java
Controller controller = new Controller();
Class<? extends Controller> controllerGetClass = controller.getClass();
~~~

exemplo Class.forName
~~~ java
Class<?> controllerClassForName = Class.forName("fullQualifyName");
~~~


para criar uma instancia do objeto desejado usamos o method new instance

~~~ java
Object controllerObject =  controllerClassLiteral.newInstance();

System.out.println(controllerObject instanceof Controller);
~~~