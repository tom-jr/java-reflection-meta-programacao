# New Instance Constructor

Nesta aula foi demostrado a razão de se usar o método newInstance do Constructor.

No exemplo foi adicionado uma checked exception no construtor usado. Tecnicamente toda e qualquer instancia deste
Objeto deve tratar a exception, relançando-a ou usando bloco try/catch. Mas é algo que não acontece no método
newInstance das instancias a partir da classe Class

Neste exemplo a exception será lança em runtime. O compilador não exigirá o trato da exception. O que não
é interessante para o desenvolvimento
~~~ java
Class<?> class = Class.forName("fullQualifyName");
Object o = class.newInstance();
~~~

