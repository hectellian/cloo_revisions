# [$\leftarrow$](../README.md) Généricité et variance

Apres avoir defini une simple classe, pendant l'appel d'une de ses methodes il est possible d'avoir un type different de celui voulu, il est donc
necessaire de tester les instances pour etre sur d'avoir le bon type. Ceci rajoute enormement de code non necessaire et on peut ce perdre facilement.

Viens alors les _generiques_ $\rightarrow$ rajoute une forme de polymorphisme par parametricite permettant d'ajouter un objet d'un certain type

Definition d'une classe avec un generique en Java:

```java
public class Stack<T> { // T n'est connu que a la compilation
...
}
// Declaration d'une stack de strings
Stack<String> stack = new Stack<String>();
```

Autre utilisation $\rightarrow$ Tableau dynamique:

```java
var l = new ArrayList<String>();
```
