# Configuration Docker Compose pour Flowise

Ce répertoire contient une configuration Docker Compose simplifiée pour installer et exécuter Flowise.

## Fichiers

*   **`docker-compose.yml`:**  Ce fichier est basé sur la configuration officielle de Flowise, disponible sur leur dépôt GitHub.  Il a été légèrement adapté pour simplifier le déploiement.
*   **`.env`:**  Ce fichier contient les variables d'environnement pour personnaliser l'installation.  Il est *très simplifié* par rapport au fichier `.env` complet de Flowise.  Les variables principales que vous pouvez configurer sont :
    *   `FLOWISE_PORT`:  Le port sur lequel Flowise sera accessible (par exemple, `3000`).  Assurez-vous que ce port est disponible sur votre système.
    *   `FLOWISE_USERNAME`:  Le nom d'utilisateur pour l'administrateur de Flowise.
    *   `FLOWISE_PASSWORD`:  Le mot de passe pour l'administrateur de Flowise.  Choisissez un mot de passe fort et sécurisé.
    *  `FLOWISE_PORT_DB`: le port utilisé par la base de données.
    * Vous pouvez ajouter des options plus avancées si vous le souhaitez.

## Installation

1.  **Prérequis:**
    *   Docker et Docker Compose doivent être installés sur votre système.  Si ce n'est pas le cas, consultez la documentation officielle de Docker pour les instructions d'installation : [https://docs.docker.com/get-docker/](https://docs.docker.com/get-docker/) et [https://docs.docker.com/compose/install/](https://docs.docker.com/compose/install/).
    * Git, pour cloner le dépot

2.  **Cloner le dépôt (si ce n'est pas déjà fait):**

    ```bash
    git clone https://github.com/HoussenMoshine/projets-youtube/tree/main
    cd projets-youtube/flowise

    ```
   (Remplacez `<URL_de_votre_depot>` et `<nom_du_dossier_de_votre_depot>` par l'url et le nom de votre dépot)

3.  **Personnaliser le fichier `.env`:**  Modifiez le fichier `.env` pour définir les valeurs souhaitées pour le port, le nom d'utilisateur et le mot de passe.

4.  **Lancer Flowise :**

    ```bash
    docker-compose up -d
    ```

    Cette commande va :
    *   Télécharger les images Docker nécessaires (si elles ne sont pas déjà présentes sur votre système).
    *   Créer et démarrer les conteneurs Docker en arrière-plan (`-d` signifie "detached").
    *   Configurer le réseau et les volumes nécessaires.

5.  **Accéder à Flowise :**

    Une fois que les conteneurs sont démarrés, vous pouvez accéder à Flowise dans votre navigateur web à l'adresse `http://localhost:<FLOWISE_PORT>`, en remplaçant `<FLOWISE_PORT>` par le port que vous avez défini dans le fichier `.env`.  Connectez-vous avec le nom d'utilisateur et le mot de passe que vous avez spécifiés.

## Arrêt et Suppression

*   **Arrêter Flowise :**

    ```bash
    docker-compose stop
    ```

    Cela arrête les conteneurs, mais conserve les données (la base de données, etc.).

*   **Arrêter et supprimer les conteneurs (et les volumes, si vous voulez tout supprimer):**

    ```bash
    docker-compose down -v
    ```

    L'option `-v` supprime les volumes associés aux conteneurs.  Utilisez cette commande avec précaution si vous avez des données importantes dans Flowise que vous ne voulez pas perdre.  Sans l'option `-v`, les données sont conservées même si vous arrêtez et supprimez les conteneurs.

## Vidéo YouTube

Pour une explication plus détaillée et une démonstration visuelle de l'installation et de la configuration, regardez la vidéo YouTube associée :

*[Ma vidéo Youtube sur l'installation de Flowise via Docker]*  **(https://youtu.be/KOmf3iBYHOo)**

## Dépôt Officiel de Flowise

Pour plus d'informations sur Flowise et pour accéder à la configuration Docker Compose complète, consultez le dépôt officiel :

[Dépot officiel Github de Flowise](https://github.com/FlowiseAI/Flowise)

## Avertissement

Cette configuration est simplifiée et peut ne pas convenir à tous les cas d'utilisation.  Pour une utilisation en production, il est recommandé de consulter la documentation officielle de Flowise et d'adapter la configuration en conséquence.  Assurez-vous de bien comprendre les implications de chaque variable d'environnement avant de la modifier.