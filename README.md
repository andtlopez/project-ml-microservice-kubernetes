[![<ORG_NAME>](https://circleci.com/gh/andtlopez/project-ml-microservice-kubernetes.svg?style=svg)](https://circleci.com/gh/andtlopez/project-ml-microservice-kubernetes)

## Project Overview

In this project, you will apply the skills you have acquired in this course to operationalize a Machine Learning Microservice API. 

You are given a pre-trained, `sklearn` model that has been trained to predict housing prices in Boston according to several features, such as average rooms in a home and data about highway access, teacher-to-pupil ratios, and so on. You can read more about the data, which was initially taken from Kaggle, on [the data source site](https://www.kaggle.com/c/boston-housing). This project tests your ability to operationalize a Python flask app—in a provided file, `app.py`—that serves out predictions (inference) about housing prices through API calls. This project could be extended to any pre-trained machine learning model, such as those for image recognition and data labeling.

### Project Tasks

Your project goal is to operationalize this working, machine learning microservice using [kubernetes](https://kubernetes.io/), which is an open-source system for automating the management of containerized applications. In this project you will:
* Test your project code using linting
* Complete a Dockerfile to containerize this application
* Deploy your containerized application using Docker and make a prediction
* Improve the log statements in the source code for this application
* Configure Kubernetes and create a Kubernetes cluster
* Deploy a container using Kubernetes and make a prediction
* Upload a complete Github repo with CircleCI to indicate that your code has been tested

You can find a detailed [project rubric, here](https://review.udacity.com/#!/rubrics/2576/view).

**The final implementation of the project will showcase your abilities to operationalize production microservices.**

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

