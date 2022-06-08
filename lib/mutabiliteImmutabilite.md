# Mutabilité et immutabilité

La majorité des langages orienté objets ont une approche mutable, c'est-à-dire que les objets sont modifiable après intanciation. Par exemple, dans un tel langage, les variables sont de base modifiable.

A l'inverse, dans l'approche immutable les objets ne peuvent être modifié après avoir été instancié, dans un tel langage on considère qu'il n'y a pas de variable et uniquement des constantes.

## Mutabilité

En *java* **par défaut** $\rightarrow$ tout est **mutable**
Par exemple, un simple variable:

```java
int i = 12; // mutable
```

## Immutabilité

Mot cle `final`

- Rendre une variable/reference **immutable**
- Dans le cas d'une classe $\rightarrow$ ne peux pas etre etendue
- Methode $\rightarrow$ ne peut pas etre redefinie

```java
final int i = 12; //immutable
```

> Ne pourra jamais changer dans le futur

## Copie Conservative

Lorsque l'on travail avec des objets mutable, on a tendance a faire des copies pour eviter les effets de bord

Cette copie doit etre profonde

Avec les objets immutables ceci n'est pas necessaire
