[![CircleCI](https://dl.circleci.com/status-badge/img/gh/zeemah/udacity-proj4-operationalize-ml-microservice/tree/main.svg?style=svg)](https://dl.circleci.com/status-badge/redirect/gh/zeemah/udacity-proj4-operationalize-ml-microservice/tree/main)

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

* Create a virtualenv with Python 3.7 and activate it. Refer to this link for help on specifying the Python version in the virtualenv. 
```bash
python3 -m pip install --user virtualenv
# You should have Python 3.7 available in your host. 
# Check the Python path using `which python3`
# Use a command similar to this one:
python3 -m venv ~/.devops
#source .devops/bin/activate
source ~/.devops/bin/activate
```
* Run `make install` to install the necessary dependencies
make install
### Running `app.py`

1. Standalone:  `python app.py`

2. Run in Docker:  `./run_docker.sh`
chmod +x run_docker.sh
./run_docker.sh

3. Run in Kubernetes:  `./run_kubernetes.sh`
chmod +x run_kubernetes.sh
./run_kubernetes.sh

### Kubernetes Steps

* Setup and Configure Docker locally
Build docker locally using: docker build -t my-docker-repo/app-name:tag .

docker build -t halimausman/flaskapp:1 .

* Setup and Configure Kubernetes locally
1. use eksctl to create k8s cluster
eksctl create cluster --region=us-east-1 --name=cluster-name

* Create Flask app in Container
* Run via kubectl
kubectl create deploy NAME_OF_DEPLOYMENT --image=DockerHubImage 
kubectl create deploy flaskapp --image=halimausman/flaskapp:1

To get deployed nodes use:
kubectl get nodes

To get more info about the pod use:
kubectl get deploy,rs,scv,pods  

Expose the app to Port thus Port forwarding, use:
kubectl port-forward pod/NAME --address 0.0.0.0 PORT:PORT

