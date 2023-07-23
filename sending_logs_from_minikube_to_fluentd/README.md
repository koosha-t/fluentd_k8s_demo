# Demo: Sending Logs from Minikube to Fluentd
### Steps
#### 1. Setting up a Minikube cluster
```%sh
# creating a new minikube cluster
$ minikube start -p fluentd --vm-driver docker

# linking kubectl to our new fluentd minikube cluster
$ kubectl config use-context fluentd
```

#### 2. Deploying a Log Simulator agent in the kubernetes cluster
We're deploying a log generator agent (from [this repository](https://github.com/mp3monster/LogGenerator/tree/master)) to generate logs in our minikube k8s cluster for fluentd to pick up. It can be deployed using the ```log-simulator-deployment.yaml``` manifest file in this directory:
```%sh
# creating a new namespace for our log-generator application
$ kubectl create namespace log-generator

# deploying the log-generator agent
$ kubectl apply -f log-simulator-deployment.yaml --namespace log-generator
``` 

