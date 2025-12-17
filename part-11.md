## 11. Subroutines, Calls and Return (Low-Level) — Q/R

### Q1. Qu’est-ce qu’une sous-routine (subroutine) ?

**R :** Un bloc de code réutilisable exécuté via un CALL, puis retour au point d’appel via RETURN.

### Q2. Quel est l’objectif principal d’une sous-routine ?

**R :** Réutilisation du code, structuration du programme et réduction de la duplication.

### Q3. Que fait une instruction CALL au niveau matériel ?

**R :** Sauvegarde l’adresse de retour (PC courant ou PC+1), éventuellement le contexte, puis met à jour le PC vers l’adresse de la sous-routine.

### Q4. Qu’est-ce que l’adresse de retour ?

**R :** L’adresse de l’instruction immédiatement après le CALL.

### Q5. Où peut être sauvegardée l’adresse de retour ?

**R :** Dans un registre spécial (LR), sur la pile (stack) ou dans une zone mémoire dédiée.

### Q6. Quelle est la solution la plus générale pour sauvegarder le PC ?

**R :** La pile, car elle permet les appels imbriqués (nested calls).

### Q7. Pourquoi un simple registre n’est pas suffisant pour les appels imbriqués ?

**R :** Un nouvel appel écraserait l’adresse de retour précédente.

### Q8. Qu’est-ce que la pile (stack) ?

**R :** Une structure mémoire LIFO utilisée pour stocker adresses de retour, paramètres, registres sauvegardés et variables locales.

### Q9. Quel registre gère la pile ?

**R :** Le SP (Stack Pointer).

### Q10. Comment évolue le SP lors d’un PUSH ?

**R :** Il est décrémenté (pile descendante la plus courante), puis l’écriture a lieu.

### Q11. Comment évolue le SP lors d’un POP ?

**R :** La donnée est lue, puis le SP est incrémenté.

### Q12. Séquence RTL typique d’un CALL avec pile.

**R :** `SP ← SP − 1 ; MAR ← SP ; MDR ← PC ; Write ; PC ← adresse_sous_routine`

### Q13. À quel moment le PC sauvegardé correspond-il à PC ou PC+1 ?

**R :** En pratique, on sauvegarde le PC déjà incrémenté (adresse de retour correcte).

### Q14. Que fait l’instruction RETURN ?

**R :** Restaure l’adresse de retour, recharge le PC et reprend l’exécution après le CALL.

### Q15. Séquence RTL typique d’un RETURN avec pile.

**R :** `MAR ← SP ; Read ; MDR ← Mem[MAR] ; PC ← MDR ; SP ← SP + 1`

### Q16. CALL et RETURN modifient-ils les flags (SR) ?

**R :** Non directement, mais le SR peut être sauvegardé/restauré selon le modèle d’appel.

### Q17. Qu’est-ce qu’un protocole d’appel (calling convention) ?

**R :** Un ensemble de règles définissant le passage des paramètres, la sauvegarde des registres, la valeur de retour et la gestion de la pile.

### Q18. Comment peut-on passer des paramètres à une sous-routine ?

**R :** Par registres, par la pile, ou par une combinaison des deux.

### Q19. Exemple de passage de paramètres par registres.

**R :** Paramètres placés dans R100, R101, R102, R103 avant le CALL.

### Q20. Avantage du passage de paramètres par registres.

**R :** Plus rapide et moins d’accès mémoire.

### Q21. Limite du passage par registres.

**R :** Nombre de paramètres limité et conflits possibles avec registres utilisés par la sous-routine.

### Q22. Comment passer des paramètres via la pile ?

**R :** Empiler les paramètres (PUSH), exécuter CALL, puis la sous-routine lit via SP ou FP.

### Q23. Qui nettoie la pile des paramètres ?

**R :** L’appelant (caller-cleanup) ou l’appelé (callee-cleanup), selon la convention.

### Q24. Qu’est-ce qu’un Frame Pointer (FP) ?

**R :** Un registre pointant vers le début du cadre de pile de la fonction courante.

### Q25. Que contient un cadre de pile (stack frame) ?

**R :** Adresse de retour, anciens FP/SP, paramètres, variables locales et registres sauvegardés.

### Q26. Pourquoi sauvegarder des GPRs lors d’un CALL ?

**R :** Pour ne pas détruire les valeurs utilisées par la fonction appelante.

### Q27. Quels registres sont typiquement sauvegardés ?

**R :** Registres non volatils (callee-saved), SR si nécessaire, parfois tous les GPRs.

### Q28. Séquence RTL complète d’un CALL « sûr » (simplifié).

**R :** Sauvegarde des GPRs nécessaires ; sauvegarde SR (optionnel) ; `PUSH PC` ; `PC ← adresse_sous_routine`

### Q29. Séquence RTL complète d’un RETURN « sûr ».

**R :** `POP PC` ; restauration SR ; restauration GPRs ; reprise de l’exécution.

### Q30. Différence entre CALL/RETURN et JUMP.

**R :** JUMP change le PC sans retour ; CALL/RETURN implémente un saut avec mécanisme de retour structuré.

### Q31. Pourquoi CALL/RETURN est fondamental pour les langages de haut niveau ?

**R :** Ils implémentent les fonctions, la récursivité et la modularité du code.

### Q32. Comment la récursivité est-elle possible matériellement ?

**R :** Grâce à la pile, chaque appel empile sa propre adresse de retour et son contexte.

### Q33. Que se passe-t-il si la pile déborde ?

**R :** Stack overflow → écrasement mémoire → comportement indéfini ou crash.

### Q34. Résume CALL/RETURN en une phrase.

**R :** CALL sauvegarde le contexte minimal et transfère le contrôle ; RETURN restaure l’adresse de retour et reprend l’exécution normale.

### Q35. Lien direct avec les interruptions ?

**R :** Une interruption est un CALL matériel automatique avec sauvegarde élargie, et un RETURN via instruction spéciale.
