# Kubernetes Demo
---

*This shows a simple kubernetes deployment on a local PC using minikube. A simple webapp and another express app are deployed.*

**Step 1 - Install Minikube on PC**
---

- If chocolatey is installed on your PC, run `choco install minikube`. Ensure Docker is installed on your device as minikube needs it to run.

- After minikube is installed, run `minikube start --driver docker`. It'll download some dependencies in the background.

*You may see a minikube warning message about it not being able to locate the docker endpoint. Run `docker context ls` to see the available endpoints, then change to the one with Docker Desktop in the description by running `docker context use xxx`*

