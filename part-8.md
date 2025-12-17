## 8. Register Transfer Language (RTL) — Q/R

### Q1. Qu’est-ce que le Register Transfer Language (RTL) ?

**R :** Une notation symbolique utilisée pour décrire les micro-opérations internes du CPU, étape par étape.

### Q2. Pourquoi utilise-t-on le RTL ?

**R :** Pour décrire précisément ce que fait le matériel pendant chaque micro-étape du cycle d’instruction.

### Q3. À quel niveau se situe le RTL ?

**R :** Entre l’assembleur et le matériel :

- Plus bas niveau que l’assembleur
- Plus abstrait que les portes logiques

### Q4. Que décrit exactement une instruction RTL ?

**R :** Un transfert de données ou une opération élémentaire entre registres, ALU et mémoire.

### Q5. Donne un exemple simple d’instruction RTL.

**R :** `PC → MAR` : le contenu du PC est copié dans le MAR.

### Q6. Que signifie la flèche (→) en RTL ?

**R :** Un transfert de données de la source vers la destination.

### Q7. Quelle est la différence entre → et ← en RTL ?

**R :**

- `A → B` : lecture de A, écriture dans B
- `B ← A` : équivalent, notation orientée destination

### Q8. Qu’est-ce qu’une micro-opération ?

**R :** Une opération élémentaire exécutée en un cycle d’horloge (ou micro-cycle).

### Q9. Donne des exemples de micro-opérations RTL.

**R :** `PC → MAR` ; `MDR → IR` ; `R1 ← R1 + R2` ; `PC ← PC + 1`

### Q10. Quels composants apparaissent le plus souvent en RTL ?

**R :** PC, MAR, MDR / MBR, IR, registres généraux (R1, R2, …), ALU.

### Q11. Que représente `R1 ← R1 + R2` en RTL ?

**R :** Une opération ALU : addition de R1 et R2, résultat stocké dans R1.

### Q12. Comment le RTL décrit-il un accès mémoire ?

**R :** En combinant :

- Transfert d’adresse (→ MAR)
- Signal de lecture/écriture
- Transfert de données (MDR ↔ mémoire)

### Q13. Quelle est la notation RTL typique d’une lecture mémoire ?

**R :** `MAR ← adresse` ; `Read` ; `MDR ← Mémoire[MAR]`

### Q14. Quelle est la notation RTL typique d’une écriture mémoire ?

**R :** `MAR ← adresse` ; `MDR ← donnée` ; `Write` ; `Mémoire[MAR] ← MDR`

### Q15. Que signifie explicitement Read en RTL ?

**R :** Activation du signal de lecture mémoire (R/W = 1).

### Q16. Que signifie explicitement Write en RTL ?

**R :** Activation du signal d’écriture mémoire (R/W = 0).

### Q17. Comment RTL représente-t-il l’instruction MOVE ?

**R :** Par un simple transfert de données : `R2 → R1` ; `MDR → R1` ; `R1 → MDR`

### Q18. Donne un RTL typique pour MOVE A, R1.

**R :** `MAR ← addr(A)` ; `Read` ; `MDR ← Mémoire[MAR]` ; `R1 ← MDR`

### Q19. Donne un RTL typique pour MOVE R1, A.

**R :** `MAR ← addr(A)` ; `MDR ← R1` ; `Write` ; `Mémoire[MAR] ← MDR`

### Q20. Comment RTL représente-t-il une opération arithmétique ?

**R :** `R3 ← R1 + R2` ; `R1 ← R1 − R2`

### Q21. Comment RTL représente-t-il un transfert de contrôle (JUMP) ?

**R :** `PC ← adresse_cible`

### Q22. Comment RTL représente-t-il un CALL ?

**R :** Sauvegarde du PC (ex. pile) ; `PC ← adresse_sous_routine`

### Q23. Comment RTL représente-t-il un RETURN ?

**R :** Restauration du PC depuis la pile ; `PC ← valeur_sauvegardée`

### Q24. Que sont les conventions RTL ?

**R :** Une ligne = une micro-opération ; opérations parallèles si non conflictuelles ; accès mémoire nécessite Read ou Write.

### Q25. Peut-on avoir plusieurs transferts RTL en parallèle ?

**R :** Oui, si : registres différents et bus interne non partagé.

### Q26. Pourquoi le RTL est essentiel pour comprendre le cycle d’instruction ?

**R :** Il décrit exactement ce que fait le CPU à chaque phase (FI, DI, FO, EI, CI).

### Q27. Donne le RTL complet du Fetch Instruction.

**R :** `PC → MAR` ; `Read` ; `MDR → IR` ; `PC ← PC + 1`

### Q28. Quels registres participent toujours au Fetch en RTL ?

**R :** PC, MAR, MDR, IR.

### Q29. Comment RTL aide-t-il à comprendre les interruptions ?

**R :** Montre quand le PC est sauvegardé, SR modifié et PC chargé avec le vecteur d’interruption.

### Q30. Quelle est la relation entre RTL et timing (Taccess, TRAM) ?

**R :** Certaines micro-opérations nécessitent d’attendre TRAM avant de passer à la suivante.

### Q31. RTL est-il dépendant de l’architecture ?

**R :** Oui, reflète l’organisation interne exacte du CPU (registres, bus, ALU).

### Q32. Pourquoi les enseignants insistent-ils sur le RTL ?

**R :** Langage universel pour expliquer le fonctionnement interne d’un processeur dans TD et examens.

### Q33. Différence essentielle entre assembleur et RTL ?

**R :** Assembleur = ce que le programmeur écrit ; RTL = ce que le CPU fait réellement.

### Q34. Résume le RTL en une phrase.

**R :** Description micro-architecturale précise des transferts et opérations internes du CPU, cycle par cycle.
