# DevOps Capstone Project

![Build Status](https://github.com/markotrnavac/devops-capstone-project/actions/workflows/ci-build.yaml/badge.svg)

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Python 3.9](https://img.shields.io/badge/Python-3.9-green.svg)](https://shields.io/)

This repository contains the code for the project [**DevOps Capstone Project**], which was developed as part of the [**IBM DevOps and Software Engineering Professional Certificate**](https://www.coursera.org/professional-certificates/devops-and-software-engineering)

The project purpose is to develop a web app (i.e. accounting service application), which uses REST interface to interact with accounting database. 

## Development Environment

Python code is developed in Python 3.9 venv using TDD and BDD development processes. It is built as a docker container afterwards after performing CI tasks - linting, unit tests and security checks using snyk. 
Database used within the environment is Postgres database deployed in a separate container. Both containers could be deployed as a microservice while there is also some code that could be used for automatic 
deployment in kubernetes cluster, while performing all CD pipeline tasks.

## Project layout

The code for the microservice is contained in the `service` package. All of the test are in the `tests` folder. The code follows the **Model-View-Controller** pattern with all of the database code and business logic in the model (`models.py`), and all of the RESTful routing on the controller (`routes.py`).

```text
├── service         <- microservice package
│   ├── common/     <- common log and error handlers
│   ├── config.py   <- Flask configuration object
│   ├── models.py   <- code for the persistent model
│   └── routes.py   <- code for the REST API routes
├── setup.cfg       <- tools setup config
└── tests                       <- folder for all of the tests
    ├── factories.py            <- test factories
    ├── test_cli_commands.py    <- CLI tests
    ├── test_models.py          <- model unit tests
    └── test_routes.py          <- route unit tests
```

## Data Model

The Account model contains the following fields:

| Name | Type | Optional |
|------|------|----------|
| id | Integer| False |
| name | String(64) | False |
| email | String(64) | False |
| address | String(256) | False |
| phone_number | String(32) | True |
| date_joined | Date | False |

## License

Licensed under the Apache License. See [LICENSE](LICENSE)
