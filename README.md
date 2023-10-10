# Kubernetes Demo
---

*This shows a simple kubernetes deployment on a local PC using minikube. A simple webapp and another express app are deployed.*

**Step 1 - Install Minikube on PC**
---

- If chocolatey is installed on your PC, run `choco install minikube`. Ensure Docker is installed on your device as minikube needs it to run.

- After minikube is installed, run `minikube start --driver docker`. It'll download some dependencies in the background.

*You may see a minikube warning message about it not being able to locate the docker endpoint. Run `docker context ls` to see the available endpoints, then change to the one with Docker Desktop in the description by running `docker context use xxx`*

- Run `minikube status` to see if minikube is properly installed.

![Minikube Status](images/minikube-status.png)

**Step 2 - Set Up Kubernetes Config File**
---

*Templates on creating K8s config files can be found in the official kubernetes documentation*

- Create config map file for K8s called `mongo-config`.

```
apiVersion: v1
kind: ConfigMap
metadata:
  name: mongo-config
data:
  mongo-url: mongo-service
```

- Create another file called `mongo-secret`, which will hold the username and password for mongodb.

```
apiVersion: v1
kind: Secret
metadata:
  name: mongo-secret
type: Opaque
data:
  mongo-user: bW9uZ291c2Vy
  mongo-password: bW9uZ29wYXNzd29yZA==
```

*Since the values of mongo secret are base64 encoded, you can't use plain text. Run `echo -n mongouser | base64` to convert the username to base64.*

-