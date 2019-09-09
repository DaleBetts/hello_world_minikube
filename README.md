# Hello World - An Example Application for Kubernetes

This is an example application written in Python, using the Flask framework and deployed for Kubernetes. This is a basic web application which will output "hello world" on a webpage, fronted by a load balancer resource type in Kubernetes.

## Requirements

* minikube - For installation, see: https://minikube.sigs.k8s.io/docs/start/
* docker - Only if you're further developing this app. See "Making changes to the application" below.

## How to Run the Application

Ensure minikube is running:

```
minikube start
kubectl cluster-info
```

Create the Kubernetes resources:

`kubectl apply -f hello-world.yaml`

Confirm resources are running:

```
kubectl get deployment helloworld
kubectl get svc helloworld
```

Start the load balancer simulation:

`minikube tunnel`

Access the application by entering the output of the following command in a browser:

`minikube service helloworld --url`


## Making changes to the application

Check out the repo, make changes to the code as appropriate, then to rebuild the docker image:

```
docker build -t dalebe/flask-hello-world:latest .
docker push dalebe/flask-hello-world:latest
```

