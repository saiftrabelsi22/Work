# Démarrer un projet Django

## Etape n°1 : Création du projet et de l'environement virtuel

* Créer un dossier sur le burreau : Nom_du_projet
* Ouvrir le CMD

Aller dans le dossier
	
	cd C:\Users\Ykhil\Desktop\Nom_du_projet

Créer un environement virtuel :

	virtualenv Nom_du_projet_env

Activer l'environement virtuel

	C:\Users\Ykhil\Desktop\Nom_du_projet\Nom_du_projet_env\Scripts\activate.bat

Installer django sur l'environement virtuel :

	pip install Django==1.11.4

Créer un projet django :

	django-admin startproject ebrain

Aller dans le dossier du projet :

	cd Nom_du_projet

Lancer le serveur web local :

	python manage.py runserver

