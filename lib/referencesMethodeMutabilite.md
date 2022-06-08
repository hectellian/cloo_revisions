# Références, méthodes et mutabilité

## Methode

Considérer **immutabilité par défaut**

- Plus simple a analyser
- Moins de bugs
- Thread safe
- Plus facile de changer d’avis

## Reference de fonctions

On peut referencer une fonction d'une instance en utilisant la notation `::`

Par exemple:

```java
Comparator<Item> priceCmp =
  Comparator.comparingInt(Item::price);
```

Il existe aussi d'autres references de fonction tel que:

- reference de constructeur
  - `Foo:: new`
- reference de méthode d'une instance
  - `(range.iterator())::hasNext`
