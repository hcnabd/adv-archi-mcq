# Fondamentaux de l’Architecture des Ordinateurs (Q/R)

## 1. Architecture de Von Neumann

**Q1. Qu’est-ce que l’architecture de Von Neumann ?**
**R :** Une architecture dans laquelle les instructions et les données partagent la même mémoire et le même bus.

**Q2. Quelles sont les caractéristiques principales de l’architecture de Von Neumann ?**
**R :**

- Une seule mémoire pour les données et les instructions
- Un bus unique (adresse, données, contrôle)

**Q3. Quel est le principal inconvénient de l’architecture de Von Neumann ?**
**R :** Le goulot d’étranglement de Von Neumann : les instructions et les données ne peuvent pas être lues simultanément.

**Q4. Où utilise-t-on principalement l’architecture de Von Neumann ?**
**R :** Dans les ordinateurs à usage général (PC, ordinateurs portables).

---

## 2. Architecture Harvard

**Q5. Qu’est-ce que l’architecture Harvard ?**
**R :** Une architecture où les instructions et les données utilisent des mémoires et des bus séparés.

**Q6. Quelles sont les caractéristiques principales de l’architecture Harvard ?**
**R :**

- Mémoire programme séparée de la mémoire données
- Bus d’instructions et bus de données distincts

**Q7. Quel est l’avantage principal de l’architecture Harvard ?**
**R :** L’accès simultané aux instructions et aux données, ce qui améliore les performances.

**Q8. Où est utilisée l’architecture Harvard ?**
**R :** Dans les microcontrôleurs et les systèmes embarqués.

---

## 3. Microprocesseur et Microcontrôleur

**Q9. Qu’est-ce qu’un microprocesseur ?**
**R :** Un circuit intégré contenant principalement le CPU, avec la mémoire et les E/S externes.

**Q10. Quelles sont les caractéristiques d’un microprocesseur ?**
**R :**

- Mémoire RAM externe
- Périphériques d’E/S externes
- Conçu pour des programmes volumineux et complexes

**Q11. Qu’est-ce qu’un microcontrôleur ?**
**R :** Un circuit intégré qui regroupe CPU, RAM, mémoire programme et périphériques d’E/S sur une seule puce.

**Q12. Quelles sont les caractéristiques d’un microcontrôleur ?**
**R :**

- Tous les composants sur le même silicium
- Faible consommation d’énergie
- Coût réduit
- Dédié à des tâches spécifiques

**Q13. Donnez des exemples d’utilisation des microprocesseurs.**
**R :** Ordinateurs personnels, serveurs, systèmes haute performance.

**Q14. Donnez des exemples d’utilisation des microcontrôleurs.**
**R :** Systèmes embarqués, objets connectés, électroménager, automobile.

---

## 4. Composants d’un Système Informatique

**Q15. Quels sont les composants de base d’un système informatique ?**
**R :**

- CPU
- Mémoire principale (RAM)
- Entrées/Sorties (E/S)
- Bus système

**Q16. Quel est le rôle du CPU ?**
**R :** Exécuter les instructions des programmes.

**Q17. Quels sont les sous-composants principaux du CPU ?**
**R :**

- UAL (Unité Arithmétique et Logique)
- Unité de contrôle
- Registres

**Q18. Qu’est-ce que la mémoire RAM ?**
**R :** Une mémoire volatile qui stocke les instructions et les données pendant l’exécution.

**Q19. Que représentent les Entrées/Sorties (E/S) ?**
**R :** Les interfaces permettant la communication entre l’ordinateur et l’environnement extérieur.

**Q20. Qu’est-ce qu’un bus système ?**
**R :** Un moyen de communication reliant le CPU, la mémoire et les périphériques.

**Q21. Quels sont les types de bus système ?**
**R :**

- Bus de données
- Bus d’adresses
- Bus de contrôle

---

## 5. Langages de Programmation et Architecture

**Q22. Pourquoi ne programme-t-on pas principalement en assembleur ?**
**R :** Parce que l’assembleur est dépendant du matériel, complexe et difficile à maintenir.

**Q23. Pourquoi utilise-t-on le langage C au lieu de l’assembleur ?**
**R :**

- Niveau d’abstraction plus élevé
- Concentration sur l’algorithme
- Portabilité
- Développement plus rapide

**Q24. Quel est l’inconvénient principal de l’utilisation du langage C ?**
**R :** Moins de contrôle direct sur le matériel et une efficacité légèrement inférieure.

**Q25. Pourquoi le langage C est-il considéré comme un bon compromis ?**
**R :** Il est proche du matériel tout en restant productif et portable.
