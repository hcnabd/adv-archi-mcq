# Mécanisme d’Accès Mémoire et Signaux de Contrôle (Q/R)

## 1. Introduction

**Q1. Qu’est-ce que le mécanisme d’accès mémoire ?**
**R :** La manière dont le CPU lit et écrit des données dans la RAM en utilisant ses registres internes et des signaux de contrôle.

**Q2. Quels registres sont principalement impliqués dans l’accès mémoire ?**
**R :** MAR (Memory Address Register) et MBR / MDR (Memory Buffer / Data Register).

**Q3. Que contient le MAR ?**
**R :** L’adresse mémoire à laquelle accéder.

**Q4. Que contient le MBR / MDR ?**
**R :** La donnée lue depuis la mémoire ou à écrire en mémoire.

---

## 2. Cycles Mémoire

### 2.1 Cycle de Lecture (Read Cycle)

**Q5. Qu’est-ce que le cycle de lecture ?**
**R :** Séquence où le CPU récupère une donnée depuis la mémoire :

- PC → MAR
- R/W = 1
- Attendre TRAM
- Mémoire → MBR

### 2.2 Cycle d’Écriture (Write Cycle)

**Q6. Que se passe-t-il lors d’un cycle d’écriture ?**
**R :**

- MAR ← adresse
- MBR ← donnée à écrire
- R/W = 0
- Attendre TRAM
- MBR → mémoire

**Q7. Que fait la ligne de contrôle R/W (R/WL) ?**
**R :** Indique si l’opération est une lecture (1) ou une écriture (0).

**Q8. Qu’est-ce que Taccess ?**
**R :** Le temps nécessaire pour accéder à une cellule mémoire.

**Q9. Qu’est-ce que TRAM ?**
**R :** La durée totale d’un cycle mémoire, incluant Taccess et le transfert de données.

**Q10. Pourquoi les signaux de contrôle sont-ils importants ?**
**R :** Ils synchronisent le CPU avec la mémoire pour éviter des lectures ou écritures erronées.

---

## 3. Étapes et Micro-étapes

**Q11. Quelles étapes incluent le cycle de lecture ?**
**R :**

- MAR ← adresse
- R/W = 1
- Attendre TRAM
- MBR ← mémoire

**Q12. Quelles étapes incluent le cycle d’écriture ?**
**R :**

- MAR ← adresse
- MBR ← donnée
- R/W = 0
- Attendre TRAM
- Mémoire ← MBR

**Q13. Quelle est la différence principale entre Taccess et TRAM ?**
**R :**

- Taccess : temps pour accéder à la mémoire
- TRAM : temps total pour le cycle complet

**Q14. Que se passe-t-il si TRAM n’est pas respecté ?**
**R :** Le CPU peut lire ou écrire des données incorrectes, entraînant des erreurs.

**Q15. Comment le CPU sait-il quand la mémoire est prête ?**
**R :** Par le respect des signaux de timing Taccess et TRAM et des micro‑étapes synchronisées par l’horloge.

**Q16. Pourquoi MAR est nécessaire avant chaque accès mémoire ?**
**R :** Pour indiquer la cellule mémoire ciblée.

**Q17. Pourquoi MBR est-il utilisé comme tampon ?**
**R :** Pour stocker temporairement les données lues ou à écrire.

**Q18. Qu’est-ce qui différencie lecture et écriture dans le flux de contrôle ?**
**R :** La valeur de la ligne R/W (1 = lecture, 0 = écriture).

**Q19. Quelles opérations utilisent TRAM ?**
**R :** Toutes les opérations d’accès mémoire : lecture d’instruction, lecture/écriture de données.

**Q20. Quels registres du CPU interagissent avec MAR/MBR pendant l’instruction ?**
**R :** PC, IR et parfois GPR selon l’instruction.

**Q21. Comment le cycle mémoire s’intègre-t-il dans le cycle d’instruction ?**
**R :** Pendant FI et FO, pour lire l’instruction et les opérandes depuis la mémoire.

**Q22. Que se passe-t-il si le CPU tente un accès avant la fin de Taccess ?**
**R :** Les données récupérées peuvent être incorrectes.

**Q23. Comment les micro‑étapes synchronisent-elles la lecture ou écriture ?**
**R :** Chaque micro‑étape est horodatée, assurant le transfert correct vers MAR/MBR et la mémoire.

**Q24. Quels types de mémoire sont concernés par Taccess et TRAM ?**
**R :** RAM principale (volatile) et parfois cache ou ROM pour instructions.

**Q25. Résumez le rôle des signaux et registres mémoire.**
**R :** MAR indique l’adresse, MBR contient les données, R/WL sélectionne lecture/écriture, TRAM/Taccess assurent la synchronisation.
