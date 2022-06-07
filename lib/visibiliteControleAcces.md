# Visibilité et contrôle d'accès

Visibilite $\rightarrow$ propriété contextuel $\Rightarrow$ dépendante de l'endroit ou on se trouve. On peut voir certains attirbut a un endroit mais pas un autre

Contrôle d'accès $\rightarrow$ notion fortement liée à la visibilité $\Rightarrow$ ce qui ne peut pas etre vu, ne peut pas etre directement accedé

## Modificateurs d'accès

- differents mots-clefs liés à la visibilité et à l'accès
- Control d'accès des membres en Java:
  - `public` $\rightarrow$ accès/utilisation partout
  - `private` $\rightarrow$ acces/utilisation uniquement par les instances de la m classe
  - `default` $\rightarrow$ ($\iff$ aucun mot clé) accès/utilisation uniquement dans le m package
  - `protected` $\rightarrow$ accès/utilisation uniquement dans le m package ou est definie sa classe à l'exception d'une sous-classe de la classe de l'attribut.

## **Recommendations**

- Tout champs $\rightarrow$ `private`
- Moins de méthode `public` possible
- Utilisation de methodes _getter_ et _setter_ pour recuperer des informations `private`

---

- Accès lecture (**getter**) et écriture (**setter**) $\rightarrow$ pratique **systématique déconseillées**:
  - Fuite des détails d'implémentation
  - Contraintes et coordination plus difficile
  - Synchronisation plus difficile
  - cf. [why getter and setter are evil](https://web.archive.org/web/20200729073721/https://www.infoworld.com/article/2073723/why-getter-and-setter-methods-are-evil.html)
- **Recommendations**:
  - retourner des _interfaces_ $\rightarrow$ cacher les details d'implementation
    - Plus simple a modifier si l'on decide de changer un type par exemple
