# Galv
> A metadata secretary for battery science

[![Validate specification](https://github.com/Battery-Intelligence-Lab/galv-spec/actions/workflows/validate.yml/badge.svg)](https://github.com/marketplace/actions/super-linter)
[![Create API clients](https://github.com/Battery-Intelligence-Lab/galv-spec/actions/workflows/clients.yml/badge.svg)](https://github.com/Battery-Intelligence-Lab/galv-spec/actions/workflows/clients.yml)
[![Create release](https://github.com/Battery-Intelligence-Lab/galv-spec/actions/workflows/create-release.yml/badge.svg)](https://github.com/Battery-Intelligence-Lab/galv-spec/actions/workflows/create-release.yml)
[![Docs website](https://github.com/Battery-Intelligence-Lab/galv-spec/actions/workflows/docs.yml/badge.svg)](https://Battery-Intelligence-Lab.github.io/galv-spec/)

## Galv Project
- [**Specification**](/Battery-Intelligence-Lab/galv-spec)
- [Backend](/Battery-Intelligence-Lab/galv-backend)
- [Frontend](/Battery-Intelligence-Lab/galv-frontend)
- [Harvester](/Battery-Intelligence-Lab/galv-harvester)

## Overview

Galv is a metadata secretary for battery science. 
This specification defines the Galv REST API that is used to store and retrieve battery data and metadata.
Code for the Galv REST API is available in the [galv-backend](/Battery-Intelligence-Lab/galv-backend) repository.

Although the specification is generated from the backend code, it does not become the 'source of truth' for the API
until it is released in this repository. 
This approach enables us to develop the backend and frontend in parallel,
while ensuring that the frontend is always compatible with the backend.

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

## GitHub Actions

This repository uses a GitHub action queue to issue new releases from updates to the specification.
These actions occur when changes are made to the `galv-spec.json` file.

The actions are:
1. Validate the specification
2. Generate clients in Python and Typescript (axios)
3. Create a release branch tagged with the version number
4. Issue the release on GitHub

The latest release is always available at https://github.com/Battery-Intelligence-Lab/galv-spec/releases/latest.

## Galv architecture

The below diagram presents an overview of Galv's architecture. 
The arrows indicate the direction of data flow.

<p align="center">
    <img src="img/GalvStructure.PNG" alt="Data flows from battery cycling machines to Galv Harvesters, then to the     Galv server and REST API. Metadata can be updated and data read using the web client, and data can be downloaded by the Python client." width="600" />
</p>

If you run your own instance of Galv, it will make its own schema available at `/schema/`,
and provide Swagger-UI and ReDoc documentation at `/schema/swagger-ui/` and `/schema/redoc/` respectively.

## Galv project features
- REST API for easy data storage and retrieval
- A Python, Julia, and MATLAB client for the REST API
- Metadata support using ontology definitions from BattINFO/EMMO
- A distributed platform with local data harvesters
- Docker based deployment
