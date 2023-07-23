# Demo: Sending Logs from Minikube to Fluentd
### Steps
#### 1. Setting up a Minikube cluster
```%sh
# creating a new minikube cluster
$ minikube start -p fluentd --vm-driver docker

# setting  the minikube profile to our new fluentd cluster
$ minikube profile fluentd

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

Now, let's verify that the logs are being generated:
```%sh
$ kubectl get pods -n log-generator

NAME                             READY   STATUS    RESTARTS      AGE
log-simulator-66f7f979b4-ggvxg   1/1     Running   4 (87s ago)   2m
```

You can now watch the logs in real-time as they are generated:
```%sh
$ kubectl logs -f  log-simulator-66f7f979b4-ggvxg -n log-generator

{"source":"basicFile", "event":"The first computer dates back to Adam and Eve. It was an Apple with limited memory, just one byte. And then everything crashed.", "cycle":50}
{"source":"basicFile", "event":"I changed my password to incorrect. So whenever I forget what it is the computer will say Your password is incorrect", "cycle":50}
{"source":"basicFile", "event":"Question What do you call the security people outside of a Samsung Store? Answer Guardians of the Galaxy", "cycle":50}
{"source":"basicFile", "event":"Entered what I ate today into my new fitness app and it just sent an ambulance to my house", "cycle":50}
{"source":"basicFile", "event":"The first time I got a universal remote control, I thought to myself This changes everything", "cycle":50}
{"source":"basicFile", "event":"Is your name Wi-Fi? Because Im feeling a connection", "cycle":50}
{"source":"basicFile", "event":"Failure is not an option - it comes bundled with the software.", "cycle":50}
{"source":"basicFile", "event":"Yesterday I decided to change my WiFi name to Hack me if you can and when I woke up this morning I saw the name changed to Challenge accepted somebody help.", "cycle":50}
{"source":"basicFile", "event":"Four fonts walk into a bar. The barman says: Oi - get out. We dont want your type in here", "cycle":50}
{"source":"basicFile", "event":"I went to buy camouflage trousers but I couldnt find any", "cycle":50}
{"source":"basicFile", "event":"Im a big fan of whiteboards. I find them quite re-markable.", "cycle":50}
{"source":"basicFile", "event":"The problem with kleptomaniacs is that they always take things literally", "cycle":50}
{"source":"basicFile", "event":"UNIX is basically a simple operating system, but you have to be a genius to understand the simplicity", "cycle":50}
{"source":"basicFile", "event":"Unix is user friendly. Its just selective about who its friends are", "cycle":50}
```

The log generator pod will be running for a few minutes before it stops by itself.


