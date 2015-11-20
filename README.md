# VirtualHosts dinamyques

## 1. Objectifs

Le but de ce repository est de configurer des virtuals hosts dynamiquement. C'est à dire ne plus retourner dans vos 
configurations apache et seulement rajouter une ligne dans un fichier texte.

## 2. Contexte

Pour réaliser cette configuration vous devez avoir créé une machine virtuel
(avec [puphpet] (https://puphpet.com/ "lien puphpet")) avec comme configuration minimale :  
 - php
 - apache2

## 3 Installation

### 3.1 Le fichier vhost.map

Créer ce fichier (vide pour le moment) à la base de vos projet. Si vous avez déclarer a votre vm un lien entre /var/www 
et utilisateur/Site alors placer le fichier dans ce dossier.

### 3.2 La configuration du host par default

Pour cela : 

 - Créer dans /etc/apache2/site-availables : le fichier 000-default.conf (le fichier est disponible sur le repo). 
 - Executer la commande :  
 ```
 a2ensite 000-default.conf
 ```
 - Redémarrer le serveur apache :  
  ```
  service apache2 restart
  ```
  
## 4. Exemple

### 4.1 mise en application

Vous avez un nouveau projet contenant l'arborescence suivante : 
```
 exemple/public/index.html
 ```

Pour tout nouveau projet vous devrez effectuer les deux taches suivantes.

 - Déclarer l'hosts dans le fichier /etc/hosts de votre machine :   
```
 127.0.0.1  exemple.dev
 ```
 - Le déclarer dans votre fichier vhost.map votre host avec le chemin vers l'index.
 ```
  exemple.dev       /exemple/public
  ```
  
Et voila votre virtual host est près et vous pouvez commencez a travailler.

### 4.2 Cas particulier


 :warning: Si dans votre projet vous avez une redirection de votre URL avec un ajout de "www." vous devez doublez la
 déclaration de de ce vhost dans votre vhost.map  
 ```
 exemple.dev       /exemple/public  
 www.exemple.dev   /exemple/public
 ```  
 :warning: Si vous avez un projet de type symfony avec non pas un index.php ou index.html n'oubliez pas de rajouter dans
 le .htaccess dossier web  
 ```
 DirectoryIndex app.php
 ```
