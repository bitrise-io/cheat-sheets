# Minikube

- `minikube start --vm-driver kvm2 --kubernetes-version v1.11.5` : Create minikube VM with kvm2 driver (linux) and kubernetes version specified.
- `eval $(minikube docker-env)` : Share local docker registry (with minikube), else it won’t be able to find the docker images that we build.
- `minikube delete` : Shut down & delete the minikube VM.
- `minikube dashboard` : Open the kubernetes dashboard in browser.
- `minikube ip` : Print the IP of the minikube VM.
