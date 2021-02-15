# Minikube Setup
  - it works on Linux, Windows, and MacOS
  - You will need Container or virtual machine manager, such as: Docker, Hyperkit, Hyper-V, KVM, Parallels, Podman, VirtualBox, or VMWare
  - You can download minikube from https://minikube.sigs.k8s.io/docs/start/
  - To launch your cluster you just need to enter (in a shell / terminal / powershell) :
    `$ minikube start --driver=<Driver>t`

# Kubectl
  - You can download kubectl from https://kubernetes.io/fr/docs/tasks/tools/install-kubectl/ 

# Docker Hub
  - Create Docker Hub account : https://hub.docker.com/ 

# CMD
 Go to first_app/docker directory
```sh
$ cd your_repertoire/kubernetes/first_app/docker
$ cat Dockerfile
$ cat index.js 
$ cat package.json
```
# Build image 
```sh
$ docker build .
$ docker run -p 3000:3000 -it "id_image"
```
# Test hello world with nodejs
```sh
$ curl localhost:3000
```
# To make image available to kubernetes, you need to push the image to docker registry, like Docker hub, ACR, ECR, etc 

# Connect with docker registry 
```sh
$ docker login
```
# Tag image 
```sh
$ docker ps  
$ docker tag "container_id" my_user/k8s-demo-nodejs
$ docker push my_user/k8s-demo-nodejs
```
# First pod 
# Create helloworld.yml 
```sh
$ cd ../k8s
$ cat helloworld.yml
$ kubectl create -f hellowrld.yml
$ kubectl get pod
$ kubectl describe pod nodehelloworld.example.com
```
# Use port forward 
```sh
$ kubectl port-forward nodehelloworld.example.com 8081:3000
$ curl localhost:8081
```
# Expose pod 
```sh
$ kuebctl expose pod nodehelloworld.example.com --type=NodePort --name nodehelloworld-service
```
# Url & ip to connecte 
```sh
$ minikube service nodehelloworld-service --url
```
# Get service 
```sh
$ kubectl get service
```
# Execute some cmd with kubectl 
```sh
$ kubectl get sevice
```
# Kubectl attach to see process 
```sh
$ kubectl attach nodehelloworld.example.com 
```
# Execute cmd in container 
```sh
$ kubectl exec nodehelloworld.example.com -- ls /app
```
# Create replication controller 
```sh
$ cat helloworld-repl-controller.yml
$ kubectl create -f helloworld-repl-controller.yml
$ kubectl get pods
$ kubectl get rc
$ kuebctl describe pod "nom_pod"
$ kubectl describe rc helloworld-controller
```
# Scale replication 
```sh
$ kubectl scale --replicas=4 -f helloworld-repl-controller.yml
$ kubectl get rc
$ kubectl get pods
```
# Delete replication 
```sh
$ kubectl delete rc/helloworld-controller
```
# Deployment 
```sh
$ cd ../deployment
$ cat helloworld.yml
$ kubectl create -f helloworld.yml 
$ kubectl get deployments
```
# Show replicas set 
```sh
$ kubectl get rs
$ kubectl get pods
```
# Show labels 
```sh
$ kubectl get pods --show-labels
```
 



