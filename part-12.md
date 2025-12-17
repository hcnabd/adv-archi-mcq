## 12. Interrupts — Q/R (Chapitre clé)

**Q1. Qu’est-ce qu’une interruption ?**

**R :** Un mécanisme matériel/logiciel qui suspend temporairement l’exécution courante pour traiter un événement prioritaire, puis reprend exactement là où le programme s’était arrêté.

---

**Q2. À quel moment précis du cycle d’instruction une interruption est-elle testée ?**

**R :** À la fin de l’exécution de l’instruction, pendant la phase CI (Check Interrupt).

---

**Q3. Pourquoi l’interruption n’est-elle pas traitée en plein milieu d’une instruction ?**

**R :** Pour garantir l’atomicité des instructions et préserver la cohérence de l’état du CPU.

---

**Q4. Que signifie le bit I testé en CI ?**

**R :** Il indique qu’une requête d’interruption est en attente.

---

**Q5. Quelle est la condition minimale pour accepter une interruption ?**

**R :**

- I = 1 (interruption demandée)
- Interruptions non masquées (M = 0)
- CPU dans un état autorisant les interruptions

---

**Q6. Quelle est la toute première action du CPU lorsqu’une interruption est acceptée ?**

**R :** Sauvegarder le contexte du programme interrompu.

---

**Q7. Que signifie « contexte CPU » ?**

**R :** L’ensemble des informations nécessaires pour reprendre l’exécution :

- PC
- SR
- GPRs (registres généraux)

---

**Q8. Où le contexte est-il sauvegardé ?**

**R :** En RAM, généralement via la pile (stack) ou une zone mémoire dédiée.

---

**Q9. Pourquoi sauvegarder le PC ?**

**R :** Pour savoir où reprendre l’exécution après le traitement de l’interruption.

---

**Q10. Pourquoi sauvegarder le SR ?**

**R :** Parce qu’il contient :

- flags (Z, N, C, V)
- bits de contrôle (S, M)
  indispensables à l’état du programme interrompu.

---

**Q11. Pourquoi sauvegarder les GPRs ?**

**R :** Parce que l’Interrupt Handler Routine (IHR) va utiliser des registres et risquer d’écraser les valeurs du programme interrompu.

---

**Q12. Séquence générale de traitement d’une interruption (vue globale).**

**R :**

1. CI : test de l’interruption
2. Sauvegarde du contexte (PC, SR, GPRs)
3. Identification de l’interruption
4. Chargement du contexte du handler
5. Exécution de l’IHR
6. Restauration du contexte sauvegardé
7. Reprise du programme interrompu

---

**Q13. Comment le CPU identifie-t-il l’interruption ?**

**R :** Via un vecteur d’interruption (numéro/index associé à chaque source d’interruption).

---

**Q14. Qu’est-ce qu’un vecteur d’interruption ?**

**R :** Une table mémoire contenant les adresses des handlers d’interruption.

---

**Q15. Comment le PC est-il initialisé pour le handler ?**

**R :** Le PC est chargé avec l’adresse lue dans la table des vecteurs d’interruption.

---

**Q16. Quel est le rôle du bit S (Supervisor) lors d’une interruption ?**

**R :** Le CPU passe en mode superviseur (kernel) pour exécuter du code privilégié.

---

**Q17. Pourquoi le handler s’exécute-t-il en mode superviseur ?**

**R :** Pour :

- accéder au matériel
- gérer la mémoire
- manipuler SR et PC
  sans restrictions utilisateur.

---

**Q18. Quel est le rôle du bit M (Mask) dans le SR ?**

**R :** Il permet de masquer (désactiver) les interruptions.

---

**Q19. Pourquoi masque-t-on les interruptions dans le kernel ?**

**R :** Pour éviter la corruption du contexte lors de sections critiques.

---

**Q20. Que se passe-t-il si M = 1 lors du CI ?**

**R :** L’interruption est ignorée (ou différée).

---

**Q21. Qu’est-ce qu’une Interrupt Handler Routine (IHR) ?**

**R :** Une sous-routine spéciale exécutée pour traiter l’interruption.

---

**Q22. En quoi une interruption ressemble-t-elle à un CALL ?**

**R :**

- Sauvegarde automatique du contexte
- Saut vers une routine
- Retour automatique à la fin

---

**Q23. Quelle est la différence clé entre CALL et interruption ?**

**R :**

- CALL : déclenché par le programme
- Interruption : déclenchée par le matériel ou le système

---

**Q24. RTL — sauvegarde typique du contexte lors d’une interruption.**

**R (schématique) :**

```
PUSH PC
PUSH SR
PUSH GPRs
```

---

**Q25. RTL — chargement du handler.**

**R :**

```
PC ← Vector[interrupt_id]
S ← 1
M ← 1   (souvent)
```

---

**Q26. Que fait l’IHR après avoir traité l’événement ?**

**R :** Elle exécute une instruction de retour d’interruption.

---

**Q27. En quoi le RETURN d’interruption est-il spécial ?**

**R :** Il restaure PC + SR + GPRs, pas seulement le PC.

---

**Q28. RTL — restauration du contexte.**

**R (schématique) :**

```
POP GPRs
POP SR
POP PC
```

---

**Q29. Que se passe-t-il après la restauration du PC ?**

**R :** Le CPU reprend exactement le programme interrompu.

---

**Q30. Quels sont les trois types d’interruptions ?**

**R :**

- Exception : faute interne (division par zéro, accès mémoire invalide)
- Interruption matérielle : I/O, timer, périphériques
- Interruption logicielle (trap) : syscall, instruction illégale

---

**Q31. Quelle est la différence entre exception et interruption matérielle ?**

**R :**

- Exception : synchrone avec l’instruction courante
- Matérielle : asynchrone, externe au flot d’instructions

---

**Q32. Qu’est-ce qu’un trap ?**

**R :** Une interruption volontaire déclenchée par le programme pour demander un service système.

---

**Q33. Pourquoi les traps sont-ils essentiels aux OS ?**

**R :** Ils permettent les appels système depuis le mode utilisateur.

---

**Q34. Qu’est-ce qu’une interruption imbriquée (nested interrupt) ?**

**R :** Une interruption de priorité plus élevée qui interrompt un handler en cours.

---

**Q35. Condition pour autoriser les interruptions imbriquées.**

**R :**

- M = 0 dans le handler
- Priorité de la nouvelle interruption > priorité courante

---

**Q36. Pourquoi utiliser des priorités d’interruptions ?**

**R :** Pour garantir que les événements critiques sont traités en premier.

---

**Q37. Comment les priorités sont-elles implémentées ?**

**R :**

- Matériel (contrôleur d’interruptions)
- Logiciel (gestion dans le kernel)

---

**Q38. Risque principal des interruptions imbriquées ?**

**R :** Dépassement de pile et complexité de restauration du contexte.

---

**Q39. Pourquoi les interruptions sont-elles fondamentales pour un OS ?**

**R :** Elles permettent :

- multitâche
- gestion du temps
- I/O asynchrones
- sécurité système

---

**Q40. Résumé en une phrase.**

**R :** Une interruption est un CALL matériel prioritaire, contrôlé par SR et traité en CI, avec sauvegarde/restauration complète du contexte pour garantir une reprise exacte du programme.
