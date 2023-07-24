# Kubernetes Log Unification, Routing, and Aggrevation Using Fluentd

__*Important Note*__: This tutorial is mainly extracted from the following book:
* [Logging in Action With Fluentd, Kubernetes and more](https://www.manning.com/books/logging-in-action?experiment=B)

### What is Fluentd?
The primary purpose of Fluentd and its sibling Fluent Bit is to capture log events from a diverse range of possible sources (infrastructure such as network switches, OS, custom applications, and prebuilt applications, including Platform as a Service and Software as a Service). It then gets those events to an appropriate tool where the log events can be processed to extract meaning and insight, and possibly trigger actions. Fluentd’s primary job is not to perform detailed log analytics itself, although it can derive meaning, and deeper analysis could be incorporated into its configuration if needed.

By unifying the log events from all the sources of logs impacting the operation of our solution, we have the opportunity to see the big picture.


### Main Objectives of Log Unification (section is in progress)
__Root cause analysis__: Sometimes we see a problem, but the cause isn’t apparent. Often this is because we are looking only at the logs from a small set of components. For example, an application based on its logs appears to slow down over time, but there is no evidence of a memory leak. Only when we bring logs together from all the sources can we identify a cause and separate other problems as side effects. For example, our application could be fine. Still, we use another service on the same server, which never releases CPU threads properly, resulting in the server slowly running out of resources to run all applications. But this can’t be seen until all the information is presented together.

### Demos
This repository will be containing several demos of fluentd usages in kubernetes. Each demo will be in its dedicated directory.

List of demos:
* [Sending k8s logs from minikube to fluentd](https://github.com/koosha-t/fluentd_k8s_demo/tree/main/sending_logs_from_minikube_to_fluentd)
* Collecting Argo Workflow Logs
* [more demos to be released soon]      

