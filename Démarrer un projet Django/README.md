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

* Ouvrir google à l'url du [serveur local 8000](localhost:8000) et vérifier que cela fonctionne
* Maintenant que cela fonctionne il faut retourner dans le cmd et faire un CTRL-C

Créer les requirements :

	cd ..
	pip freeze > requirements.txt


* Créer ensuite un fichier AUTHORS.txt dans le dossier Nom_du_projet et y mettre le nom des auteurs
* Créer aussi un fichier README.md dans le dossier Nom_du_projet qui sera specifique au project

On doit donc obtenir cette architecture :

![Architechture d'un projet django](https://raw.githubusercontent.com/YannickHillion/Work/master/D%C3%A9marrer%20un%20projet%20Django/ART/Architecture%20d'un%20projet%20django.PNG)

## Etape n°2 : Création d'un Application Django et configuration de django

### Création de l'application
commencont par retourner dans notre dossier django :

	cd Nom_du_projet

on craient notre application :

	python manage.py startapp Nom_de_application

### Configuration de django
Dans settings.INSTALLED_APPS il faut ajouter notre application :

	'Nom_de_application.apps.Nom_de_applicationConfig',

Dans settings.LANGUAGE_CODE il faut modifier par :

	'fr-fr'

Dans settings.TIME_ZONE il faut modifier par :

	'Europe/Paris'

dans settings En dessous de `STATIC_URL = '/static/'` il faut rajouter :

	STATIC_ROOT = os.path.join(BASE_DIR, 'static')

Dans Urls ecrire :

	from django.conf import settings
	from django.conf.urls import include, url
	from django.contrib import admin
	from django.conf.urls.static import static


	urlpatterns = [
	    url(r'^admin/', admin.site.urls),
	    url(r'^', include('Nom_de_application.urls')),
	]

	if settings.DEBUG:
	    urlpatterns += static(settings.STATIC_URL, document_root=settings.STATIC_ROOT)

### Configuration de l'app

Dans l'app
Créer un fichier urls.py contenant :
	
	from django.conf.urls import url
	from . import views

	urlpatterns = [
	    url(r'^$', views.index, name='index'),   
	]

Dans views.py écrire :

	from django.shortcuts import render
	from django.conf import settings
	from django.http import HttpResponseRedirect

	def index(request):
		context = locals()
		template = "index.html"

		return render(request,template,context)

Créer un dossier nomée : templates
* Dans le dossier templates créer un fichier index.html
* Dans le dossier templates créer un fichier base.html
* Dans le dossier templates créer un fichier 400.html
* Dans le dossier templates créer un fichier 404.html
* Dans le dossier templates créer un fichier 403.html
* Dans le dossier templates créer un fichier 500.html

Créer un dossier nomée : static
* Dans le dossier static créer un dossier Nom_de_application

Dans le Nom_de_application
* Créer un dossier img
* Créer un dossier js
* Créer un dossier css
* Créer un dossier mp4
* Créer un dossier fonts

Dans le fichier base.html ecrire :

	{% load staticfiles %}
	<!DOCTYPE html>
	<html>
	<head>
		<title></title>
		<link rel="icon" type="image/png" href="" />
	</head>
	<body>

	{% block content %}

	{% endblock %}

	</body>
	</html>

Dans les fichier 400 403 404 500 ecrire :

	{% extends 'base.html' %}
	{% load staticfiles %}

	{% block content %}

	<h1>
	Explications de l'erreur 400 ou 403 ou 404 ou 500.
	</h1>

	{% endblock %}

Dans le fichier index.html ecrire :

	{% extends 'base.html' %}
	{% load staticfiles %}

	{% block content %}
	<h1> Hello world </h1>
	{% endblock %}

### Les derniére comandes

dans le cmd il faut lancer les comandes suivantes :

	python manage.py collectstatic
	python manage.py makemigrations
	python manage.py migrate
	python manage.py runserver

Si tout marche bien rdv à l'url du [serveur local 8000](localhost:8000), cela devrais afficher Hello world ! 