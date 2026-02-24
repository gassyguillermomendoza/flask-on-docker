# Flask on Docker

## Overview
--------

This repository contains a Flask application running on Docker. It provides a simple API for serving static files and uploading media.

## Getting Started
---------------

To get started, clone the repository and navigate to the project directory.

## Development Environment
------------------------

To start the development environment, run the following command:

```
$ docker compose up
```

This will start the Flask application and PostgreSQL database.

## Production Environment
-----------------------

To start the production environment, run the following command:

```
$ docker compose -f docker-compose.prod.yml up
```

This will start the Flask application, PostgreSQL database, and Nginx server.

## API Endpoints
--------------

The following API endpoints are available:

* `/`: Returns a JSON response with a "hello" message.
* `/media/<filename>`: Serves a media file from the `MEDIA_FOLDER`.
* `/upload`: Uploads a file to the `MEDIA_FOLDER`.

