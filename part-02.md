# Organisation Interne du CPU (Q/R)

## 1. Vue Générale

**Q1. Que signifie l’organisation interne du CPU ?**
**R :** Elle décrit les blocs matériels internes du processeur et la manière dont ils sont interconnectés pour exécuter les instructions.

**Q2. Qu’est-ce que le datapath (chemin de données) d’un CPU ?**
**R :** L’ensemble des composants matériels qui manipulent et transportent les données à l’intérieur du CPU.

**Q3. Quels éléments composent typiquement le datapath ?**
**R :**

- ALU
- Registres
- Bus internes
- Multiplexeurs
- Connexions vers la mémoire

---

## 2. Unité de Contrôle

**Q4. Qu’est-ce que l’unité de contrôle (Control Unit) ?**
**R :** Le bloc qui commande et coordonne le fonctionnement du datapath en générant les signaux de contrôle.

**Q5. Quel est le rôle principal de l’unité de contrôle ?**
**R :** Décoder les instructions et activer les signaux nécessaires pour exécuter chaque étape.

### 2.1 Unité de contrôle câblée (Hardwired Control)

**Q6. Qu’est-ce qu’une unité de contrôle câblée ?**
**R :** Une unité de contrôle implémentée par des circuits logiques fixes.

**Q7. Quels sont les avantages de l’unité de contrôle câblée ?**
**R :**

- Exécution rapide
- Faible latence

**Q8. Quels sont les inconvénients de l’unité de contrôle câblée ?**
**R :**

- Peu flexible
- Difficile à modifier ou étendre

### 2.2 Unité de contrôle microprogrammée

**Q9. Qu’est-ce qu’une unité de contrôle microprogrammée ?**
**R :** Une unité de contrôle basée sur un microprogramme stocké en mémoire.

**Q10. Quels sont les avantages de l’unité de contrôle microprogrammée ?**
**R :**

- Plus flexible
- Facile à modifier ou à étendre

**Q11. Quels sont les inconvénients de l’unité de contrôle microprogrammée ?**
**R :**

- Plus lente que le contrôle câblé
- Dépend d’une mémoire de microinstructions

---

## 3. ALU (UAL – Unité Arithmétique et Logique)

**Q12. Qu’est-ce que l’ALU (UAL) ?**
**R :** Un circuit du CPU chargé d’exécuter les opérations arithmétiques et logiques.

**Q13. Quelles opérations réalise l’ALU ?**
**R :**

- Addition, soustraction
- Opérations logiques (ET, OU, XOR, NON)
- Comparaisons
- Décalages (shift)

---

## 4. Bus Internes et Connexion Mémoire

**Q14. Que sont les bus internes du CPU ?**
**R :** Des voies de communication qui transportent les données et les signaux entre les blocs internes du processeur.

**Q15. Quel est le rôle des bus internes ?**
**R :** Assurer le transfert des données entre registres, ALU et interfaces mémoire.

**Q16. Comment le CPU est-il connecté à la mémoire ?**
**R :** Via des bus (données, adresses, contrôle) reliant le CPU à la mémoire principale.

---

## 5. Registres du CPU

### 5.1 Registres à usage général

**Q17. Que sont les registres à usage général (GPR – General Purpose Registers) ?**
**R :** Des registres utilisés pour stocker temporairement des données ou résultats intermédiaires.

**Q18. À quoi servent les registres à usage général ?**
**R :** Accélérer l’exécution des instructions en évitant des accès fréquents à la mémoire.

### 5.2 Registres à usage spécial

**Q19. Que sont les registres à usage spécial ?**
**R :** Des registres ayant un rôle précis dans le fonctionnement du CPU.

**Q20. Donnez des exemples de registres à usage spécial.**
**R :**

- Compteur de programme (PC)
- Registre d’instruction (IR)
- Registre d’état / flags
- Pointeur de pile (SP)

**Q21. Quel est le rôle du compteur de programme (PC) ?**
**R :** Contenir l’adresse de la prochaine instruction à exécuter.

**Q22. Quel est le rôle du registre d’instruction (IR) ?**
**R :** Stocker l’instruction en cours d’exécution.

**Q23. Quel est le rôle du registre d’état (flags) ?**
**R :** Indiquer les résultats des opérations (zéro, signe, retenue, débordement).

**Q24. Quel est le rôle du pointeur de pile (SP) ?**
**R :** Pointer vers le sommet de la pile en mémoire.

**Q25. Pourquoi les registres sont-ils plus rapides que la mémoire ?**
**R :** Parce qu’ils sont intégrés directement dans le CPU et accessibles en un minimum de cycles.
