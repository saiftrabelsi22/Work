# Déploiement Django sur Ngrok

## Information

Ngrok permet de créer un tunel provisoir entre ton site en local de ton pc et internet.


## La mise en ligne

#### 1. Commençon par télécharger [Ngrok](https://ngrok.com/download)

#### 2. ouvrir ngrok.exe, un cmd va normalement s'ouvrir.

#### 3. Lancer son site en local sur son pc

* Aller dans un nouveau cmd

Aller dans le dossier
	
	cd C:\Users\Ykhil\Desktop\Nom_du_projet\Nom_du_projet

Activer l'environement virtuel

	C:\Users\Ykhil\Desktop\Nom_du_projet\Nom_du_projet_env\Scripts\activate.bat

Lancer le serveur web local :

	python manage.py runserver


#### 4. Retourner à l'invité de comande de Ngrok.exe et lancer le serveur !

Pour lancer le tunel local on utilise la comande suivante :

	ngrok http 8000

Vous devrer optenir les deux cmd suivant :

![Les cmd](https://raw.githubusercontent.com/YannickHillion/Work/master/D%C3%A9ploiement%20Django%20sur%20Ngrok/ART/les%20cmd.PNG)

#### 5. Modifier les settings.ALLOWED_HOSTS et ajouter l'url qui nous est donnée par ngrok, dans mon exemple l'url est  `bf7e9d63.ngrok.io`


Maintenant aller verifier a l'url donnée par ngrok si votre application est bien en ligne !
!!! Attention, l'aplication n'est en ligne que temporerement !