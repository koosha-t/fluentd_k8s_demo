# Collecting Argo Workflow Logs Using Fluentd
### What is Argo Workflow?
As described in [here][1], Argo Workflows is an open source container-native workflow engine for orchestrating parallel jobs on Kubernetes. Argo Workflows is implemented as a Kubernetes CRD (Custom Resource Definition).Here are what we can do using Argo:

* Define workflows where each step in the workflow is a container.
* Model multi-step workflows as a sequence of tasks or capture the dependencies between tasks using a directed acyclic graph (DAG).
* Easily run compute intensive jobs for machine learning or data processing in a fraction of the time using Argo Workflows on Kubernetes.
* Argo is a Cloud Native Computing Foundation (CNCF) graduated project.

### Installing Argo Workflows on Minikube
```%sh
# creating a new minikube cluster called argo
$ minikube start -p argo

# setting the default minikube profile to argo
$ minikube profile argo

# setting the kubetl context to our new minikube argo cluster
$kubectl config use-context argo

# creating a new namespace to host argo deployments and services
$kubectl create namespace argo

# installing argo workflows
$kubectl apply -n argo -f https://github.com/argoproj/argo-workflows/releases/download/v3.4.9/install.yaml


```


[1]: https://argoproj.github.io/argo-workflows/
