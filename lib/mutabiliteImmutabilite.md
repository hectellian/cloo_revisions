# Mutabilité et immutabilité

**Par défaut** $\rightarrow$ tout est **mutable** [JAVA]

## Variable

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

