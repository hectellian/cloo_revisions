# Identité et Égalité

## **Identite**

- 2 Objets sont **identique** $\iff$ physiquement le m, c-a-d pointer au m endroit, m case memoire (addresse pas valeur)
- Java: Opérateur `==` retourne vrai ssi les 2 refs pointent sur la m instance

---

## **Egalite**

- 2 Obkjets sont **egaux** $\iff$ m valeurs
- Methode `equals`
  - Par défaut $\rightarrow$ m effet que identite
  - Redéfinition $\rightarrow$ pour tester l'égalité entre valeurs

---

## **Code de hachage**

- Valeur numérique calc pour chaque instance
- Si `x.equals(y)` $\Rightarrow$ `x.hashCode()` = `y.hashCode()`
- Redefinition `equals` $\Rightarrow$ redefinition hashCode
- **Criteres**:
  - Aussi rapide que possible
  - m champs que `equals`
  - Repose sur appel à l'autre
  - Retourne des valeurs réparties sur `int`

---

## **Value Object vs Entity**

- 2 types de Objects:
  - **Value Objects**: Definis par la valeur de leur champs
    - si m valeurs $\Rightarrow$ m objet
    - Egalite $\rightarrow$ Toujours redefinir `equals`
  - **Entity Objects**:
    - Definis par la structure de leur champs
    - m objet peut avoir des valeurs différentes au cours du temps
    - Identite
    - Gerer cycle de vie
