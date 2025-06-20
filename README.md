# Interpreteur HPRIM - Générateur de Rapport d'Analyse

Ce projet est une application de bureau qui utilise l'IA d'OpenAI pour analyser des fichiers de résultats biologiques (`.hpr`, `.hl7`) et générer un rapport d'interprétation au format Word.


## Fonctionnalités

* Interface graphique simple et intuitive avec Tkinter.
* Sécurisation de la clé API OpenAI par chiffrement et via le trousseau du système d'exploitation.
*  Analyse du contenu du fichier HPR via un prompt personnalisable.
*  Génération d'un rapport `.docx` propre et formaté, basé sur un modèle.

## Démo (Installation et Utilisation)

1.  **Téléchargement :**
    * Rendez-vous dans la section [**Releases**](https://github.com/VOTRE_NOM_UTILISATEUR/interpreteur-hprim/releases) de ce dépôt.
    * Téléchargez le fichier `interpreteur.exe` de la dernière version.

2.  **Configuration (Première utilisation uniquement) :**
    * Placez `interpreteur.exe` dans un dossier.
    * Ouvrez une invite de commandes (CMD ou PowerShell) dans ce dossier.
    * Exécutez la commande de configuration suivante :
      ```bash
      .\interpreteur.exe setup
      ```
    * L'application vous demandera votre clé API OpenAI, puis un mot de passe pour la chiffrer. Cette opération crée un fichier `config.enc` sécurisé. **Votre clé ne quitte jamais votre machine.**

3.  **Lancement :**
    * Double-cliquez sur `interpreteur.exe` pour lancer l'application.
    *  Entrez le mot de passe que vous avez défini lors de la configuration.
    *  Cliquez sur "Générer Rapport" et sélectionnez votre fichier d'analyse.

## Pour les développeurs

Si vous souhaitez contribuer ou exécuter le projet depuis les sources :

1.  Clonez le dépôt :
    ```bash
    git clone [https://github.com/VOTRE_NOM_UTILISATEUR/interpreteur-hprim.git](https://github.com/VOTRE_NOM_UTILISATEUR/interpreteur-hprim.git)
    cd interpreteur-hprim
    ```
2.  Créez un environnement virtuel et installez les dépendances :
    ```bash
    python -m venv venv
    .\venv\Scripts\activate
    pip install -r requirements.txt
    ```
3.  Suivez l'étape de **Configuration** ci-dessus pour créer votre propre fichier `config.enc` en utilisant `python main.py setup`.
4.  Lancez l'application :
    ```bash
    python main.py
    ```
