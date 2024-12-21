# Mini Compilateur en Flex, Bison et C

Ce projet implémente un mini-compilateur pour un langage personnalisé, conçu avec Flex pour l'analyse lexicale, Bison pour l'analyse syntaxique, et le langage C pour la génération de code intermédiaire. Le compilateur supporte des fonctionnalités avancées .

---

## Fonctionnalités principales

1. **Support de structures complexes :**
   - Variables globales et locales.
   - Déclarations de constantes.
   - Tableaux statiques.

2. **Structures de contrôle :**
   - Boucles `FOR` avec pas personnalisés.
   - Conditions `IF/ELSE` imbriquées.

3. **Opérations de base :**
   - Affectations.
   - Calculs mathématiques (+, -, *, /).

4. **Entrée/Sortie :**
   - Lecture (`READ`) des données utilisateur.
   - Affichage (`WRITE`) des résultats.

5. **Commentaires :**
   - Prise en charge des commentaires au niveau global et local.

6. **Code intermédiaire :**
   - Génération de quadruplets pour représenter les instructions du programme source.

---

## Structure du projet

Le projet est organisé comme suit :

| Fichier         | Description                                                              |
|-----------------|--------------------------------------------------------------------------|
| `lexic.l`       | Analyseur lexical : identifie les mots-clés, identificateurs et symboles. |
| `synta.y`       | Analyseur syntaxique : valide la grammaire et génère des quadruplets.     |
| `Fonctions.h`   | Déclarations des fonctions et structures pour la gestion du compilateur. |
| `Fonctions.c`   | Implémentation des fonctions pour le traitement des instructions.         |
| `commandes.bat` | Script pour compiler et exécuter le programme.                           |

---

## Langage supporté

### Exemple de programme source

```c
VAR_GLOBAL {
    FLOAT F1, F2;
    INTEGER I1, I2, I3, Sum, A, B;
    INTEGER I;
    CHAR C1, C2;
    INTEGER Arr[5];
}

DECLARATION {
    INTEGER J, K;
    CONST INTEGER MAX_SIZE = 100;
    CONST FLOAT PI = 3.1415;
    CONST CHAR INITCHAR = "X";
}

INSTRUCTION {
    F1 = 0.0;
    I1 = 15;
    A = 4;

    FOR (I = 0 : 1 : A) {
        Sum = Sum + I;
    }

    IF (I2 < I1) {
        I2 = 5;
    } ELSE {
        I2 = 0;
    }

    WRITE("Final values of I2:");
    READ(I3);
}
```

---

## Installation et utilisation

### Prérequis

- [Flex](https://github.com/westes/flex)
- [Bison](https://www.gnu.org/software/bison/)
- Compilateur C (e.g., GCC)

### Compilation

1. Clonez ce dépôt dans votre environnement local.
2. Exécutez le script `commandes.bat` ou les commandes suivantes manuellement :

```bash
flex lexic.l
bison -d synta.y
gcc lex.yy.c synta.tab.c Fonctions.c -o mini_compilateur
```

### Exécution

1. Préparez un fichier source (e.g., `programme_source.txt`) avec le langage supporté.
2. Exécutez le compilateur :

```bash
./mini_compilateur < programme_source.txt
```

### Sorties

- Les messages d'analyse lexicale et syntaxique.
- Les quadruplets générés pour représenter le code intermédiaire.

---

## Exemple de code intermédiaire

Voici un extrait des quadruplets générés pour le programme source précédent :

```
*************** Code Intermediaire ***************
_________________________________________________________________
| Operateur | Operande1  | Operande2  | Resultat   |
_________________________________________________________________
| :=        | 0          |            | I          |
| IF<       | I          | A          | L1         |
| +         | Sum        | I          | T1         |
| :=        | T1         |            | Sum        |
| +         | I          | 1          | T2         |
| :=        | T2         |            | I          |
| GOTO      |            |            | L0         |
| L1        |            |            |            |
_________________________________________________________________
```

---

## Détails techniques

1. **Analyse lexicale :**
   - Reconnaissance des mots-clés (`VAR_GLOBAL`, `DECLARATION`, etc.).
   - Identification des identificateurs, types de données et opérateurs.

2. **Analyse syntaxique :**
   - Vérification des structures grammaticales.
   - Détection des erreurs syntaxiques.

3. **Gestion de la table des symboles :**
   - Enregistrement des variables et constantes déclarées.
   - Validation des types lors des affectations.

4. **Génération de quadruplets :**
   - Représentation intermédiaire pour les affectations, calculs, conditions et boucles.

---

## Extensions possibles

- Support des fonctions et des appels de procédure.
- Gestion dynamique de la mémoire pour les tableaux.
- Génération de code machine ou assembleur.

---

## Auteur

Ce projet met en valeur des compétences avancées en compilation, programmation en C, et conception de langages.

---
 

## Contact

Pour toute question ou suggestion, veuillez contacter ahlamghribi77@gmail.com

