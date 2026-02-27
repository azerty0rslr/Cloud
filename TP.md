# Jour 1
## Azure et création de VM
b2ats -- Debian 13 "Trixie" - Génération2 x64  
clé ssh : manon-machine-key  
<img width="1826" height="825" alt="image" src="https://github.com/user-attachments/assets/ab7b8946-62b1-41e8-b695-84e007e6ac32" />  
Bien éteindre la VM pour ne pas surconsommer  
<img width="1826" height="762" alt="image" src="https://github.com/user-attachments/assets/18299a2d-a6c9-4a05-814d-9e971eba6ce3" />  

# Jour 2
## Connection SSH
Connection  
<img width="993" height="632" alt="image" src="https://github.com/user-attachments/assets/022469d5-ae24-4537-8b35-513dcd1200dd" />  
Connection au SSH : ```ssh mrousseliere@20.199.8.96 -i Downloads\manon-machine-key.pem```  
<img width="1382" height="249" alt="image" src="https://github.com/user-attachments/assets/59e5e63d-2e95-46a7-ac3a-ed9d81c91c85" />  
  
## Site web
Autoriser HTTP en port d'entrée  
<img width="1815" height="728" alt="image" src="https://github.com/user-attachments/assets/c536cc40-313a-466b-b01b-f114fd9d011b" />  
En mettant l'IP privé dans la barre de recherche on a le résultat demandé  
<img width="1819" height="924" alt="image" src="https://github.com/user-attachments/assets/cac50696-a73e-466e-a51a-a7e135c4e542" />  
```
sudo rm /var/www/html/index.html
sudo cp index.php /var/www/html/
```

## Azure
### Azure DevOps
Créer une organisation Azure DevOps  
<img width="583" height="907" alt="image" src="https://github.com/user-attachments/assets/4b2dc4f8-0e3f-417c-a91f-995d7b2265d6" />  
Créer le projet  
<img width="1836" height="719" alt="image" src="https://github.com/user-attachments/assets/d3275d05-8814-41e2-886f-1a8610a82520" />  
<img width="1833" height="725" alt="image" src="https://github.com/user-attachments/assets/1d49e815-d5c6-47cc-95ac-14a434555498" />  
Upload sur Git puis récupérer les infos du dépot local  
<img width="1746" height="734" alt="image" src="https://github.com/user-attachments/assets/6f0f3f55-2df6-4067-9825-84cdb747eeef" />  
```
git remote add origin git@ssh.dev.azure.com:v3/TPAzureMRO/websiteMRO/websiteMRO
git push -u origin --all

// rappel commmandes git
git add .
git commit -m "nom commit"
git push -u origin --all
```  
On génère une clé SSH qu'on ajoute à Azure DevOps  
<img width="571" height="871" alt="image" src="https://github.com/user-attachments/assets/1d43088a-ff1d-4f87-b6b9-b83cd726ad18" />  
On upload toute le projet sur Azure DevOps  
<img width="1841" height="848" alt="image" src="https://github.com/user-attachments/assets/4d23cb43-7d9c-4876-b26c-7bedc32590ef" />  
  
Contenu actuel de src/index.php :  
```php
La connexion est ?
<?php
// Configuration de la connexion à la base de données
$servername = "cloud102-db.mysql.database.azure.com";
$username = "jesuisunadmin";
$password = "ON\\7>Ary~BLT64oj>iVUFO+Q{|(gdfE0";
$dbname = "cloud102-test";
// Création de la connexion avec MySQLi en mode orienté objet
$conn = new mysqli($servername, $username, $password, $dbname);
// Vérification de la connexion
if ($conn->connect_error) {
// En cas d'erreur, afficher un message et arrêter l'exécution
die("Échec de la connexion : "
. $conn->connect_error);
echo("Echec!");
} else {
// En cas de succès, afficher un message de confirmation
echo "Connexion réussie à la base de données MySQL !";
}
// Fermeture de la connexion
$conn->close();
?>
```
  
Contenu actuel de Dockerfile :  
```
# Utiliser l'image officielle PHP avec Apache
FROM php:8.1-apache
# Installer l'extension mysqli pour interagir avec MySQL
RUN docker-php-ext-install mysqli
# Copier le code de votre application dans le répertoire de l'application Apache
COPY ./src /var/www/html/
# Exposer le port 80 pour accéder à l'application via le navigateur
EXPOSE 80
```

### Azure Pipeline
Sur Azure on créer un registre de conteneurs  
<img width="970" height="917" alt="image" src="https://github.com/user-attachments/assets/1c16d5aa-c31c-48b3-92e1-1aeb90680eb9" />  
On retourne sur Azure DevOps pour créer un pipeline  
<img width="1842" height="762" alt="image" src="https://github.com/user-attachments/assets/dbfe5e61-4d99-4b37-bfe4-b240fe604940" />  
<img width="575" height="873" alt="image" src="https://github.com/user-attachments/assets/a6c47ca8-c5fd-49cf-a761-ec139deedbf8" />  
Avec la configuration du cours nous ne pouvons pas poursuivre car pas assez de privilèges :  
<img width="1823" height="628" alt="image" src="https://github.com/user-attachments/assets/32d6dbec-2b7a-46d1-bf65-1616d3f8c09b" />  

## Docker
Commandes build docker :  
```
sudo docker build -t mrousseliereapp:v0.1 .
sudo docker images --all
sudo docker run -p 80:80 mrousseliereapp:v0.1

// Pour supprimer une image
sudo docker image rm nom_de_image
```
Pour lancer le docker ne pas oublier de remove Apache2  
<img width="1474" height="571" alt="image" src="https://github.com/user-attachments/assets/c3c3bf3a-f0f2-4fce-b23d-5149a49699e8" />  
<img width="1466" height="503" alt="image" src="https://github.com/user-attachments/assets/6f651740-fc64-46ad-8ae7-c65240226430" />  
  
Pour débugger ```sudo docker exec -it 86497e07fc4e /bin/sh``` :  
<img width="1257" height="626" alt="image" src="https://github.com/user-attachments/assets/eedaf8aa-68e6-4de3-8864-7c5f2d68e0c9" />  
  
Contenu du docker-compose.yaml : service web (avec le site web) + service data  
```
services:
  web:
    image: mrousseliereapp:v0.1
    restart: always
    ports:
      - 80:80
    depends_on:
      - data

  data:
    image: mariadb
    restart: always
    environment:
      MARIADB_ROOT_PASSWORD: password
```  
<img width="1459" height="552" alt="image" src="https://github.com/user-attachments/assets/5e99fd58-4fb0-4b43-ba58-6ef58b0ac936" />  

# Jour 3
## Docker (suite)
On modifie docker-compose.yaml et index.php de la sorte :  
```docker-compose.yaml```  
```
services:
  web:
    image: mrousseliereapp:v0.2
    restart: always
    ports:
      - 80:80
    depends_on:
      - data

  data:
    image: mariadb
    restart: always
    environment:
      MARIADB_DATABASE: Cloud-MR
      MARIADB_USER: mrousseliere
      MARIADB_PASSWORD: password
      MARIADB_ROOT_PASSWORD: password
```  
  
```index.php```  
```
La connexion est ?
<?php
// Configuration de la connexion à la base de données
$servername = "data";
$username = "mrousseliere";
$password = "password";
$dbname = "Cloud-MR";

// Création de la connexion avec MySQLi en mode orienté objet
$conn = new mysqli($servername, $username, $password, $dbname);

// Vérification de la connexion
if ($conn->connect_error) {
        // En cas d'erreur, afficher un message et arrêter l'exécution
        die("Échec de la connexion : ". $conn->connect_error);
        echo("Echec!");
} else {
// En cas de succès, afficher un message de confirmation
        echo "Connexion réussie à la base de données MySQL !";
}
// Fermeture de la connexion
$conn->close();
?>
```  
  
Grâce au docker-compose et à l'index.php modifiés le site est lié à la BDD :  
```
// arrête l'image en cours
sudo docker compose down -v
sudo docker compose up -d
// lancer le site, s'il ne fait pas le lien avec la BDD faire 
sudo docker compose logs -f
```  
<img width="691" height="235" alt="image" src="https://github.com/user-attachments/assets/761561b3-a0a7-4c44-bb1d-6cd9026fbaec" />  


### Docker Hub
Pour que le monde puisse avoir accès à nos images, on va déployer l'image sur un tree via Docker Hub  
```
// on se connecte
 sudo docker login
// on donne un tag
sudo docker tag mrousseliereapp:v0.2 azerty0rslr/docker-mrousseliere-b2-cloud:v0.2
// on pousse ce tag sur Docker Hub
sudo docker push azerty0rslr/docker-mrousseliere-b2-cloud:v0.2
```  

### Staging build
Attaque possible : compromission par dépôt de source  
Pour les langages compilés on doit modifier le Dockerfile puisqu'il faut copier une image/plusieurs images (qui sera/seront détruite(s)) et créer une nouvelle image où l'on mets tout dans le même docker.  

### Sécurisation
Pour cacher des données privées, on créer un .env qui sera dans le gitignore avec les données privées 
Tout d'abord on modifie ```index.php``` et ```docker-compose.yaml```  
```index.php```  
```
nouveauté 2026 ?
<?php
// Configuration de la connexion à la base de données
$servername = getenv('DATABASEURL');
$username = getenv('DATABASEUSER');
$password = getenv('DATABASEUSERPASSWORD');
$dbname = getenv('DATABASE');

// Création de la connexion avec MySQLi en mode orienté objet
$conn = new mysqli($servername, $username, $password, $dbname);

// Vérification de la connexion
if ($conn->connect_error) {
        // En cas d'erreur, afficher un message et arrêter l'exécution
        die("Échec de la connexion : ". $conn->connect_error);
        echo("Echec!");
} else {
// En cas de succès, afficher un message de confirmation
        echo "Connexion réussie à la base de données MySQL !";
}
// Fermeture de la connexion
$conn->close();
?>
```  
  
```docker-compose.yaml```  
```
services:
  web:
    build: .
    restart: always
    ports:
      - 80:80
    depends_on:
      - data
    volumes:
      - ./src:/var/www/html/
    environment:
      DATABASEURL: ${DATABASEURL}
      DATABASEUSER: ${DATABASEUSER}
      DATABASEUSERPASSWORD: ${DATABASEUSERPASSWORD}
      DATABASE: ${DATABASE}

  data:
    image: mariadb
    restart: always
    environment:
      MARIADB_DATABASE: ${DATABASE}
      MARIADB_USER: ${DATABASEUSER}
      MARIADB_PASSWORD: ${DATABASEUSERPASSWORD}
      MARIADB_ROOT_PASSWORD: ${MARIADB_ROOT_PASSWORD}
```  

Et on a également créé un fichier .env à la racine contenant tout les mots de passe.  

## BDD
Créer une BDD azure, faire se connecter, retourner dans la vm et faire ```mysql -h mrousseliereb22026.mysql.database.azure.com -u mrousseliere -p```  
Puis create database, use database et show database.  
<img width="1468" height="623" alt="image" src="https://github.com/user-attachments/assets/1210b834-3feb-4fcf-b028-cdced11d8ebd" />  
  
# Jour 4
## Pipeline
On installe donc Azure Pipeline, pour cela on configure Docker conformement au contenu du TP  
Ensuite on installe une clé PAC via Azure DevOps  
<img width="811" height="599" alt="image" src="https://github.com/user-attachments/assets/0e6d347d-e961-45e9-9e74-51ee8bce7472" />  
Ensuite on configure les agents en ajoutant une pool d'agent  
<img width="1814" height="897" alt="image" src="https://github.com/user-attachments/assets/597e21f4-c721-4f5b-a4b4-4c84a89f5050" />  
On clic sur la pool qu'on vient de créer et on fait New agent  
<img width="1042" height="912" alt="image" src="https://github.com/user-attachments/assets/2b8e9c57-86b6-43b1-a560-ddc949508b58" />  
Ensuite on créer un dossier en dehors du projet pour gérer les agents  
<img width="1462" height="599" alt="image" src="https://github.com/user-attachments/assets/41a102f4-64c4-4925-a723-3d2bc806c8ed" />  
Après une erreur assez longue à résoudre, j'arrive enfin à lancer config.sh. L'erreur était dû à un fichier docker.list incorrecte.  
<img width="1446" height="688" alt="image" src="https://github.com/user-attachments/assets/4b8ab1bb-9e3d-4da9-a56e-a5e3eabd6d3f" />  
<img width="1454" height="694" alt="image" src="https://github.com/user-attachments/assets/26bcfd9a-b5b8-424a-a731-e2471af9cfa6" />  
Puis on lance l'agent ./run.sh  
<img width="1755" height="788" alt="image" src="https://github.com/user-attachments/assets/f5ef8fee-eef2-4f7a-9ddc-39942215617a" />  
