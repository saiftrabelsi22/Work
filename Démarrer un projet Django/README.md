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

	django-admin startproject Nom_du_projet

Aller dans le dossier du projet :

	cd Nom_du_projet

Lancer le serveur web local :

	python manage.py runserver

* Ouvrir google à l'url du [serveur local 8000](http://www.siteduzero.com) et vérifier que cela fonctionne
* Maintenant que cela fonctionne il faut retourner dans le cmd et faire un CTRL-C

Créer les requirements :

	cd ..
	pip freeze > requirements.txt


* Créer ensuite un fichier AUTHORS.txt dans le dossier Nom_du_projet et y mettre le nom des auteurs
* Créer aussi un fichier README.md dans le dossier Nom_du_projet qui sera specifique au project

On doit donc obtenir cette architecture :

![Architechture d'un projet django](https://raw.githubusercontent.com/YannickHillion/Work/master/D%C3%A9marrer%20un%20projet%20Django/ART/Architecture%20d'un%20projet%20django.PNG)

