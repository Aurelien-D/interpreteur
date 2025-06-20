Interpreteur HPRIM - Générateur de Rapport d'Analyse
Ce projet est une application de bureau qui utilise l'IA d'OpenAI pour analyser des fichiers de résultats biologiques (.hpr, .hl7) et générer un rapport d'interprétation au format Word.

Fonctionnalités
Interface graphique simple et intuitive avec Tkinter. 
Sécurisation de la clé API OpenAI par chiffrement et via le trousseau du système d'exploitation. 
Analyse du contenu du fichier HPR via un prompt personnalisable (prompt.txt). 
Génération d'un rapport .docx propre et formaté, basé sur un modèle (modele_entete.docx). 
Comment Tester l'Application
Pour tester cette application, vous devez télécharger le code source, configurer votre propre clé API OpenAI, puis compiler l'exécutable vous-même. Voici les étapes détaillées :

Étape 1 : Prérequis
Assurez-vous d'avoir Git et Python (version 3.8 ou supérieure) installés sur votre machine.

Étape 2 : Télécharger le Code Source
Ouvrez un terminal ou une invite de commandes et clonez le dépôt GitHub :

Bash

git clone https://github.com/Aurelien-D/interpreteur.git
cd interpreteur
Étape 3 : Installer les Dépendances
Il est fortement recommandé de créer un environnement virtuel pour isoler les dépendances du projet.

Bash

# Créez un environnement virtuel
python -m venv venv

# Activez-le (sur Windows)
.\venv\Scripts\activate
# (sur macOS/Linux: source venv/bin/activate)

# Installez les librairies nécessaires
pip install -r requirements.txt
(Assurez-vous que votre projet contient bien un fichier requirements.txt)

Étape 4 : Configurer votre Clé API OpenAI
C'est l'étape la plus importante. Vous devez utiliser votre propre clé API OpenAI.

Exécutez la commande de configuration suivante :

Bash

python main.py setup
Le script vous demandera d'entrer votre clé API, puis un mot de passe pour la chiffrer. Cette opération crée un fichier config.enc localement, qui est ignoré par Git et ne quittera jamais votre machine.

Étape 5 : Compiler l'Application en .exe
Une fois la configuration terminée, utilisez PyInstaller (installé via requirements.txt) pour créer le fichier exécutable :

Bash

pyinstaller --onefile --windowed --name "interpreteur" --icon="logo.ico" --add-data="modele_entete.docx;." --add-data="prompt.txt;." main.py
Étape 6 : Lancer l'Application
Un nouveau dossier dist a été créé. Il contient votre application.

Allez dans le dossier dist.
Lancez interpreteur.exe.
Au premier démarrage, l'application vous demandera le mot de passe que vous avez défini à l'étape 4 pour déchiffrer votre clé API.
