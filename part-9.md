## 9. ALU Operations, Flags and Their Effect — Q/R

### Q1. Qu’est-ce que l’ALU ?

**R :** L’Arithmetic Logic Unit est le bloc du CPU qui exécute les opérations arithmétiques et logiques.

### Q2. Quelles sont les entrées principales de l’ALU ?

**R :** Opérande 1 (depuis un registre ou MDR) ; Opérande 2 (registre, MDR ou immédiat) ; Signaux de contrôle (type d’opération).

### Q3. Quelle est la sortie principale de l’ALU ?

**R :** Le résultat de l’opération, envoyé vers un registre ou la mémoire.

### Q4. Quel registre est impacté par l’état de l’ALU ?

**R :** Le SR (Status Register / FLAGS).

### Q5. Quelles opérations arithmétiques de base l’ALU exécute-t-elle ?

**R :** ADD, SUB, MULT, DIV.

### Q6. Quelle est la différence matérielle entre ADD et SUB ?

**R :** ADD : addition directe ; SUB : addition avec le complément à deux du second opérande.

### Q7. MULT et DIV sont-elles toujours réalisées en un cycle ?

**R :** Non, elles sont souvent multi-cycles ou microprogrammées.

### Q8. Que signifie une opération arithmétique signée ?

**R :** Les opérandes sont interprétés en complément à deux.

### Q9. Que signifie une opération arithmétique non signée ?

**R :** Les opérandes sont interprétés comme des entiers positifs binaires.

### Q10. Quel est le rôle du flag Z (Zero) ?

**R :** Il est positionné à 1 si le résultat vaut 0.

### Q11. Quand le flag Z est-il mis à 0 ?

**R :** Quand le résultat est différent de 0.

### Q12. Quel est le rôle du flag N (Negative) ?

**R :** Il reflète le bit de signe du résultat (MSB).

### Q13. Quand N = 1 ?

**R :** Quand le résultat est négatif en arithmétique signée.

### Q14. Quel est le rôle du flag C (Carry) ?

**R :** Indique un report en addition non signée ou un emprunt en soustraction non signée.

### Q15. Le flag C est-il pertinent en arithmétique signée ?

**R :** Non, il est principalement utilisé pour l’arithmétique non signée.

### Q16. Quel est le rôle du flag V (Overflow) ?

**R :** Il indique un débordement en arithmétique signée.

### Q17. Quand y a-t-il overflow en addition signée ?

**R :** Deux positifs → résultat négatif ; Deux négatifs → résultat positif.

### Q18. Quand y a-t-il overflow en soustraction signée ?

**R :** Positif − négatif → résultat négatif ; Négatif − positif → résultat positif.

### Q19. Quelle est la différence clé entre C et V ?

**R :** C = dépassement binaire ; V = dépassement sémantique signé.

### Q20. Quels flags sont mis à jour après une opération ALU ?

**R :** Z, N, C, V (selon l’opération).

### Q21. Les opérations logiques modifient-elles les flags ?

**R :** Oui, généralement Z et N, mais pas toujours C et V.

### Q22. Comment l’ALU reçoit-elle l’ordre d’opération ?

**R :** Via des signaux de contrôle issus de l’unité de commande.

### Q23. Qu’est-ce qu’un signal de contrôle ALU ?

**R :** Un ensemble de bits qui sélectionnent l’opération (ADD, SUB, etc.).

### Q24. Que signifie “side effect” d’une opération ALU ?

**R :** La modification automatique des flags dans le SR.

### Q25. Pourquoi les flags sont-ils essentiels pour les branchements ?

**R :** Parce que les instructions de branchement testent directement les flags.

### Q26. Comment fonctionne l’instruction BE (Branch if Equal) ?

**R :** Elle teste Z = 1.

### Q27. Quelle comparaison est typiquement effectuée avant BE ?

**R :** Une soustraction : A − B.

### Q28. Comment fonctionne BLT (Branch if Less Than) en signé ?

**R :** Elle teste N ≠ V.

### Q29. Pourquoi BLT utilise N et V ?

**R :** Pour corriger les effets de l’overflow signé.

### Q30. Comment fonctionne BGT (Branch if Greater Than) en signé ?

**R :** Elle teste Z = 0 et N = V.

### Q31. Quelle est la logique complète de comparaison signée ?

**R :** Égal : Z = 1 ; Inférieur : N ≠ V ; Supérieur : Z = 0 et N = V.

### Q32. Les comparaisons non signées utilisent quels flags ?

**R :** Principalement C et Z.

### Q33. Exemple : comment tester A < B en non signé ?

**R :** Tester le flag C après A − B.

### Q34. Les flags sont-ils toujours mis à jour ?

**R :** Non, certaines instructions peuvent ne pas affecter le SR.

### Q35. Où sont stockés les flags ?

**R :** Dans le Status Register (SR / FLAGS).

### Q36. Comment le RTL montre la mise à jour des flags ?

**R :** Implicitement lors d’une opération ALU : `R1 ← R1 + R2 ; SR ← {Z,N,C,V}`.

### Q37. Pourquoi les flags font le lien entre ALU et contrôle ?

**R :** Parce qu’ils influencent directement les transferts de contrôle (branches).

### Q38. Résume le rôle de l’ALU en une phrase.

**R :** L’ALU exécute les calculs, produit les résultats et met à jour les flags qui pilotent la logique de contrôle du programme.
