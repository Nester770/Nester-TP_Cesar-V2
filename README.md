DOCUMENTATION — TP2
Nester Jorris

Chiffrement de César (Version Sophistiquée)

Objectif
Cette seconde version du TP améliore le programme précédent afin de le rendre plus complet et plus proche d’un vrai outil informatique.
Le programme permet maintenant de chiffrer/déchiffrer un texte ou un fichier tout en ajoutant des mécanismes de suivi d’exécution.

Nouveautés ajoutées
•	Décorateurs (notion avancée Python)
Deux décorateurs ont été implémentés pour enrichir les fonctions sans modifier leur code interne.
`@log_call` : Affiche automatiquement l’appel d’une fonction et ses paramètres.
`@timer` : Mesure le temps d’exécution d’une fonction.

•	Chiffrement amélioré
Contrairement au TP1 :
* conserve les majuscules et minuscules
* ignore les chiffres et la ponctuation
* ne modifie pas les espaces
* fonctionne sur des phrases réelles
Exemple :
Bonjour, Zzz! 123 → Erqmrxu, Ccc! 123

•	Chiffrement de fichiers
Le programme peut maintenant lire et écrire dans des fichiers texte.
Fonctions ajoutées :

* `chiffrer_fichier()`
* `dechiffrer_fichier()`

Fonctionnement :
1. Lire le contenu d’un fichier
2. Appliquer le chiffrement César
3. Écrire le résultat dans un nouveau fichier
Principe du chiffrement
Chaque lettre est transformée en position dans l’alphabet :

A → 0
B → 1
...
Z → 25
Puis :
(position + clé) % 26
Le modulo permet de revenir au début de l’alphabet après Z.
Exemple de test
Message : Bonjour, Zzz! 123
Clé : 3
Résultat chiffré : Erqmrxu, Ccc! 123
Résultat déchiffré : Bonjour

Apports pédagogiques
Cette version introduit des notions plus avancées :

* Décorateurs Python
* Mesure de performance
* Journalisation d’exécution
* Manipulation de fichiers
* Gestion de chaînes réelles

Conclusion
Ce TP montre comment transformer un simple algorithme en outil plus professionnel en ajoutant des fonctionnalités de suivi, d’analyse et de traitement de fichiers, tout en conservant le principe du chiffrement de César.
