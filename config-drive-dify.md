# Guide complet — Connexion Google Drive à Dify (Knowledge Pipeline)

**Projet SamaSante — GET409 · SamaTeam**

Ce guide couvre l'intégralité de la procédure : de la création des identifiants sur Google Cloud Console jusqu'à la publication du pipeline dans Dify.

---

## PARTIE 1 — Google Cloud Console (créer les identifiants OAuth)

### 1.1 Créer/sélectionner un projet

1. Va sur [console.cloud.google.com](https://console.cloud.google.com/)
2. En haut de la page, clique sur le sélecteur de projet
3. Crée un nouveau projet (ex : "SamaSante-Dify") ou réutilise un projet existant

### 1.2 Activer l'API Google Drive

1. Dans le menu, va dans **APIs & Services → Library**
2. Cherche **"Google Drive API"**
3. Clique **Enable / Activer**

### 1.3 Configurer l'écran de consentement OAuth

1. Va dans **APIs & Services → OAuth consent screen**
2. Choisis le type (External, sauf si tu as un Google Workspace organisationnel)
3. Renseigne :
    - Nom de l'application : SamaSante
    - Email de contact
4. Si l'app reste en mode **"Testing"**, ajoute manuellement dans **Test users** l'adresse Gmail du compte qui possède le dossier Drive SamaSante (souvent le compte de l'admin de votre workspace Dify)

### 1.4 Créer les identifiants OAuth (Client ID)

1. Va dans **APIs & Services → Credentials**
2. Clique **Create Credentials → OAuth client ID**
3. Type d'application : **Web application** (⚠️ jamais "Desktop", jamais un fichier JSON de compte de service — le plugin Dify exige des identifiants OAuth Client ID + Client Secret)
4. Dans **Authorized redirect URIs**, ajoute exactement l'URL suivante :
    - Si tu es sur **Dify Cloud** (cloud.dify.ai) : 
        
        ```
        https://cloud.dify.ai/console/api/oauth/plugin/langgenius/google_drive/google_drive/datasource/callback
        ```
        
    - Si tu es en **self-hosted**, remplace le domaine par ton URL console API, en gardant le même chemin après `/console/api/oauth/...`
5. Valide → Google te génère un **Client ID** et un **Client Secret** → copie-les, tu en auras besoin à l'étape 2.3

---

## PARTIE 2 — Installation et configuration côté Dify

### 2.1 Installer les plugins nécessaires

Dans Dify, va dans **Plugins → Marketplace**, cherche et installe :

1. **Google Drive** (`langgenius/google_drive`) — Datasource, permet de parcourir et récupérer des fichiers depuis Drive
2. **Google Drive Trigger** (`langgenius/google_drive_trigger`) — optionnel, utile seulement si tu veux déclencher des actions automatiques sur changement de fichier (pas indispensable pour une simple base de connaissances)
3. **General Chunker** (`langgenius/general_chunker`) — indispensable, c'est ce plugin qui transforme le texte extrait en "Chunks" structurés compatibles avec le nœud Base de connaissances

### 2.2 Autoriser la connexion Google Drive

1. Ouvre le plugin **Google Drive** installé
2. Colle le **Client ID** et le **Client Secret** générés à l'étape 1.4
3. Lance l'autorisation OAuth, connecte-toi avec le compte Google propriétaire du dossier Drive SamaSante, accepte le consentement
4. Vérifie que la connexion apparaît bien dans **Integrations → Source de données** avec un statut "connecté"

⚠️ **Point d'attention (bug connu Dify Cloud)** : sur un workspace à plusieurs membres, seul le membre **admin** qui a créé la connexion peut pleinement l'utiliser ; les autres membres peuvent recevoir une erreur 403. Fais cette configuration avec le compte admin du workspace SamaTeam.

---

## PARTIE 3 — Préparer le fichier sur Google Drive

1. Crée (ou utilise) un dossier dédié sur le Drive, ex : **SamaSante**
2. Dépose ton fichier **CSV** (catalogue produits, ou tout autre document de référence) dans ce dossier
3. Garde ce fichier à jour — c'est tout l'intérêt du système "dynamique" : toute modification future du fichier sur Drive pourra être re-synchronisée dans Dify sans tout reconfigurer

---

## PARTIE 4 — Construire le Knowledge Pipeline dans Dify

### 4.1 Créer une base de connaissances en mode Pipeline

1. Va dans **Knowledge**
2. Choisis l'option de création avec **Pipeline** (pas le mode classique "Create Knowledge" basique)
3. Tu arrives sur le canvas vide avec le nœud **Base de connaissances** déjà présent

### 4.2 Ajouter la source de données

1. Clique **"Ajouter une source de données"**
2. Sélectionne **Google Drive**
3. Navigue dans l'arborescence jusqu'au dossier **SamaSante**
4. Sélectionne le fichier CSV voulu (la sélection précise du fichier se fait soit ici, soit au moment du "Série d'essai" selon la version)

### 4.3 Ajouter le nœud Extracteur de documents

1. Clique sur le **"+"** après le nœud Google Drive
2. Ajoute **"Extracteur de documents"**
3. Dans **Variable d'entrée**, sélectionne le fichier venant de Google Drive (`Google ... {x} file`)
4. Ce nœud produit une variable de sortie nommée **`text`** (le contenu brut extrait du CSV)

### 4.4 Ajouter le nœud General Chunker

1. Clique sur le **"+"** après l'Extracteur de documents
2. Ajoute **"General Chunker"**
3. Configure les champs :

|Champ|Valeur recommandée|Pourquoi|
|---|---|---|
|**Input Content**|Variable `text` issue de l'Extracteur de documents|C'est le texte brut à découper|
|**Delimiter**|`\n`|Une ligne de CSV = un produit = un chunk cohérent|
|**Maximum Chunk Length**|`500`|Largement suffisant pour une ligne produit complète|
|**Chunk Overlap Length**|`50`|Léger chevauchement pour ne pas perdre de contexte|
|**Replace consecutive spaces, newlines and tabs**|`False`|Éviter de fusionner les lignes avant découpage|
|**Delete all URLs and email addresses**|`False`|Pas nécessaire pour un catalogue produits|

4. Ce nœud produit une variable de sortie appelée **`result`**, au format compatible "Chunks" attendu par la Base de connaissances

### 4.5 Configurer le nœud Base de connaissances

1. Clique sur le nœud **Base de connaissances**
2. **Structure de morceaux** : `Généralités` (mode général — cohérent avec un CSV/catalogue produits)
3. **MORCEAUX** : sélectionne la variable **`result`** issue du General Chunker (elle doit maintenant apparaître dans la liste, au lieu de "PAS DE VARIABLE")
4. **Mode d'index** : `Économique`
5. **Nombre de mots-clés par chunk** : `3` (suffisant pour des chunks courts type "1 produit par ligne" — tu pourras monter à 5 plus tard si la recherche manque de précision)
6. **Méthode de récupération** : laisse le réglage par défaut (Indexé), ajustable plus tard selon les résultats de recherche

---

## PARTIE 5 — Tester le pipeline

1. Clique sur **"Série d'essai"** en haut à droite
2. Si demandé, confirme/sélectionne le fichier CSV précis à utiliser pour ce test (navigation dans le Drive)
3. Lance le test
4. Vérifie dans l'onglet **"DERNIÈRE EXÉCUTION"** de chaque nœud :
    - L'Extracteur de documents a bien récupéré le texte du CSV
    - Le General Chunker a bien découpé le texte en chunks lisibles (idéalement un chunk = une ligne produit, pas de coupure au milieu d'une donnée)
    - La Base de connaissances a bien indexé les chunks sans erreur

Si un chunk contient plusieurs produits mélangés ou coupe un produit en deux, ajuste le **Maximum Chunk Length** dans le General Chunker.

---

## PARTIE 6 — Publier le pipeline

1. Clique sur le bouton **"Publier"** en haut à droite (celui qui affichait auparavant "Ce pipeline n'a pas encore été publié")
2. Une fois publié, la base de connaissances devient active et utilisable

---

## PARTIE 7 — Lier la base de connaissances à l'agent SamaSante

1. Va dans ton application/agent (ex : le workflow **Chercheur**)
2. Dans les paramètres de **Context**, clique **Ajouter**
3. Sélectionne ta nouvelle base de connaissances (celle connectée à Drive)
4. Configure le **Retrieval Setting** :
    - **Top K** : nombre de chunks max récupérés par requête (3 à 5 pour commencer)
    - **Score Threshold** : seuil de pertinence, à ajuster selon les tests
5. Teste une question type dans l'agent (ex : "Quel est le prix du Poulet yassa riz ?") et vérifie que la réponse s'appuie bien sur les données du CSV Drive

---

## Récapitulatif visuel du pipeline final

```
Google Drive (source)
        ↓
Extracteur de documents  →  sortie : text
        ↓
General Chunker  →  sortie : result (Chunks)
        ↓
Base de connaissances  →  MORCEAUX = result | Mode = Économique
        ↓
   [Publier]
        ↓
Liée au Context de l'agent Chercheur/Rédacteur
```

---

## Pour mettre à jour les données plus tard

Si tu modifies le CSV directement sur Google Drive (nouveau produit, prix changé) :

1. Retourne dans la base de connaissances Dify
2. Relance une synchronisation/exécution du pipeline sur ce même fichier
3. Les nouveaux chunks remplacent ou s'ajoutent aux anciens selon la configuration — pas besoin de reconstruire tout le pipeline

---

_Document préparé pour le projet SamaSante — GET409 · SamaTeam · UMEF Dakar_