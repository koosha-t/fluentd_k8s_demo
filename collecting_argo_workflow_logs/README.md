# Collecting Argo Workflow Logs Using Fluentd
### What is Argo Workflow?
As described in [here][1], Argo Workflows is an open source container-native workflow engine for orchestrating parallel jobs on Kubernetes. Argo Workflows is implemented as a Kubernetes CRD (Custom Resource Definition).Here are what we can do using Argo:

* Define workflows where each step in the workflow is a container.
* Model multi-step workflows as a sequence of tasks or capture the dependencies between tasks using a directed acyclic graph (DAG).
* Easily run compute intensive jobs for machine learning or data processing in a fraction of the time using Argo Workflows on Kubernetes.
* Argo is a Cloud Native Computing Foundation (CNCF) graduated project.

[1]: https://argoproj.github.io/argo-workflows/
