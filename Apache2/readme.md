# Créer une serveur Apache fonctionnelle.

## Qu'est-ce que le serveur Apache
Apache est un serveur Web HTTP open source développé et maintenu par une communauté d’utilisateurs autour de l’ Apache Software Foundation. Il permet de répondre aux demandes de contenu provenant de clients Web (navigateurs).

# Pour toutes les configurations,il est exigé d'être en mode root:
            -Sur Debian: user@debian:~$ su
            -Sur Ubuntu: user@debian:~$ sudo su

# 1-Installer Apache2 sur un systeme basée sur linux(Debian/Ubuntu)
  Commande:
        -apt-get update
        -apt-get install Apache2
  ##Pour verifier:
        -apache2 -v

# 2-Configuration du serveur - Donner un nom du serveur
  Commande: <br>
            -root@debian:~# nano /etc/apache2/apache2.conf <br>
Ajouter un nom de seveur: <br>
.... <br>
#ServerRoot "/etc/apache2" <br>
ServerName www.test.fr
<br>
### 3-Configuration du serveur - etablir la configuration du sécurité et les bases

            -root@debian:~# vi conf-enabled/security.conf
            :set nu
Modifier l'initial par:
...
24 #ServerTOkens Minimal
25 ServerTokens prod
=>Enregistrer cette modification

            -root@debian:~# nano /etc/apache2/sites-available/000-default.conf
      Par défaut,la configuration est :

### 
      <VirtualHost *:80>
	ServerAdmin webmaster@localhost
	DocumentRoot /var/www/html
	ErrorLog ${APACHE_LOG_DIR}/error.log
	CustomLog ${APACHE_LOG_DIR}/access.log combined
### </VirtualHost>

ServerAdmin consiste à l'extension serveur.
/var/www/html est le repertoire du serveur.

## 4-Configuration du serveur - sites disponible et liens symboliques
            -root@debian:~# cd /var/www/html
            -root@debian:~# nano index.html <br>
<img src="image/apache-html.png" alt="">

#### Recupérer l'adresse IP
<img src="image/apache-IP.png">

## 5-Redémarrer le service Apache2

            -root@debian:~# /etc/init.d/apache2 restart
## 6-Récuperer l'adresse IP et le saisir sur un navigateur.
            -root@debian:~# ip addr
<img src="image/apache-test.png" alt="">

### Vous avez une serveur Apache fonctionnelle
<a href="https://github.com/Jonas4884/Reseau-et-systeme">Revenir au liste des serveurs</a>