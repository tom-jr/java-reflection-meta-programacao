# Criando Annotations


Estrutura inicial de uma annotation
```java
package br.com.alura.alurator.playground.annotations;

public @interface NomeTag {
}
```

Adicionamos uma metaAnnotation para definir em que momento essa annotation é considerada pela JVM. Neste caso ela esta
sendo considerada em tempo de execução, onde justamente utilizaremos. 
```java
package br.com.alura.alurator.playground.annotations;

import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;

@Retention(RetentionPolicy.RUNTIME)
public @interface NomeTag {
}
```

Estamos adicionando outra metaAnnotation para definir onde essa annotation pode ser aplicada em um elemento Java.
```java
package br.com.alura.alurator.playground.annotations;

import java.lang.annotation.ElementType;
import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;
import java.lang.annotation.Target;

@Retention(RetentionPolicy.RUNTIME)
@Target({ElementType.TYPE, ElementType.FIELD})
public @interface NomeTag {
}
```
