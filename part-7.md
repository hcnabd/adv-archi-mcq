## 7. Modes d’adressage (Q/R)

### Q1. Qu’est-ce qu’un mode d’adressage ?

**R :** La règle qui précise comment l’opérande d’une instruction est obtenu (valeur immédiate, registre, adresse directe, adresse indirecte, etc.).

### Q2. Qu’est-ce que le mode immédiat (Immediate) ?

**R :** L’opérande est encodée directement dans l’instruction (constante littérale).

### Q3. Donne un exemple d’instruction immédiate.

**R :** `MOVE 1, R1` — la valeur `1` est fournie par l’instruction et placée dans `R1`.

### Q4. Quels sont les avantages du mode immédiat ?

**R :** Pas d’accès mémoire supplémentaire, rapide, utile pour constantes et initialisations.

### Q5. Quels sont les inconvénients du mode immédiat ?

**R :** Peut augmenter la taille de l’instruction si la constante est grande ; valeur fixée à la compilation.

### Q6. Qu’est-ce que le mode registre (Register) ?

**R :** L’opérande se trouve dans un registre du processeur (GPR).

### Q7. Donne un exemple d’instruction registre.

**R :** `ADD R1, R2` — ajoute le contenu de `R1` à `R2`.

### Q8. Quels sont les avantages du mode registre ?

**R :** Accès très rapide, aucun accès mémoire, idéal pour calculs intermédiaires.

### Q9. Quels sont les inconvénients du mode registre ?

**R :** Nombre limité de registres ; nécessite des copies vers/depuis la mémoire.

### Q10. Qu’est-ce que le mode direct (Direct) ?

**R :** L’instruction contient directement l’adresse mémoire de l’opérande.

### Q11. Donne un exemple d’instruction directe.

**R :** `MOVE A, R1` — charge dans `R1` la valeur stockée à l’adresse `A`.

### Q12. Micro-opérations typiques pour un accès direct (lecture) ?

**R :** `MAR ← addr(A)` → `R/W = 1` → attendre `TRAM` → `MBR ← mémoire` → `R1 ← MBR`.

### Q13. Qu’est-ce que le mode indirect (Indirect) ?

**R :** L’adresse de l’opérande est contenue dans un registre.

### Q14. Donne un exemple d’instruction indirecte.

**R :** `MOVE 1, (R1)` — écrit la valeur `1` à l’adresse mémoire pointée par `R1`.

### Q15. Micro-opérations typiques pour un accès indirect (écriture) ?

**R :** `MBR ← 1` ; `MAR ← R1` ; `R/W = 0` ; attendre `TRAM` ; `mémoire ← MBR`.

### Q16. Quelle est la différence entre adresse et valeur ?

**R :** Adresse = emplacement mémoire ; valeur = contenu stocké à cette adresse.

### Q17. Comment note-t-on la distinction adresse / contenu ?

**R :** `A` ou `@A` = adresse ; `(R1)` ou `[R1]` = contenu mémoire ; immédiat : `1` ou `#1`.

### Q18. Quel mode nécessite le plus d’accès mémoire ?

**R :** Le mode indirect.

### Q19. Quel mode est le plus compact en code ?

**R :** Le mode registre est le plus compact ; l’immédiat peut augmenter la taille si la constante est grande.

### Q20. Rôle des registres selon le mode (résumé)

**R :**

* **Immediate** : constante dans `IR` → registre cible
* **Register** : lecture directe d’un `GPR`
* **Direct** : `MAR ← adresse` → mémoire → `MBR` → registre
* **Indirect** : `MAR ← contenu du registre` → mémoire

### Q21. Micro-opérations pour `MOVE A, R1` (lecture directe)

**R :** `PC→MAR` ; mémoire→`MBR` ; `MBR→IR` ; `PC←PC+1` ; `MAR←addr(A)` ; mémoire→`MBR` ; `R1←MBR`.

### Q22. Micro-opérations pour `MOVE 1, (R1)` (écriture indirecte immédiate)

**R :** `PC→MAR` ; mémoire→`MBR` ; `MBR→IR` ; `PC←PC+1` ; `MBR←1` ; `MAR←R1` ; `R/W=0` ; attendre `TRAM` ; mémoire←`MBR`.

### Q23. Erreurs courantes du mode indirect

**R :** Pointeurs non initialisés, aliasing involontaire, accès mémoire invalide, pertes de performance.

### Q24. Impact du mode d’adressage sur performance et taille

**R :**

* **Registre** : très rapide, faible latence
* **Immédiat** : rapide, mais taille d’instruction plus grande
* **Direct** : un accès mémoire (coût `TRAM`)
* **Indirect** : flexible mais coûteux en accès mémoire et micro-opérations
