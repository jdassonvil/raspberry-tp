# TP raspberry PI

## Préparation du poste de travail
### Windows
Pour réaliser ce projet vous avez besoin d'installer les logiciels suivants:

* [7zip](http://www.7-zip.de/)
* [Win 32 disk imager](http://sourceforge.net/projects/win32diskimager/)
* [Putty](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe)
* [Zenmap](http://sourceforge.net/projects/nmap.mirror/?source=typ_redirect)


### MacOS

## Configuration du Raspberry PI
### Formattage de la carte SD
Dans cette première étape nous allons formatter la carte SD depuis une image préconfigurée. Une image est comme une photographie du disque à un instant donnée. En utilisant une image allons nous éviter de nombreuses étapes d'installation et le raspberry PI sera tout de suite prêt à être utilisé.

#### Windows

1. Téléchargez l'image du disque depuis le site de Hypriott ([ici](http://blog.hypriot.com/downloads/))
1. A l'aide 7zip décompressez le fichier précédement téléchargé, vous devez obtenir un fichier avec une extension en `.img`
1. Inserez votre SD dans le lecteur de carte et notez la lettre sur laquelle elle est accessible (il doit être détecté et doit apparaitre dans le poste de travail)
1. Lancez en mode administrateur *Win 32 disk imager* (clique droit > Lancer en administrateur)
1. Cliquez sur le dossier bleu pour retrouver le fichier image précédement décompressé
1. A côté du dossier bleu, dans la rubrique *device*, choissisez la lettre qui correspond à la carte SD
1. Cliquez enfin sur **write**, l'écriture sur la carte débute
1. Lorsque le formattage est terminé, éjectez proprement la carte à l'aide de l'icone se trouvant en bas à droite de la barre de tache. Vous pouvez ensuite retirer la carte du lecteur.

#### MacOS
1. Téléchargez l'image du disque depuis le site de Hypriott ([ici](http://blog.hypriot.com/downloads/))

## Demarrage du raspberry PI
Il est à présent temps de mettre en route notre raspberry PI.

1. Insérez la carte micro SD dans le raspberry
1. Connectez le raspberry au réseau à l'aide
1. Branchez le raspberry, les LEDs doivent commencer à clignoter. Le premier démarrage prend entre une et trois minutes

## Test de bon fonctionnement
Votre raspberry a à présent bien démarré avec une image préconfiguré, il est temps de s'assurer que tout s'est bien passé.

Votre raspberry n'est actuellement connecté qu'au réseau, il n'a aucune interface avec le monde extérieur mise à part quelques LEDs. Alors comment s'en servir ?
Une solution pourrait être de brancher un écran sur le port HDMI, un clavier USB et nous pourrions l'utilisé comme un ordinateur "classique".
Cependant l'image que nous avons téléchargez est un image de type serveur et ne possède pas d'interface graphique. Nous allons nous connecter à distance depuis notre ordinateur

### Découverte de l'adresse IP
En connectant le raspberry au réseau celui-ci a automatiquement reçu une adresse IP, mais nous ne la conaissons pas encore !

#### Windows
1. Lancez cmdr et entrez `ipconfig`, notez votre adresse IP
1. Lancez Zenmap
1. Dans le champ commande saisissez la ligne suivante `nmap -sP <votre adresse IP>/24` avec votre propre adresse IP. L'ensemble de la plage IP de votre réseau est scanée, vous devez obtenir le résultat suivant.
![résultat nmap](./img/zenmap-scan-result.png")

1. Dans le champ *Host filter* en bas de la fenêtre, saisissez le mot **black** puis utilisez le bouton *filter host*, le résultat filtré est l'adresse IP de votre raspberry PI


#### MacOS

### Connexion au raspberry

#### Windows
1. Lancez putty
1. Dans le champ 'hostname' saisissez l'adresse IP de votre raspberry
1. Cliquez sur open en bas à gauche pour ouvrir une Connexion
1. Saisissez alors `pirate` comme nom d'utilisateur et `hypriot` comme mot de passe (les caractères ne s'affichent pas lorsque vous tapez le mot de passe, c'est normal)
1. Vous être à présent connecté !

#### MacOS

### Lancer un serveur de Test

Dans le terminal précédement ouvert, lancez cette commande `docker run -d -p 80:80 hypriot/rpi-busybox-httpd`. Ouvrez un navigateur web (chrome, firefox...) sur votre ordinateur et dans la barre d'adresse saisissez l'IP du raspberry. Si tout s'est bien passé la page suivante doit s'afficher.

![fin installation](./img/browser-pi-hypriot-logo")

Donc que c'est il passé ? A l'aide de docker nous avons lancé un serveur web qui écoute sur le port 80 (le port par défaut sur internet). Dans notre navigateur nous avons demandé à accéder à une page se trouvant à l'IP de notre raspberry et de manière implicite sur le port 80.

En savoir plus sur:
  * C'est quoi cette histoire de port ?
  * C'est quoi docker ?

## Déploiement d'une première application

## Premiers pas avec Ruby on rails

## Déploiement de redis

##
