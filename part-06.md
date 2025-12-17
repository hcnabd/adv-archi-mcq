# Assembleur : Bases et Exemple (Q/R)

## 1. Introduction

**Q1. Quel est le rôle de l’assembleur ?**
**R :** Traduire les instructions haut niveau (C) en instructions machine compréhensibles par le CPU.

**Q2. Quelles opérations de base existent en assembleur ?**
**R :** MOVE, ADD, SUB, MULT, DIV, JUMP, CALL, RETURN, BE, BLT, BGT.

---

## 2. Instructions et Modes d’Adressage

**Q3. Que fait MOVE A, R1 ?**
**R :** Charge la valeur de la variable A dans le registre R1.

**Q4. Que fait MOVE 1, (R1) ?**
**R :** Stocke la valeur 1 à l’adresse mémoire contenue dans R1.

**Q5. Quels modes d’adressage sont illustrés ?**
**R :** Direct (A), indirect ((R1)), immédiat (valeur constante).

**Q6. Comment écrire C = A + B en assembleur ?**
**R :**

- MOVE A, R1
- ADD B, R1
- MOVE R1, C

---

## 3. Registres et Micro-opérations

**Q7. Quels registres participent à l’exécution d’une instruction ?**
**R :** PC, MAR, MBR, IR, GPR selon l’opération.

**Q8. Que sont les micro‑opérations dans un exemple assembleur ?**
**R :** Les étapes internes exécutées par le CPU pour chaque instruction.

**Q9. Exemple de micro-opérations pour MOVE A, R1 :**
**R :**

- PC → MAR
- Lecture mémoire → MBR
- MBR → IR
- Décode IR
- MAR ← adresse A
- Lecture mémoire → MBR
- MBR → R1

**Q10. Exemple de micro-opérations pour ADD B, R1 :**
**R :**

- PC → MAR
- Lecture mémoire → MBR
- MBR → IR
- Décode IR
- MAR ← adresse B
- Lecture mémoire → MBR
- ALU : R1 + MBR → R1

---

## 4. Instructions de Contrôle

**Q11. Que fait JUMP en assembleur ?**
**R :** Change la valeur du PC pour transférer le flux de contrôle.

**Q12. Que fait CALL ?**
**R :** Sauvegarde le PC actuel et saute à une sous-routine.

**Q13. Que fait RETURN ?**
**R :** Restaure le PC pour revenir après une sous-routine.

**Q14. Que fait BE ?**
**R :** Branche si le résultat précédent est zéro (Z flag = 1).

**Q15. Que fait BLT ?**
**R :** Branche si le résultat précédent est inférieur (N flag ou comparateur).

**Q16. Que fait BGT ?**
**R :** Branche si le résultat précédent est supérieur.

---

## 5. Compréhension et Flux

**Q17. Pourquoi étudier le mapping C → assembleur → micro‑opérations ?**
**R :** Pour comprendre comment les instructions haut niveau sont exécutées par le CPU et la participation des registres.

**Q18. Quel registre contient l’instruction en cours ?**
**R :** IR (Instruction Register).

**Q19. Quel registre contient l’adresse de l’instruction suivante ?**
**R :** PC (Program Counter).

**Q20. Comment le CPU récupère-t-il une donnée depuis la mémoire dans un programme assembleur ?**
**R :** MAR ← adresse, lecture mémoire → MBR, MBR → registre cible.

**Q21. Comment le CPU écrit-il une donnée en mémoire ?**
**R :** MAR ← adresse, MBR ← donnée, écriture mémoire.

**Q22. Pourquoi les micro‑opérations sont-elles synchronisées par l’horloge ?**
**R :** Pour garantir le bon ordre des transferts et calculs.

**Q23. Quel rôle joue l’ALU dans l’exécution d’instructions assembleur ?**
**R :** Effectuer toutes les opérations arithmétiques et logiques.

**Q24. Pourquoi les registres généraux (GPR) sont-ils utilisés ?**
**R :** Pour stocker temporairement les données et résultats intermédiaires, accélérant l’exécution.

**Q25. Quelle est la séquence générale du cycle d’instruction pour une instruction assembleur typique ?**
**R :** FI → DI → FO → EI → CI (PC, MAR, MBR, IR et ALU participent à chaque étape).
