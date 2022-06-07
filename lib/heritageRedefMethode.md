# [$\leftarrow$](../README.md) Héritage: redéfinition des méthodes

$\rightarrow$ Mécanisme qui permet à une classe d’obtenir la structure et le comportement de la super classe

Toute classe $\rightarrow$ implémentation par défaut de plusieurs méthodes $\leftarrow$ **Object class hérédité**:

```java
public String toString();
```

```java
public boolean equals();
```

```java
public int hashCode();
```

$\rightarrow$ On peut redefinir une methode heritee.

Java:

- La reference `super` $\rightarrow$ acceder au methodes de la super classe
- Annotation `@Override` $\rightarrow$ redefinition d'un membre de la super classe
  - optionnelle
  - recommendé dans le cadre d'une extension de classe
  - Inutile dans le cas d'une implementation d'interface
