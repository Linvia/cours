# Symfony installer

Cet outil permet d'installer Symfony.

Attention : il existe deux versions de cet outil :

- la version `4.x` permet d'installer les versions de Symfony `3.x` et Symfony `4.x`.
- la version `1.5.11` permet d'installer les versions de Symfony `2.x` et Symfony `3.x`.

## Installation du nouvel outil (version `4.x`)

### Windows

Télécharger le programme d'installation depuis l'adresse suivante et le lancer : [https://get.symfony.com/cli/setup.exe](https://get.symfony.com/cli/setup.exe).

### MacOS et Linux

Ouvrir un terminal et taper les commandes suivante :

    curl -sS https://get.symfony.com/cli/installer | bash
    sudo mkdir -p /usr/local/bin
    sudo mv ~/.symfony/bin/symfony /usr/local/bin/symfony

### Commandes utiles

Tester l'installation :

    symfony -V

La commande précédente est censée afficher quelque chose qui ressemble à :

    Symfony CLI version 4.2.5 (Wed Jan 16 09:53:39 CET 2019)

Installer la version LTS de Symfony (actuellement la `3.4`) en mode web app :

    symfony new --full --version=3.4 my_project

Installer la version LTS de Symfony (actuellement la `3.4`) en mode minimal (microservice, cli ou API) :

    symfony new --version=3.4 my_project

Installer la dernière version stable de Symfony en mode web app :

    symfony new --full my_project

Installer la dernière version stable de Symfony en mode minimal (microservice, cli ou API) :

    symfony new my_project

## Installation de l'ancien outil (version `1.5.11`)

### Windows

Ouvrir un terminal et se déplacer dans sa home (`C:\Users\[user]`) :

    cd %HOMEPATH%

Attention : notez bien le dossier dans lequel vous vous toruvez, c'est votre home.
Dans les lignes qui suivent, je désigne le dossier de la home par `C:\Users\[user]`.
Mais vous devrez utiliser le vrai chemin de votre home.

Télécharger l'installeur :

    php -r "file_put_contents('symfony-1.5.11.phar', file_get_contents('https://symfony.com/installer'));"

Créer un dossier `bin` dans sa home :

    mkdir bin

Déplacer le binaire `symfony-1.5.11.phar` :

    move symfony-1.5.11.phar bin/

Créer le fichier `symfony-1.5.11.bat` dans le dossier `bin` :

    cd bin
    (echo @ECHO OFF & echo php "%~dp0symfony-1.5.11.phar" %*) > symfony-1.5.11.bat

Télécharger le fichier [cacert.pem](https://curl.haxx.se/ca/cacert.pem) puis le déplacer dans le dossier `bin`.

Trouver le fichier `php.ini` utilisé :

    php --ini

Ouvrir le fichier `php.ini` et modifier la ligne :

    ;curl.cainfo =

afin d'obtenir :

    curl.cainfo = "C:\Users\[user]\bin\cacert.pem"

Ajouter le dossier `C:\Users\[user]\bin` dans la variable d'environnement `PATH` du système.

Voir [variables-environnement.md](variables-environnement.md) pour plus d'infos.

Fermer le terminal. Ouvrir un nouveau terminal puis tester le binaire :

    symfony-1.5.11

### Macos et Linux

    sudo mkdir -p /usr/local/bin
    sudo curl -LsS https://symfony.com/installer -o /usr/local/bin/symfony-1.5.11
    sudo chmod a+x /usr/local/bin/symfony-1.5.11

### Commandes utiles

Tester l'installation :

    symfony-1.5.11 -v

Installer Symfony 2.8 :

    symfony-1.5.11 new my_project 2.8

Installer Symfony 3.4 :

    symfony-1.5.11 new my_project 3.4

## Doc

- [Download Symfony Framework and Components](https://symfony.com/download)
- [symfony/symfony-installer: The Symfony Installer](https://github.com/symfony/symfony-installer)
- [Installing & Setting up the Symfony Framework (Symfony 3.4 Docs)](http://symfony.com/doc/3.4/setup.html)
- [Installing & Setting up the Symfony Framework (Symfony 2.8 Docs)](https://symfony.com/doc/2.8/setup.html)
- [curl - Extract CA Certs from Mozilla](https://curl.haxx.se/docs/caextract.html)
