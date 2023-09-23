[![CircleCI](https://dl.circleci.com/status-badge/img/gh/chuanhtoan/DevOps_Microservices/tree/master.svg?style=svg)](https://dl.circleci.com/status-badge/redirect/gh/chuanhtoan/DevOps_Microservices/tree/master)

## Project Overview

This project using sklearn model to predict housing prices in Boston according to several features, such as average rooms in a home and data about highway access. It's using CircleCI to deploy a Python flask app to prodives predictions through API calls.

### Project Tasks

Your project goal is to operationalize this working, machine learning microservice using [kubernetes](https://kubernetes.io/), which is an open-source system for automating the management of containerized applications. In this project you will:

- Test your project code using linting
- Complete a Dockerfile to containerize this application
- Deploy your containerized application using Docker and make a prediction
- Improve the log statements in the source code for this application
- Configure Kubernetes and create a Kubernetes cluster
- Deploy a container using Kubernetes and make a prediction
- Upload a complete Github repo with CircleCI to indicate that your code has been tested

You can find a detailed [project rubric, here](https://review.udacity.com/#!/rubrics/2576/view).

**The final implementation of the project will showcase your abilities to operationalize production microservices.**

---

## Setup the Environment

- Create a virtualenv with Python 3.7 and activate it. Refer to this link for help on specifying the Python version in the virtualenv.

```bash
python3 -m pip install --user virtualenv
# You should have Python 3.7 available in your host.
# Check the Python path using `which python3`
# Use a command similar to this one:
python3 -m virtualenv --python=<path-to-Python3.7> .devops
source .devops/bin/activate
```

- Run `make install` to install the necessary dependencies

### Running `app.py`

1. Standalone: `python app.py`
2. Run in Docker: `./run_docker.sh`
3. Run in Kubernetes: `./run_kubernetes.sh`

### Kubernetes Steps

You should be in your virtual machine first

1. Setup and Configure Docker locally

   - You should have wsl2 first:
     wsl --install
     wsl --update
     wsl --set-default-version 2

   - You can douwnload Docker Desktop for Windows here:
     https://docs.docker.com/desktop/install/windows-install/

2. Setup and Configure Minikube locally

   - Download and setup
     New-Item -Path 'c:\' -Name 'minikube' -ItemType Directory -Force
     Invoke-WebRequest -OutFile 'c:\minikube\minikube.exe' -Uri 'https://github.com/kubernetes/minikube/releases/latest/download/minikube-windows-amd64.exe' -UseBasicParsing

   - Add Minikube to PATH:
     $oldPath = [Environment]::GetEnvironmentVariable('Path', [EnvironmentVariableTarget]::Machine)
        if ($oldPath.Split(';') -inotcontains 'C:\minikube') {
     [Environment]::SetEnvironmentVariable('Path', $('{0};C:\minikube' -f $oldPath), [EnvironmentVariableTarget]::Machine)
     }

   - Minikube start

3. Install dependencies using make

   - npm install make -g
   - make all

4. Setup and Configure Kubernetes locally

   - You can download it using curl:
     curl.exe -LO "https://dl.k8s.io/release/v1.28.2/bin/windows/amd64/kubectl.exe"

5. Running script files

   - ./run_docker.sh
   - ./run_kubernetes.sh
   - ./upload_docker.sh
   - ./make_prediction.sh
