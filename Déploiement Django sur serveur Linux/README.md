# Déploiement d'une application Django (serveur virtuel de A à Z en hébergement mutualisé)

Nous verrons en détail quels logiciels installer sur Ubuntu, comment configurer Nginx, Gunicorn et lancer des processus sous supervision.

## Memo linux 

## Configurez un espace serveur

### Création du serveur

1. Créer un compte sur [ovh](https://www.ovh.com/fr/)  

2. Acheter un Cloud vps ssd
* Virtual Private server SSD
* VPS 2016 SSD (1vCore/2GO/10GO) (3,99€ HT/mois)
* Quantité 1
* localisation en Europe ( de préference en france )
* Distribution Ubuntu
* Version Ubuntu 16.04 Server 64bits
* Language Français

3. Installer putty
* télécharger [putty](https://www.commentcamarche.net/download/telecharger-90-putty)

### Aciver le pare-feu (Firewall dans OVH) - [doc](https://docs.ovh.com/fr/dedicated/firewall-network/)

1. Créer un fireWall (retour dans ovh)
* aller dans la section IP dans la bare de gauche et selectioner l'ipv4 concerné
* cliquer sur les "..."" et cliquer sur créer un firewall 

2. maintenant il faut re cliquer sur les "..." et cliquer sur "activer le firewall"

3. maintenant il faut re cliquer sur les "..." et cliquer sur "Configurer le firewall"

4. suivre la configuration de l'image ci dessous pour autoriser les protocole http et https
![Firewall](https://raw.githubusercontent.com/YannickHillion/Work/master/D%C3%A9ploiement%20Django%20sur%20Ngrok/ART/les%20cmd.PNG)

### Connexion en SSH

1. Conexion en SSH grace a putty sur notre serveur
* prendre l’IPv4 ou le nom de la machine (dans le mail envoyer par ovh)
* prendre le mot de passe root de la machine (reçu par mail à l’installation).
* Ouvrir putty et entrer l'IPV4 de son serveur puis cliquer sur 'open'.
* puis se connecter avec le mot de passe et l'utilisateur root reçu par mail (si cela fonctionne on devrais voir un cmd pour ubuntu s'ouvrir)

2. Création d'un utilisateur avec des droit restrain à root

ecrire la comande dans le putty :

	adduser nouveau_nom_utilisateur

* entrer nos nouveu mot de passe et note full name, pour tout le reste faire juste 'enter'.

3. donner des droit plus important au nouveaux utilisateur

ecrire la comande dans le putty :

	gpasswd -a nouveau_nom_utilisateur sudo

4. Changer maintenant pour passer de root a votre nouvelle utilisateur.

ecrire la comande dans le putty :

 	su - nouveau_nom_utilisateur

5. tapez la commande `pwd` cela devrais afficher : /home/nouveau_nom_utilisateur

6. on peut maintenant quitter

ecrire la comande dans le putty :

	exit

---------------------------
	