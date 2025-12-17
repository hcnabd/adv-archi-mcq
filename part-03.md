# Registres du CPU et Modèle du Programmeur (Q/R)

## 1. Modèle du Programmeur

**Q1. Qu’est-ce que le modèle du programmeur (Programmer Model) ?**
**R :** L’ensemble des registres visibles et utilisables par le programmeur pour écrire et comprendre le comportement des programmes.

**Q2. Pourquoi ces registres sont-ils importants ?**
**R :** Ils sont utilisés en RTL, dans le cycle d’instruction et dans la gestion des interruptions.

---

## 2. Compteur de Programme et Registre d’Instruction

**Q3. Qu’est-ce que le PC (Program Counter) ?**
**R :** Le registre qui contient l’adresse de la prochaine instruction à exécuter.

**Q4. Comment évolue le PC ?**
**R :**

- Il s’incrémente automatiquement après chaque instruction
- Il est modifié lors des sauts, appels et interruptions

**Q5. Qu’est-ce que le IR (Instruction Register) ?**
**R :** Le registre qui contient l’instruction actuellement chargée depuis la mémoire.

**Q6. À quoi sert le IR ?**
**R :** À permettre le décodage et l’exécution de l’instruction par l’unité de contrôle.

---

## 3. Registres d’Accès Mémoire

**Q7. Qu’est-ce que le MAR (Memory Address Register) ?**
**R :** Le registre qui contient l’adresse mémoire à lire ou à écrire.

**Q8. Quel est le rôle du MAR ?**
**R :** Envoyer l’adresse vers la mémoire principale lors d’un accès mémoire.

**Q9. Qu’est-ce que le MBR / MDR (Memory Buffer Register / Memory Data Register) ?**
**R :** Le registre qui contient les données lues depuis la mémoire ou à écrire en mémoire.

**Q10. Quelle est la différence entre MAR et MBR ?**
**R :**

- **MAR** : contient une adresse
- **MBR** : contient des données

---

## 4. Registre d’État (SR / FLAGS)

**Q11. Qu’est-ce que le SR (Status Register) ou FLAGS ?**
**R :** Un registre qui contient les indicateurs d’état résultant des opérations du CPU.

**Q12. Quels sont les flags classiques contenus dans le SR ?**
**R :**

- Z (Zero)
- N (Negative)
- C (Carry)
- V (Overflow)

**Q13. À quoi sert le flag Z (Zero) ?**
**R :** Indique que le résultat d’une opération est égal à zéro.

**Q14. À quoi sert le flag N (Negative) ?**
**R :** Indique que le résultat d’une opération est négatif.

**Q15. À quoi sert le flag C (Carry) ?**
**R :** Indique une retenue lors d’une opération arithmétique non signée.

**Q16. À quoi sert le flag V (Overflow) ?**
**R :** Indique un dépassement lors d’une opération arithmétique signée.

---

## 5. Modes de Fonctionnement et Interruptions

**Q17. Qu’est-ce que le bit S (Supervisory mode) ?**
**R :** Un bit indiquant si le CPU s’exécute en mode superviseur (kernel) ou en mode utilisateur.

**Q18. À quoi sert le mode superviseur ?**
**R :** À exécuter des instructions privilégiées (gestion mémoire, interruptions, E/S).

**Q19. Qu’est-ce que le bit M (Mask) ?**
**R :** Un bit indiquant si les interruptions sont masquées (désactivées) ou autorisées.

**Q20. Que se passe-t-il si le bit M est activé ?**
**R :** Les interruptions masquables ne sont pas prises en compte par le CPU.

---

## 6. Registres à Usage Général

**Q21. Que sont les registres à usage général (GPRs) ?**
**R :** Des registres (R1, R2, …) utilisés pour stocker des données et résultats intermédiaires du programme.

**Q22. Pourquoi les GPRs sont-ils essentiels ?**
**R :** Ils permettent une exécution rapide en évitant des accès fréquents à la mémoire.

**Q23. Quelle est la différence entre registres généraux et registres spéciaux ?**
**R :**

- **GPRs** : utilisés par le programme
- **Registres spéciaux** : contrôlent le fonctionnement du CPU

---

## 7. Registres Clés dans l’Exécution

**Q24. Quels registres sont principalement utilisés lors du cycle d’instruction ?**
**R :**

- PC
- MAR
- MBR
- IR

**Q25. Quels registres sont critiques pour la gestion des interruptions ?**
**R :**

- PC
- SR (FLAGS)
- Bit S
- Bit M
