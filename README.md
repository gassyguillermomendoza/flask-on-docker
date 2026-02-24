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
$ docker compose up
```

This will start the Flask application and PostgreSQL database.

### Production Environment

To start the production environment, run the following command:

```
$ docker compose -f docker-compose.prod.yml up
```

This will start the Flask application, PostgreSQL database, and Nginx server.


### Access and features

To access the application, make sure port forwarding is enabled in your server, and in a browser navigate to http://localhost:4239/. The following API endpoints are available:

* `/`: Returns a JSON response with a "hello" message from the 'static' folder.
* `/media/<filename>`: Serves a media file from the `media` folder.
* `/upload`: Uploads a file to the `media` folder.


### Example API usage

Get hello message
```
$ curl http://localhost:4239
```
Upload a file
```
$ curl -F "file=@example.png" http://localhost:4239/upload
```
To View uploaded media, navigate to: http://localhost:4239/media/example.png

## Web Demo
![Demo](demo.gif)
