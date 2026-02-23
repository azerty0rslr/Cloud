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


b2ats -- Debian 13 "Trixie" - Génération2 x64
clé ssh : manon-machine-key
