## 10. Branches conditionnelles et inconditionnelles (Q/R)

### Q1. Qu’est-ce qu’une branche (branch) ?

**R :** Une instruction qui modifie le flux d’exécution en mettant à jour le Program Counter (PC) vers une adresse cible (immédiate, relative, ou contenue dans un registre).

### Q2. Qu’est-ce qu’un saut inconditionnel (Unconditional JUMP) ?

**R :** Instruction qui change toujours le PC vers la cible : `PC ← target`.

### Q3. Qu’est-ce qu’une branche conditionnelle ?

**R :** Instruction qui teste des flags dans le SR (Z, N, C, V) et met à jour le PC seulement si la condition est vraie.

### Q4. Donne un exemple de branche conditionnelle classique et sa condition.

**R :** BE : Z = 1 ; BLT : N ≠ V ; BGT : Z = 0 et N = V.

### Q5. Séquence micro-opérationnelle générale d’une branche (fetch → decode → evaluate → act) en RTL.

**R :** `PC → MAR ; Read ; MDR → IR ; PC ← PC + 1 ; Decode IR ; Evaluate condition (lire SR) ; If condition true then PC ← target`

### Q6. Où et quand le PC est-il incrémenté dans le cycle d’instruction ?

**R :** Pendant FI après le chargement de l’instruction : `PC ← PC + 1`. Si la branche est prise, le PC est ensuite remplacé par la cible.

### Q7. Que signifie « fall-through » dans le contexte d’une branche ?

**R :** Chemin d’exécution continu quand la condition est fausse — le CPU exécute l’instruction suivante pointée par le PC.

### Q8. Qu’est-ce que la résolution de cible (branch target resolution) ?

**R :** Calcul/détermination de l’adresse de destination de la branche (IR, PC + offset, registre/mémoire).

### Q9. Quels modes de spécification de la cible existent ?

**R :** Adresse absolue, offset relatif (PC-relative), registre-indirect, mémoire.

### Q10. Quelle différence pratique entre adresse absolue et relative ?

**R :** Relative = position-indépendante, champ offset réduit ; Absolue = adresse complète, fixe.

### Q11. RTL : micro-opérations pour branche conditionnelle avec cible immédiate (PC-relative).

**R :** `PC → MAR ; Read ; MDR → IR ; PC ← PC + 1 ; Decode IR ; If condition holds then PC ← PC + offset`

### Q12. RTL : micro-opérations pour branche conditionnelle avec cible en registre.

**R :** `...fetch & decode... ; If condition holds then PC ← Rk`

### Q13. RTL : micro-opérations pour branche dont la cible est stockée en mémoire.

**R :** `Decode IR ; MAR ← addr_of_target ; Read ; MDR ← Mem[MAR] ; If condition holds then PC ← MDR`

### Q14. Que faut-il vérifier avant d’écrire `PC ← target` ?

**R :** Que la cible a été correctement résolue et que la condition SR est vraie.

### Q15. Comment les flags SR sont-ils utilisés lors d’une branche conditionnelle ?

**R :** L’unité de contrôle lit SR (Z, N, C, V) et applique la logique de condition.

### Q16. Pour un branchement relatif, pourquoi ajouter l’offset au PC post-incrémenté ?

**R :** L’offset est relatif à l’adresse de l’instruction suivante, simplifiant le calcul du saut.

### Q17. Si la condition est fausse, que contient le PC après DI/EI ?

**R :** La valeur PC calculée lors du FI (souvent ancienne_PC + 1).

### Q18. Quelles implications pour IR, MDR, MAR après une branche prise ?

**R :** IR contient l’instruction branche ; MAR/MDR peuvent être réutilisés ; prochain FI lira la nouvelle adresse.

### Q19. Comment les branchements affectent-ils l’architecture pipeline ?

**R :** Créent des contrôle hazards → nécessitent flush, stall, prédiction de branche, ou delay slot.

### Q20. Qu’est-ce qu’un delay slot de branche ?

**R :** Instruction immédiatement suivante exécutée même si la branche est prise, pour pipeline.

### Q21. Comment implémenter CALL (saut avec lien) au micro-niveau ?

**R :** Sauvegarder l’adresse de retour (PC) puis `PC ← target` ; ex. `Push(PC); PC ← target` ou `LR ← PC; PC ← target`.

### Q22. Quelles vérifications de sécurité/intégrité sur la cible ?

**R :** Alignement, accès valide, permissions (user vs kernel).

### Q23. Impact des interruptions sur une branche en cours ?

**R :** Vérification après EI/CI ; branche prise met à jour PC, puis interruption selon ISA.

### Q24. Exemple : micro-opérations pour BE offset = −2.

**R :** `PC → MAR ; Read ; MDR → IR ; PC ← PC + 1 ; Decode IR ; If Z = 1 then PC ← PC + (-2)`

### Q25. Résumé des étapes critiques pour une branche correcte au micro-niveau.

**R :** 1) fetch & PC+1 ; 2) décodage et calcul/lecture de la cible ; 3) évaluation des flags SR ; 4) écriture atomique de PC ← target si condition vraie ; 5) préparer le prochain fetch (ou flush si pipeline).
