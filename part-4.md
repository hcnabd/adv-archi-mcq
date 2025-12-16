# Cycle d’Instruction (Q/R)

## 1. Introduction

**Q1. Qu’est-ce que le cycle d’instruction ?**
**R :** L’ensemble des étapes qu’un CPU suit pour exécuter une instruction, depuis sa lecture en mémoire jusqu’à sa terminaison et la vérification des interruptions.

**Q2. Quelles sont les phases principales du cycle d’instruction ?**
**R :** FI, DI, FO, EI, CI

* **FI** : Fetch Instruction
* **DI** : Decode Instruction
* **FO** : Fetch Operands / Fetch Operate
* **EI** : Execute Instruction
* **CI** : Check Interrupt

---

## 2. Phases du Cycle

### 2.1 Fetch Instruction (FI)

**Q3. Que fait la phase FI ?**
**R :**

* Le PC (Program Counter) est envoyé dans le MAR (Memory Address Register)
* La mémoire lit l’instruction → stockée dans le MBR (Memory Buffer Register)
* MBR → IR (Instruction Register)
* PC ← PC + 1 (prépare l’adresse de la prochaine instruction)

**Q4. Quel est l’objectif principal de FI ?**
**R :** Charger l’instruction suivante depuis la mémoire dans le CPU.

### 2.2 Decode Instruction (DI)

**Q5. Que se passe-t-il pendant DI ?**
**R :**

* L’IR est décodé
* Les signaux de contrôle nécessaires à l’exécution sont préparés

**Q6. Quel est l’objectif principal de DI ?**
**R :** Préparer le CPU pour savoir quelle opération effectuer et quels registres ou mémoire utiliser.

### 2.3 Fetch Operands / Fetch Operate (FO)

**Q7. Que fait la phase FO ?**
**R :**

* Si les opérandes sont en mémoire : utiliser MAR/MBR pour lire les données
* Si les opérandes sont dans des registres : lire directement depuis les GPRs

**Q8. Quel est l’objectif de FO ?**
**R :** Récupérer toutes les données nécessaires pour exécuter l’instruction.

### 2.4 Execute Instruction (EI)

**Q9. Que se passe-t-il pendant EI ?**
**R :**

* L’ALU effectue l’opération (ADD, SUB, MULT, DIV)
* Ou le CPU effectue un transfert de contrôle (JUMP, CALL)

**Q10. Quel est l’objectif principal de EI ?**
**R :** Effectuer l’opération demandée par l’instruction.

### 2.5 Check Interrupt (CI)

**Q11. Que fait la phase CI ?**
**R :**

* À la fin de EI, vérifier le bit d’interruption (I bit)
* Si le bit est activé, débuter la séquence d’interruption

**Q12. Pourquoi CI est importante ?**
**R :** Permet au CPU de répondre aux interruptions externes ou internes après chaque instruction.

---

## 3. Micro-opérations et Signaux de Timing

**Q13. Que sont les micro-opérations dans le cycle d’instruction ?**
**R :** Petites opérations élémentaires exécutées par le CPU à chaque étape du cycle, comme transférer des données entre registres ou ALU.

**Q14. Exemples de micro-opérations dans FI :**
**R :**

* PC → MAR
* MBR → IR
* PC ← PC + 1

**Q15. Qu’est-ce que les signaux de timing comme Taccess et TRAM ?**
**R :**

* **Taccess** : durée nécessaire pour accéder à une cellule mémoire
* **TRAM** : durée totale d’un accès mémoire (lecture ou écriture)

**Q16. Pourquoi ces signaux de timing sont-ils importants ?**
**R :** Ils permettent de synchroniser les micro-opérations avec la mémoire et éviter les erreurs de lecture/écriture.

**Q17. Ordre général des micro-opérations du cycle d’instruction :**
**R :** FI → DI → FO → EI → CI

---

## 4. Instructions et Exécution

**Q18. Quelles instructions impliquent un transfert de contrôle dans EI ?**
**R :** JUMP, CALL, RET, BRANCH

**Q19. Quelles instructions impliquent des opérations sur ALU dans EI ?**
**R :** ADD, SUB, MULT, DIV, AND, OR, XOR

**Q20. Que se passe-t-il si une interruption est détectée à CI ?**
**R :** Le CPU sauvegarde le contexte courant et exécute le service d’interruption (ISR – Interrupt Service Routine).
