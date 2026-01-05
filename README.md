# 🧬 Genomic Reads Mapper : Alignement de séquences par K-mers

## 📝 Contexte du Projet
Dans le cadre du cours d'Algorithmique pour la Génomique, ce projet vise à développer une solution de **mapping de séquences courtes (reads)** issues de séquençage haut-débit (type Illumina) sur un génome de référence[cite: 2, 6, 7].

Le défi principal est de gérer les imperfections des données :
* **Erreurs de séquençage** (bruit technique).
* **Variations biologiques** (SNP, indels) par rapport à la référence.

## ⚙️ Méthodologie Algorithmique
[cite_start]Notre approche repose sur l'analyse des **k-mers** (sous-mots de longueur $k$).

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

## 📂 Contenu du Projet

### 💻 Le Code (Jupyter Notebook)
[cite_start]Le notebook contient l'implémentation complète, de l'importation FASTQ avec **Biopython** [cite: 31] jusqu'à l'évaluation.

> ⚠️ *Affichage recommandé via Nbviewer pour visualiser les graphiques interactifs.*
>
> ➡️ **[Voir le Notebook complet (Nbviewer)](VOTRE_LIEN_ICI)**

### 💾 Les Données
Le projet utilise des données simulées pour valider l'algorithme.
* `genome.fasta` : Le génome de référence.
* `reads.fastq` : Les séquences à aligner.
* *Le fichier ZIP complet étant volumineux (>100Mo), il est téléchargeable ici : [Lien vers Google Drive/Releases]*

## 📊 Évaluation & Résultats
[cite_start]Nous avons comparé nos résultats à une **vérité terrain** (fichier BAM fourni)[cite: 44].

* **Précision :** [XX]% des reads correctement alignés.
* [cite_start]**Complexité :** Analyse de la complexité temporelle et du temps de calcul réel[cite: 45].
* [cite_start]**Limites :** Discussion sur les cas de répétitions multiples et les mutations en extrémités de reads[cite: 13, 23].

## 🛠️ Stack Technique
* **Langage :** Python 3
* **Librairies :** Biopython (parsing), Pandas, NumPy.
* **Outil de comparaison :** Fichiers BAM/SAM.

## 👥 Auteurs
Projet réalisé par **[Votre Nom]**, [Nom collègue 1] et [Nom collègue 2].
