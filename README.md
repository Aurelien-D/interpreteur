# Interpréteur HPRIM - Générateur de Rapport d'Analyse

Ce projet est une application de bureau qui utilise l'IA d'OpenAI pour analyser des fichiers de résultats biologiques (`.hpr`, `.hl7`, etc.) et générer un rapport d'interprétation au format Word.

## Fonctionnalités

- Interface graphique simple et intuitive avec Tkinter
- Sécurisation de la clé API OpenAI par chiffrement et via le trousseau du système d'exploitation
- Analyse du contenu des fichiers via un prompt personnalisable (`prompt.txt`)
- Génération d'un rapport `.docx` propre et formaté, basé sur un modèle (`modele_entete.docx`)

## Comment Lancer l'Application

Pour utiliser cette application, vous devez télécharger le code source, configurer votre propre clé API OpenAI, puis compiler l'exécutable vous-même. Voici les étapes détaillées :

### Étape 1 : Prérequis

Assurez-vous d'avoir **Git** et **Python** (version 3.8 ou supérieure) installés sur votre machine.

### Étape 2 : Télécharger le Code Source

Ouvrez un terminal ou une invite de commandes et clonez le dépôt GitHub :

```bash
git clone https://github.com/Aurelien-D/interpreteur.git
cd interpreteur
```

### Étape 3 : Installer les Dépendances

Il est fortement recommandé de créer un environnement virtuel pour isoler les dépendances du projet.

```bash
# Créez un environnement virtuel
python -m venv venv

# Activez-le (sur Windows)
.\venv\Scripts\activate

# (sur macOS/Linux)
source venv/bin/activate

# Installez les librairies nécessaires depuis requirements.txt
pip install -r requirements.txt
```

### Étape 4 : Configurer votre Clé API OpenAI

⚠️ **C'est l'étape la plus importante.** Vous devez utiliser votre propre clé API OpenAI.

Exécutez la commande de configuration suivante :

```bash
python main.py setup
```

Le script vous demandera d'entrer votre clé API, puis un mot de passe pour la chiffrer. Cette opération crée un fichier `config.enc` localement, qui est ignoré par Git et ne quittera jamais votre machine.

### Étape 5 : Compiler l'Application en .exe

Une fois la configuration terminée, utilisez PyInstaller pour créer le fichier exécutable. La commande suivante inclut les fichiers et les hooks nécessaires :

```bash
pyinstaller --onefile --windowed --name "interpreteur" --icon="logo.ico" --add-data="modele_entete.docx;." --add-data="prompt.txt;." --additional-hooks-dir=. main.py
```

### Étape 6 : Lancer l'Application

1. Un nouveau dossier `dist` a été créé. Il contient votre application `interpreteur.exe`
2. Allez dans le dossier `dist`
3. Lancez `interpreteur.exe`

Au premier démarrage, l'application vous demandera le mot de passe que vous avez défini à l'étape 4 pour déchiffrer votre clé API.

## Structure du Projet

```
interpreteur/
├── main.py                 # Fichier principal de l'application
├── requirements.txt        # Dépendances Python
├── prompt.txt             # Prompt personnalisable pour l'IA
├── modele_entete.docx     # Modèle Word pour le rapport
├── logo.ico               # Icône de l'application
├── config.enc             # Fichier de configuration chiffré (généré)
└── dist/                  # Dossier contenant l'exécutable (après compilation)
    └── interpreteur.exe
```

## Sécurité

- Votre clé API OpenAI est chiffrée localement
- Le fichier de configuration chiffré ne quitte jamais votre machine
- Aucune donnée sensible n'est partagée avec le dépôt Git
