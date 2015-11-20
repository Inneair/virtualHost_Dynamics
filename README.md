# VirtualHosts dynamiques

## 1. Objectifs

Le but de ce repository est de configurer des virtuals hosts dynamiquement. C'est à dire ne plus retourner dans vos 
configurations apache et seulement rajouter une ligne dans un fichier texte.

## 2. Contexte

Pour réaliser cette configuration vous devez avoir créé une machine virtuel
(avec [puphpet](https://puphpet.com/ "lien puphpet")) avec comme configuration minimale :

- php
- apache2

## 3 Installation

### 3.1 Fichier vhost.map

Créer un fichier vide `vhost.map` dans le dossier de partage de l'hôte (par exemple `/Users/<username>/Sites`).

### 3.2 VirtualHost par défaut

- Ajouter le fichier `000-default.conf` (fourni dans cet entrepôt) dans `/etc/apache2/site-availables`.
- Configurer le chemin du `vhost.map` dans le fichier `000-default.conf` (par exemple `/var/www/vhost.map`).
- Executer la commande `a2ensite 000-default.conf`.
- Redémarrer le serveur apache `service apache2 restart`
  
## 4. Mise en application

Vous avez un nouveau projet contenant l'arborescence suivante : 
```
exemple/www/index.html
```
Ce projet doit se trouver dans votre dossier de partage. Le répertoire `www` correspond au dossier public de
l'application.

- Déclarer le nom de domaine dans le fichier `/etc/hosts` de l'hôte. Adapter l'IP en fonction de celle de la machine
virtuelle :
```
192.168.58.101  exemple.dev
```  
- Déclarer la correspondance entre le nom de domaine et le dossier public dans votre fichier `vhost.map` :
```
exemple.dev       /exemple/www
```

Votre virtual host est près, vous pouvez commencez à travailler.

:warning: Si dans votre projet vous avez une redirection de votre URL avec un ajout de `www.` vous devez doublez la
déclaration de de ce vhost dans votre vhost.map  
```
exemple.dev       /exemple/www  
www.exemple.dev   /exemple/www
```  
:warning: Si vous avez un projet de type symfony avec non pas un index.php ou index.html n'oubliez pas de rajouter dans
le .htaccess dossier web  
```
DirectoryIndex app.php
```
