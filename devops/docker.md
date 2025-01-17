# Docker

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

### la création d'une image docker
Elle est construite à partir d'un fichier appelé Dockerfile, qui contient une série d'instructions permettant de définir l'environnement et les dépendances nécessaires à une application.
L'image est créer grace a docker build:
```
docker build -t nom_image:v1 .
```
-t nom_image:v1 : Cette option permet de taguer l'image avec un nom (ici, nom_image) et une version (v1).
. : Le . représente le contexte de construction, ici le répertoire courant. Cela signifie que Docker va chercher un fichier Dockerfile dans le répertoire courant pour créer l'image.
Si vous avez un répertoire spécifique pour votre projet, vous pouvez le remplacer par le chemin approprié. Par exemple :
```
docker build -t mon_app:v2 ./mon_dossier
```
Voici un exemple de dockerfile:
 ```Dockerfile
# Use the official Node.js image.
FROM node:20-alpine
# Set the working directory inside the container
WORKDIR /app
# Copy package.json and package-lock.json
COPY package*.json ./
# Install dependencies
RUN npm install
# Copy the rest of your application code
COPY . .
# Build the React application
RUN npm run build
# Start the application
CMD ["npm","run", "start"]
```

### l'éxécution d'un container
Se fait grace a docker run,
Lorsque vous exécutez docker run, Docker vérifie si l'image demandée existe localement sur votre machine :

Si l'image existe localement, elle est utilisée directement.
Si l'image n'existe pas localement, Docker la télécharge depuis un registre distant (par défaut, Docker Hub).
```
  docker run hello-world

```
Docker vérifie si l'image hello-world existe localement.
Si ce n'est pas le cas, elle est téléchargée depuis Docker Hub.

Docker attribue un ID unique au conteneur (par exemple, 8d4e1b97e3e2) pour le suivre et interagir avec lui.

Avant de démarrer le conteneur, Docker applique toutes les options spécifiées dans la commande docker run :

Ports : Les ports spécifiés avec -p ou --publish sont mappés.
Volumes : Les volumes spécifiés avec -v ou --mount sont montés.
Variables d'environnement : Les variables spécifiées avec -e ou --env sont définies.
Nom du conteneur : Si un nom est donné avec --name, il est attribué au conteneur.

Docker exécute le processus spécifié dans l'image, souvent défini dans le Dockerfile via :

CMD : Par défaut, commande définie dans l'image.
ENTRYPOINT : Peut définir un point d'entrée obligatoire pour l'image.
Si une commande est passée à docker run, elle remplace la commande définie dans le CMD.

Exemple :
```
docker run ubuntu echo "Bonjour Docker !"
````
Ici, Docker utilise l'image ubuntu, mais exécute la commande echo "Bonjour Docker !" au lieu du CMD par défaut de l'image.

Exécution en mode interactif ou détaché
Interactif : Avec l'option -it, le conteneur démarre en mode interactif (permettant d'interagir avec le terminal).
Exemple :
```
docker run -it ubuntu bash
```
Ici, un conteneur Ubuntu démarre avec un accès direct au shell bash.

Détaché : Avec l'option -d, le conteneur s'exécute en arrière-plan.
Exemple :
```
docker run -d nginx
```

Si le processus du conteneur se termine (par exemple, le script ou la commande s'achève), le conteneur s'arrête automatiquement.
Vous pouvez aussi arrêter manuellement le conteneur avec docker stop suivi de l'ID ou du nom du conteneur.

Exemple complet de commande :
```
docker run -d -p 8080:80 --name mon_nginx nginx
````
Explications :
-d : Exécution en mode détaché (en arrière-plan).
-p 8080:80 : Mappe le port 8080 de l'hôte au port 80 du conteneur.
--name mon_nginx : Attribue le nom mon_nginx au conteneur.
nginx : Utilise l'image nginx pour créer le conteneur.

### l'orchestration de containers avec docker-compose ❌ / ✔️


## 💻 J'utilise

### Un exemple personnel commenté ❌ / ✔️

### Utilisation dans un projet ❌ / ✔️

[lien github](...)

Description :

### Utilisation en production si applicable❌ / ✔️

[lien du projet](...)

Description :

### Utilisation en environement professionnel ❌ / ✔️

Description :

## 🌐 J'utilise des ressources

### Titre

- lien
- description

## 🚧 Je franchis les obstacles

### Point de blocage ❌ / ✔️

Description:

Plan d'action : (à valider par le formateur)

- action 1 ❌ / ✔️
- action 2 ❌ / ✔️
- ...

Résolution :

## 📽️ J'en fais la démonstration

- J'ai ecrit un [tutoriel](...) ❌ / ✔️
- J'ai fait une [présentation](...) ❌ / ✔️
