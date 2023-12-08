# Galv

[![GitHub Super-Linter](https://github.com/Battery-Intelligence-Lab/galv-spec/actions/workflows/validate.yml/badge.svg)](https://github.com/marketplace/actions/super-linter)
[![Clients](https://github.com/Battery-Intelligence-Lab/galv-spec/actions/workflows/clients.yml/badge.svg)](https://github.com/Battery-Intelligence-Lab/galv-spec/actions/workflows/clients.yml)
[![Create Release](https://github.com/Battery-Intelligence-Lab/galv-spec/actions/workflows/create-release.yml/badge.svg)](https://github.com/Battery-Intelligence-Lab/galv-spec/actions/workflows/create-release.yml)

Galv is an open-source platform for automated storage of battery data with advanced metadata support for battery scientists. 
Galv is deployed with [Docker](https://docs.docker.com/) to support robust local and cloud instances. 
An example frontend view is displayed below. 

<p align="center">
<img src="img/galv_frontend_v1.png" width="900" />
</p>

## Features:
- REST API for easy data storage and retrieval
- A Python, Julia, and MATLAB client for the REST API
- Metadata support using ontology definitions from BattINFO/EMMO
- A distributed platform with local data harvesters
- Docker based deployment

## Specification

Galv is built on a REST API specification.

The schema can be downloaded from the [documentation page](https://Battery-Intelligence-Lab.github.io/galv-spec/UserGuide.html#api-spec). 
If you run your own instance of Galv, it will make its own schema available at `/schema/`, 
and provide Swagger-UI and ReDoc documentation at `/schema/swagger-ui/` and `/schema/redoc/` respectively.

The below diagram presents an overview of Galv's architecture. 
The arrows indicate the direction of data flow.

<p align="center">
    <img src="docs/source/img/GalvStructure.PNG" alt="Data flows from battery cycling machines to Galv Harvesters, then to the     Galv server and REST API. Metadata can be updated and data read using the web client, and data can be downloaded by the Python client." width="600" />
</p>
