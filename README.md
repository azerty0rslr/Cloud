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

## TP
b2ats -- Debian 13 "Trixie" - Génération2 x64  
clé ssh : manon-machine-key  
<img width="1826" height="825" alt="image" src="https://github.com/user-attachments/assets/ab7b8946-62b1-41e8-b695-84e007e6ac32" />  
Bien éteindre la VM pour ne pas surconsommer  
<img width="1826" height="762" alt="image" src="https://github.com/user-attachments/assets/18299a2d-a6c9-4a05-814d-9e971eba6ce3" />  
  
Connection  
<img width="993" height="632" alt="image" src="https://github.com/user-attachments/assets/022469d5-ae24-4537-8b35-513dcd1200dd" />  
Connection au SSH : ```ssh mrousseliere@20.199.8.96 -i Downloads\manon-machine-key.pem```  
<img width="1382" height="249" alt="image" src="https://github.com/user-attachments/assets/59e5e63d-2e95-46a7-ac3a-ed9d81c91c85" />  
Autoriser HTTP en port d'entrée  
<img width="1815" height="728" alt="image" src="https://github.com/user-attachments/assets/c536cc40-313a-466b-b01b-f114fd9d011b" />  
En mettant l'IP privé dans la barre de recherche on a le résultat demandé  
<img width="1819" height="924" alt="image" src="https://github.com/user-attachments/assets/cac50696-a73e-466e-a51a-a7e135c4e542" />  
```
sudo rm /var/www/html/index.html
sudo cp index.php /var/www/html/
```  
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
```  
On génère une clé SSH qu'on ajoute à Azure DevOps  
<img width="571" height="871" alt="image" src="https://github.com/user-attachments/assets/1d43088a-ff1d-4f87-b6b9-b83cd726ad18" />  
On upload tout sur Azure  
<img width="1841" height="848" alt="image" src="https://github.com/user-attachments/assets/4d23cb43-7d9c-4876-b26c-7bedc32590ef" />  
