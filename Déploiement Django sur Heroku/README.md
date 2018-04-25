# Déploiement Django sur heroku

## Instalation d'heroku

1. créer un compte sur [heroku](https://www.heroku.com/) 
2. installer [heroku cli](https://devcenter.heroku.com/articles/heroku-cli#download-and-install)  
* instaler heroku dans le disque local C.

3. Modifier les PATHs cmd de windose 10
* Aller dans le panneau de configuration
* Aller dans Système et sécurité
* Aller dans système
* Aller dans paramétres système avancés
* Aller dans Variables d'environement
* Dans varaible système cliquer sur : path
* Ajouter C:\Heroku\bin

4. Se conecter à notre compte heroku, Dans le cmd écrire :

écrire la comande suivante :

	heroku login

5. pour vérifier que tout fonction ecrire (on verra afficher : You have no apps.) :

écrire la comande suivante :

	heroku apps --all

## Préparation de la mise en production

1. Générer une SECRET_KEY

Ouvrire la console et taper les instruction suivante :

	python
	import random, string
	"".join([random.choice(string.printable) for _ in range(24)])

*appuyer sur Enter puis copier la nouvelle dans un fichier txt sur votre bureau

2. Modifier les settings
* modifier `DEBUG = True` par `DEBUG = False`
* Dans ALLOWED_HOSTS insérer le nom de domaine voullu : `'nomdedomaine.herokuapp.com'`

3. Instaler whitenoise 
* dans l'env : `pip install whitenoise`
* dans les Settings.MIDDLEWARE ajouter : `'whitenoise.middleware.WhiteNoiseMiddleware',`

Tout en bas des settings ajouter :

	if DEBUG == True:
   		STATICFILES_STORAGE = 'whitenoise.storage.CompresseManifestStaticFilesStorage'

4. Créer le Procfile qui dit lance gunicorn et lit le fichier wsgi :
* écrire : `web: gunicorn Nom_du_projet.wsgi`

5. Retour dans le cmd et l'env et écrire télécharger gunicorn : `pip install gunicorn`

6. créer le fichier requirements.txt dans dans le même dossier que manage.py

il sufit de taper la commande :

	pip freeze > requirements.txt

## Création d'un nouveau projet sur Heroku

Tout ce qui suit sera dans l'env et dans le projet
1. ecrire `git init` puis `git status`
* si cela fonctionne on devrais observer l'architercture qui contient le fichier manage.py

2. Ajouter au git les fichier du projet

écrire la comande suivante :

	git add Procfile Nom_du_projet manage.py requirements.txt Mes_apps

3. Lancer un commit

écrire la comande suivante :

	git commit -m "mise en production"

4. Créer une nouvelle application heroku

écrire la comande suivante :

	heroku create Nom_de_application (la meme que le nom de domaine des settings)

5. configurer la nouvelle sercret_kay

écrire la comande suivante :
	
	heroku config:set SECRET_KEY="Clé_du_fichier_txt"

6. verification du fonctionnement en tappant `heroku config` qui devrais renvoyer les variable modifier du serveur

7. Envoyer le projet sur les serveur d'heroku

écrire la comande suivante :

	git push heroku master


## Finir la mise en production

1. Lancer les migrations 

écrire la comande suivante :

	heroku run python manage.py migrate

2. Créer un superutilisateurs

écrire la comande suivante :

	heroku run python manage.py createsuperuser

-----------------------------