# VirtualHosts dinamyques

## 1. Objectifs

Le but de ce repository est de configurer des virtuals hosts dynamiquement. C'est à dire ne plus retourner dans vos 
configurations apache et seulement rajouter une ligne dans un fichier texte.

## 2. Le fichier vhost.map

Creer ce fichier a la base de vos projet. Pour un exemple de ce fichier référer vous à celui present dans ce repo.

:warning: Si dans votre projet vous avez une redirection de votre URL avec un ajout de "www." vous devez doublez la
déclaration de de ce vhost dans votre vhost.map  
Pour plus de détail je vous renvoie au fichier d'exemple de ce repo.

## 3. La configuration du host par default

Pour cela : 

 - Creer dans /etc/apache2/site-availables : le fichier 000-default.conf (le fichier est disponible sur le repo). 
 - Executer la commande :  
 ```
 a2ensite 000-default.conf
 ```
 - Redémarrer le serveur apache :  
  ```
  service apache2 restart
  ```
  
## 4. Rappels

Ne pas oublier de déclarer les hosts dans le fichier /etc/hosts de votre machine, exemple :   
```
 127.0.0.1  test.dev
 ```