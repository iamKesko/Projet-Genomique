# 🧬 Genomic Reads Mapper : Alignement de séquences par K-mers

## 📝 Contexte du Projet
Dans le cadre du cours d'Algorithmique pour la Génomique, ce projet vise à développer une solution de **mapping de séquences courtes (reads)** issues de séquençage haut-débit (type Illumina) sur un génome de référence.

Le défi principal est de gérer les imperfections des données :
* **Erreurs de séquençage** (bruit technique).
* **Variations biologiques** (SNP, indels) par rapport à la référence.

## ⚙️ Méthodologie Algorithmique
Notre approche repose sur l'analyse des **k-mers** (sous-mots de longueur $k$).

### 1. Structure d'Indexation
Pour gérer efficacement un génome de grande taille ($n > 10^9$ paires de bases), nous avons implémenté une structure de recherche optimisée (Suffix Array) capable de :
* Identifier les occurrences exactes d'un k-mer.
* Calculer son **support** (nombre d'apparitions).

### 2. Stratégie de Mapping
L'algorithme analyse la cohérence des k-mers d'un read pour déterminer sa position :
* **Cas simple :** Alignement unique et ordonné des k-mers.
* **Brin inverse :** Gestion des reads provenant du brin complémentaire.
* **Diagnostic des variations :**
    * Si les k-mers centraux sont manquants mais que le **support est élevé**, il s'agit probablement d'une **variation biologique**.
    * Si le support est faible, il s'agit d'une **erreur de séquençage**.

### 💾 Les Données
Le projet utilise des données simulées pour valider l'algorithme.
* `genome.fasta` : Le génome de référence.
* `reads.fastq` : Les séquences à aligner.
* *Le fichier ZIP complet étant volumineux (>100Mo), il est accesible dans la section Releases*


* **Précision :** [XX]% des reads correctement alignés.
* **Limites :** Discussion sur les cas de répétitions multiples et les mutations en extrémités de reads.

## 🛠️ Stack Technique
* **Langage :** Python 3
* **Librairies :** Biopython (parsing), Pandas, NumPy.

## 👥 Auteurs
BIYIK Kenan, EL HOUMA Mohamed, DEKARI Adil
