# Obtendo fields de uma class

Utilizaremos os methods do Class<T> para obter methods

- getField(String name)
Retorna o field com nome especificado, sendo o mesmo publico

- getFields()
Retorna array de fields públicos

- getDeclaredField(String name)
  Retorna o field com nome especificado, sendo o mesmo publico ou privado

- getDeclaredFields()
  Retorna array de fields públicos ou privados

Lembrando para o caso dos privados é preciso manipular o **accessible** para true

ex:

```java
public class Main {
  public static void main(String[] args) throws ClassNotFoundException, NoSuchMethodException, InvocationTargetException, InstantiationException, IllegalAccessException, NoSuchFieldException {

    Pessoa pessoa = new Pessoa("Johanna", "4568954599", "5593988446868");
    Class<?> class1 = Class.forName(pessoa.getClass().getName());


    Constructor constructor = class1.getDeclaredConstructor(String.class, String.class, String.class);
    constructor.setAccessible(true);
    Object o = constructor.newInstance("Marta Kent", "44651231578", "93988776644");
    System.out.println(o instanceof Pessoa);

    Method apresentacao = class1.getDeclaredMethod("apresentacao");
    apresentacao.invoke(o);

    Method printDados = class1.getDeclaredMethod("printDados", String.class, String.class);
    Object invoke = printDados.invoke(o, "123456", "654321");
    System.out.println(invoke);

    Field field = class1.getDeclaredField("nome");
    field.setAccessible(true);
    System.out.println(field.getName() + ": " + field.get(o));


  }
}
```
