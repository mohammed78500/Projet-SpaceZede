## Installation et configuration des serveurs
<p align="right"><a href="README.md">(Retourner au sommaire)</a></p>

**Description de l'étape :**  

**1 - Installation et configuration de l'ADDS avec role DNS et DHCP :**


**2 - Installation et configuration du serveur de fichiers :**

**3 - Installation et configuration du serveur de téléphonie :**

**4 - Installation et configuration du serveur de messagerie :**

**5 - Installation et configuration du serveur GLPI :**

**6 - Installation et configuration du serveur WEB :**

Procédure d'installation de GLPI 

1 – Mise à jour des paquets Debian

On commence par mettre à jour les paquets présents :

apt update & apt upgrade -y

2 – Installation, si nécessaire, du serveur LAMP (Linux Apache MariaDB PHP)
Remarque : cette étape n’est pas nécessaire si un serveur LAMP a déjà été installé.

a) Installation d’Apache :
apt install apache2

b) Installation PHP 8.2 (GLPI 10 nécessite une version PHP 8 au minimum) :

Pour installer PHP 8.2 en tant que module Apache, vous devez procéder ainsi (Debian 12 possède les paquets PHP 8.2 par défaut) :

apt install php libapache2-mod-php
sudo systemctl restart apache2

c) Installation de MariaDB :

apt install mariadb-server

Une fois l’installation de MariaDB effectuée, lancez l’utilitaire de configuration du mot de passe root en saisissant la commande
suivante :

mysql_secure_installation (suivez les étapes pour sécuriser MariaDB en définissant le mot de passe du root)

3 – Création de la base de données « GLPI »

Pour commencer nous allons nous connecter à MariaDB afin de créer une base de données :

mysql -u root -p
(saisir le mot de passe du root que vous avez défini lors de l’installation)

Ensuite nous allons créer une base de données nommée « glpi », créer un utilisateur « glpi », lui donner un mot de passe et lui
accorder tous les droits de lecture/écriture. Pour cela, nous saisissons les commandes :

create database glpi; (création de la base de données « glpi »)
create user 'glpi'@'localhost' identified by 'glpi'; (création de l’utilisateur avec son mot de passe qui sera « glpi »)
grant all privileges on glpi.* to 'glpi'@'localhost' with grant option; 
flush privileges; 
quit 

4 Téléchargement et décompression de l’archive « GLPI »

Pour installer GLPI, il est nécessaire de connaître le lien de téléchargement du logiciel. En parcourant le web, on trouve l’adresse
exacte de téléchargement de la dernière version stable (on évitera les versions beta et RC) :
https://github.com/glpi-project/glpi/releases/download/10.0.10/glpi-10.0.10.tgz

Sur la machine Debian, on peut créer un dossier « glpi » dans lequel on téléchargera l’archive, puis on lance le téléchargement de
l’archive GLPI depuis ce dossier.
Lien de téléchargement de la dernière version de GLPI (10.0.10 – Septembre 2023) :
wget https://github.com/glpi-project/glpi/releases/download/10.0.10/glpi-10.0.10.tgz

**5 - Installation et configuration du serveur WEB :**


<a href="README.md">(Retourner au sommaire)</a>
