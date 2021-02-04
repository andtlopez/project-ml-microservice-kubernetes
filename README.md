[![<ORG_NAME>](https://circleci.com/gh/andtlopez/project-ml-microservice-kubernetes.svg?style=svg)](https://circleci.com/gh/andtlopez/project-ml-microservice-kubernetes)

## Project Overview

This project aims to operationalize a working, machine learning microservice using [kubernetes](https://kubernetes.io/), which is an open-source system for automating the management of containerized applications. In this project, the following steps are done:
* Test your project code using linting
* Complete a Dockerfile to containerize this application
* Deploy your containerized application using Docker and make a prediction
* Improve the log statements in the source code for this application
* Configure Kubernetes and create a Kubernetes cluster
* Deploy a container using Kubernetes and make a prediction
* Upload a complete Github repo with CircleCI to indicate that your code has been tested


---

## Setup the Environment

* Create a virtualenv and activate it
python3 -m venv ~/.devops
source ~/.devops/bin/activate

* Run `make install` to install the necessary dependencies

### Running `app.py`

1. Standalone:  `python app.py`
2. Run in Docker:  `./run_docker.sh`
3. Run in Kubernetes:  `./run_kubernetes.sh`
4. Run Make Predictions script: `./make_predictions.sh`

### Docker Steps
* Build Image: `docker build --tag=andtlopez/devops .`
* Run via docker: `docker run -p 8000:80 andtlopez/devops`
* Upload image: `./upload_docker.sh`

### Kubernetes Steps

* Setup and Configure Docker locally
* Setup and Configure Kubernetes locally
    1. Install minikube
    2. Run minikube: `minikube start`
* Create Flask app in Container
* Run via kubectl
    1. `kubectl run devops --image=andtlopez/devops --port=80 --labels app=devops`
    2. `kubectl port-forward devops 8000:80`

### List of Files
* app.py: Python web application
* modeldata/: Contains the data for the app
* Makefile: install, test, and lint
* requirements.txt: app dependencies
* Dockerfile: Docker config
* run_docker.sh: Script that builds Docker image
* make_prediction.sh: Script that sends data to the app
* output_txt_files/docker_out.txt: Output for Docker built app
* upload_docker.sh: Uploads image to Docker Hub
* run_kubernetes.sh: Script that builds a Kubernetes pod
* output_txt_files/kubernetes.out.txt: Output for Kubernetes pod app
* .circleci/config.yml: CircleCI config file

