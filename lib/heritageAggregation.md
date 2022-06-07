# [$\leftarrow$](../README.md) Héritage et aggrégation

La plupart des implementations d'heritage sont abstraite $\rightarrow$ mauvaise pratique

- ## Heritage

  - extension d'une classe
  - Java: mot cle `extends`
  - Sous-Classe **herite** de tous les **membres** de sa Super-Classe qui ne sont **pas** `private`

```java
class Foo extemds Bar { /*... */ }
```
>
> - Foo sous-type de Bar
> - Foo recupere une partie des membre de Bar

---

- ## **Aggregation**

  - Membres d’une classe $\rightarrow$ aussi refs vers instances
  - Remplacer l'heritage pur
    - Avoir une interface commune pour les differentes implementations $\rightarrow$ polymorphisme
    - Encapsuler une instance de la classe dont on derive le comportement **aggregation** (ou composition)
