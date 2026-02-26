# Flask on Docker [![Build and Deploy](https://github.com/gassyguillermomendoza/flask-on-docker/actions/workflows/build.yml/badge.svg)](https://github.com/gassyguillermomendoza/flask-on-docker/actions/workflows/build.yml)

## Overview

This project demonstrates a production-ready Flask application deployed with Docker. 
The application exposes a small API that serves static files, allows users to upload media, 
and stores metadata in a PostgreSQL database. The system runs as a multi-container 
environment using Docker Compose with:

- Flask + Gunicorn application server
- PostgreSQL database
- Nginx reverse proxy for production

The repository includes both development and production configurations as well as a CI 
workflow that builds the project automatically.

## Build instructions

### Getting Started

To get started, clone the repository and navigate to the project directory.

### Development 

To start the development environment, run the following command:

```
$ docker compose up -d --build
```

This will start the Flask application and PostgreSQL database.

### Production Environment

To start the production environment, run the following command:

```
$ docker compose -f docker-compose.prod.yml up -d --build
```

This will start the Flask application, PostgreSQL database, and Nginx server.


### Access and features

To access the application in the production environment, first create a 'env.prod.db' file containing your credential as follows: 

```
$ cat > .env.prod.db << EOF
POSTGRES_USER=change_me 
POSTGRES_PASSWORD=change_this
POSTGRES_DB=change_me_too
EOF
```
Make sure port forwarding is enabled in your server, and run this line:

```
$ docker-compose -f docker-compose.prod.yml exec web python manage.py create_db
```
Then in a browser navigate to http://localhost:4239/ (or replace that number with whichever port you are forwarding to). 
>>Note: If you  want to initialize the development environment instead, replace `.prod` in the filename from the line above.  

The following API endpoints are available:
* `/`: Serves a JSON response with a fun greeting message from the 'static' folder.
* `/upload`: Allows the user to upload a file to the `media` folder.
* `/media/<filename>`: Serves a media file from the `media` folder.


## Web Demo
![Demo](demo.gif)
