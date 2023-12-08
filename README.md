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

The role of the Galv specification is to define the REST API and the data model.

The specification is in OpenAPI 3.0 format and is located at [galv-spec.json](galv-spec.json).

### Uses of the specification

There are three main uses of the specification:
1. To describe the REST API
2. To generate clients for the REST API
3. To generate mock servers for testing

#### 1. REST API

The specification is used to describe the REST API.
When the Galv REST API is updated, the specification should be updated to reflect the changes.
Breaking changes should be avoided, but if they are necessary, the version number should be updated.
Non-breaking changes should be reflected in the minor version number.

The specification is also used to generate documentation for the REST API, 
and to verify responses produced during testing conform to the specification.

#### 2. Clients

This specification can be used to generate clients in different languages using the [OpenAPI Generator](https://openapi-generator.tech/).
Each release comes with clients for Python and Typescript (axios).
The Glav frontend React app uses the Typescript client.

#### 3. Mock servers

The specification can be used to generate mock servers for testing.
When testing and developing the Galv frontend, a mock server is used to simulate the Galv REST API.

## Galv architecture

The below diagram presents an overview of Galv's architecture. 
The arrows indicate the direction of data flow.

<p align="center">
    <img src="img/GalvStructure.PNG" alt="Data flows from battery cycling machines to Galv Harvesters, then to the     Galv server and REST API. Metadata can be updated and data read using the web client, and data can be downloaded by the Python client." width="600" />
</p>

If you run your own instance of Galv, it will make its own schema available at `/schema/`,
and provide Swagger-UI and ReDoc documentation at `/schema/swagger-ui/` and `/schema/redoc/` respectively.
