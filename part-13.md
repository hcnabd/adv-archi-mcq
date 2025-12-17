## 13. Exceptions and Error Handling — Q/R

### Q1. Qu’est-ce qu’une exception ?

**R :** Une interruption détectée par le CPU lui-même, déclenchée par l’exécution d’une instruction fautive ou spéciale.

### Q2. Quelle est la différence fondamentale entre exception et interruption matérielle ?

**R :**

- Exception : interne au CPU, synchrone avec l’instruction
- Interruption matérielle : externe, asynchrone

### Q3. Donne des exemples classiques d’exceptions.

**R :**

- Division par zéro
- Accès mémoire invalide (page fault)
- Instruction illégale
- Débordement arithmétique (selon ISA)

### Q4. À quel moment une exception est-elle détectée ?

**R :** Pendant l’exécution (EI) de l’instruction fautive ou immédiatement après.

### Q5. Une exception est-elle testée en CI comme les interruptions ?

**R :** Logiquement oui, mais elle est prioritaire et liée à l’instruction courante.

### Q6. Pourquoi dit-on que les exceptions sont synchrones ?

**R :** Parce qu’elles sont directement causées par l’instruction en cours.

### Q7. Comment le CPU réagit-il lorsqu’une exception est détectée ?

**R :**

- Stoppe l’instruction fautive
- Sauvegarde le contexte
- Transfère le contrôle à un handler OS

### Q8. Que signifie « transfert de contrôle » dans ce contexte ?

**R :** Le PC est chargé avec l’adresse du handler d’exception.

### Q9. Où se trouve l’adresse du handler d’exception ?

**R :** Dans une table des vecteurs d’exceptions, similaire à celle des interruptions.

### Q10. Le contexte sauvegardé pour une exception est-il identique à celui d’une interruption ?

**R :** Oui : PC, SR, GPRs (minimum requis pour reprise ou terminaison).

### Q11. Quelle est la particularité du PC sauvegardé lors d’une exception ?

**R :** Il peut pointer vers :

- l’instruction fautive
- ou l’instruction suivante (selon si l’exception est reprise possible)

### Q12. Qu’est-ce qu’une exception reprise (restartable exception) ?

**R :** Une exception après laquelle l’instruction peut être ré-exécutée (ex. page fault).

### Q13. Qu’est-ce qu’une exception fatale ?

**R :** Une exception qui ne permet pas de reprendre l’exécution normale (ex. instruction illégale).

### Q14. Comment l’OS décide-t-il de la suite après une exception ?

**R :**

- Corriger le problème (ex. charger une page)
- Reprendre l’exécution
- Terminer le programme
- Signaler une erreur à l’utilisateur

### Q15. Que signifie « signaling error » ?

**R :** Informer l’OS ou le programme qu’une condition anormale s’est produite.

### Q16. Comment une exception signale-t-elle la nature de l’erreur ?

**R :** Via un code d’exception fourni par le CPU.

### Q17. Où ce code d’exception est-il stocké ?

**R :**

- Dans un registre spécial
- Ou implicitement par l’index du vecteur d’exception

### Q18. Que devient le SR lors d’une exception ?

**R :**

- Passage en mode superviseur (S = 1)
- Interruptions souvent masquées (M = 1)

### Q19. Pourquoi les handlers d’exceptions s’exécutent-ils en mode kernel ?

**R :** Parce qu’ils doivent :

- accéder à la mémoire système
- gérer le processus
- contrôler le matériel

### Q20. RTL — séquence simplifiée d’une exception.

**R :**

```
Détection faute (EI)
PUSH PC
PUSH SR
PUSH GPRs
PC ← Exception_Vector[type]
S ← 1
```

### Q21. Quelle est la différence clé entre trap et exception ?

**R :**

- Trap : volontaire (instruction logicielle)
- Exception : involontaire (erreur/fault)

### Q22. Pourquoi les traps sont-ils parfois classés avec les exceptions ?

**R :** Parce qu’ils utilisent le même mécanisme matériel (vecteur, sauvegarde, handler).

### Q23. Une exception peut-elle être masquée par le bit M ?

**R :** Non. Les exceptions critiques ne sont pas masquables.

### Q24. Priorité relative entre exception et interruption matérielle ?

**R :** L’exception a toujours priorité, car elle concerne l’instruction courante.

### Q25. Comment le système reprend-il après une exception corrigée ?

**R :** Par une instruction de retour d’exception, restaurant le contexte.

### Q26. Différence pratique entre retour d’exception et RETURN classique ?

**R :**

- RETURN : restaure PC seulement
- Retour d’exception : restaure PC + SR + GPRs

### Q27. Exemple concret : page fault.

**R :**

- Accès mémoire invalide
- Exception détectée
- OS charge la page manquante
- Instruction est relancée

### Q28. Exemple concret : division par zéro.

**R :**

- Exception détectée
- Handler OS appelé
- Programme terminé ou signal d’erreur envoyé

### Q29. Pourquoi les exceptions sont essentielles à la sécurité système ?

**R :** Elles empêchent :

- accès mémoire illégaux
- exécution de code non autorisé
- corruption du système

### Q30. Résume exception vs interruption en une phrase.

**R :** Une exception est une interruption synchrone et interne, déclenchée par une faute CPU, alors qu’une interruption matérielle est asynchrone et externe.

### Q31. Lien direct avec le cycle d’instruction.

**R :** Les exceptions sont détectées durant EI et traitées via un mécanisme proche du CI, avec transfert immédiat vers le kernel.
