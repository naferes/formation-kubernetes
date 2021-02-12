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

$ cd your_repertoire/kubernetes/first_app/docker
$ cat Dockerfile
$ cat index.js 
$ cat package.json

#### build image ###
$ docker build .
$ docker run -p 3000:3000 -it "id_image"
#### test hello world with nodejs ###
curl localhost:3000

### to make image available to kubernetes, you need to push the image to docker registry, like Docker hub, ACR, ECR, etc ###

## connect with docker registry ###
$ docker login

### tag image ###
$ docker ps #show container id# 
$ docker tag "container_id" my_user/k8s-demo-nodejs
$ docker push my_user/k8s-demo-nodejs
##### first pod ###
##### create helloworld.yml ####"
$ cd ../k8s
$ cat helloworld.yml
$ kubectl create -f hellowrld.yml
$ kubectl get pod
$ kubectl describe pod nodehelloworld.example.com
### use port forward ##
$ kubectl port-forward nodehelloworld.example.com 8081:3000
$ curl localhost:8081
#### expose pod ####
$ kuebctl expose pod nodehelloworld.example.com --type=NodePort --name nodehelloworld-service
#### url & ip to connecte ##
$ minikube service nodehelloworld-service --url
## get service ##
$ kubectl get service
### execute some cmd with kubectl ###
$ kubectl get sevice
### kubectl attach to see process ###
$ kubectl attach nodehelloworld.example.com 
### execute cmd in container ###
$ kubectl exec nodehelloworld.example.com -- ls /app
##### create replication controller ###
$ cat helloworld-repl-controller.yml
$ kubectl create -f helloworld-repl-controller.yml
$ kubectl get pods
$ kubectl get rc
$ kuebctl describe pod "nom_pod"
$ kubectl describe rc helloworld-controller
##### scale replication ######
$ kubectl scale --replicas=4 -f helloworld-repl-controller.yml
$ kubectl get rc
$ kubectl get pods
##### delete replication ####
$ kubectl delete rc/helloworld-controller
##### deployment #####
$ cd ../deployment
$ cat helloworld.yml
$ kubectl create -f helloworld.yml 
$ kubectl get deployments
#### show replicas set ###
$ kubectl get rs
$ kubectl get pods
#### show labels #####
$ kubectl get pods --show-labels
#### 



