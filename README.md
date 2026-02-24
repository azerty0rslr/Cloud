# Cloud Computing
## Intro
Objectif du cloud : réduction coûts infrastructure, scalabilité et élasticité selon la charge, accessibilité globale des services, MAJ prises en charge par le fournisseur.  
Limites : dépendance à Internet, enjeux de sécurité & conffidentialité, contraintes conformité, risque de surcoûts si mauvaise gourvenance, dépendance vis-à-vis du fournisseur  
Exemple : AWS, Microsoft Azure, Google Cloud Platform  

### Modèles de service Cloud
#### IaaS : Infrastructure as a Service
#### PaaS : Platform as a Service
Le fournisseur gère l'infrastructure, l'OS, le runtime.  
#### SaaS : Software as a Service
exemple : Gmail  
  
SSO : Single Sign On  
CICD : Continus Integration / Continus Delivery  
  
VM Azure : attention à la config, crame de l'argent même si la VM est éteinte  

## Security by Design
D'abord sécurité au début puis le design.  
Principe fondamental de moindre privilège : donner juste ce qu'il faut pour faire qlq chose
- Sécurité par défaut
- Séparation des responsabilités
- Fail Safe Defaults : toujours anticiper la situation de la panne

Philosophie : zéro trust - chaque service est protégé différement 

### SOP - Same Origin Polities 
Mécanisme de sécurité imposé par les navigateurs web qui restreint comment les documents ou scripts chargés depuis une origine peuvent intéragir avec les ressources d'une autre origine.  
exemple : CORS (Cross Origin Resource Sharing) sécurité de navigateur web, norme qui permet aux serveurs d'indiquer toute autre origine que le navigateur devrait autoriser à accéder à la ressource.  
Origine : Définie par le schéma (protocole), l'hôte (domaine) et le port d'une URL. Une origine est donc considérée comme identique uniquement si ces trois éléments correspondent.  
DOM (corps HTML) 
CSP (Content Security Policy) 

### Attaque REDOS
Plus le REGEX est complex plus il a de chance de subir une attaque REDOS  

### Attaque XSS (Cross-Site Scripting)
Objectif - exécution d'un script sur un site qui n'esst pas fait pour. 

## Docker
Création de conteneurs comme des VM mais les VM sont plus isolées  
VM : noyau, BIOS/EFI, programmes de l'OS, applications dans l'OS - accède au matériel de l'hôte (CPU, RAM, Disk, OS - noyau et app)  
Conteneur : même idée que pour la VM mais pour que ce soit plus légé on ne recréer pas de noyau et de BIOS donc uniquement programmes de l'OS et ses app - et le conteneur comme la VM accède au matériel de l'hôte (CPU, RAM, Disk, OS - noyau et app)  
Conteneur a donc un coût moindre que la VM mais le conteneur on ne peut pas le déplacer à chaud contrairement à la VM. Pour les deux on peux les dupliquer avec un template pour la VM et une image pour le conteneur. Pour les VM on peut faire des clônes liés et des clônes complets; pour le conteneur c'est forcément un clône lié.  
Docker est un conteneur spécifique pensé pour les développeurs, on y retrouve donc les images fixe mais si un logiciel plante alors l'image s'éteind. Quand un docker démarre on ne le change pas donc si on mets à jour on détruit la data (même si pas vraiment car on ne mets jamais la data sur le docker, la data est stocké sur l'hôte)  
Dockerfile : image (FROM, ADD, PORT, START -- précision un site web est considéré comme une donnée fixe puisqu'il ne change que lorsqu'on le décide)  
Dockercompose : fichier dans lequel on dit ce qu'il faut pour fonctionner et où tourne quoi  
  
## CI/CD
La CI créer l'image et la dépose pour le CD. 
Le CD prends la Registrie (l'image) de la CI.  



