- Container is like a lightweight, standalone executable package that includes everything needed to run a piece of software, including the code, runtime, libraries, and 
  system tools. 
- containers provide consistency across different environments and make it easy to deploy and run applications.
- Orchestration - managing and coordinating multiple containers to work together seamlessly. Kubernetes helps automate tasks like deploying, scaling, and managing 
  containerized applications.
- Node is an individual machine (physical or virtual) that is part of a cluster. Nodes are responsible for running containers and executing tasks assigned by the control 
  plane, making them the worker machines in the Kubernetes system.
- Cluster is a set of nodes (machines) that work together to run containerized applications. It includes a control plane for managing the cluster and nodes that execute 
  tasks. Clusters provide a unified environment for deploying and managing applications at scale.
- Pod is the smallest deployable unit in Kubernetes, representing a single instance of a running process. Pods can contain one or more containers that share resources and a 
  network namespace. They are the basic building blocks of applications in Kubernetes.

group of pods --> Replica set
cluster - set of nodes grouped together

Node - physical/ virtual machine [master node and worker node]
Worker Node - where the containers are hosted
Master Node Responsilities:-
  - Managing the worker nodes
  - Storing the information about the members of the clusters
  - Managing the clusters
  - Moving the workload of the failed node to another node
Note: master watches over the nodes in the cluster and is responsible for the actual orchestration of the containers on the worker nodes.
-------------------------            ---------------------------
|      Master Node      |            |     Worker Node         |
| </> kube-api server   |            | </>  Kubectl            |
|     etcd              |            |      container runtime  |
|     controllers       |            |                         |
|     shedulers         |            ----------------------------
-------------------------

container runtime - to run docker container on a system we need a container runtime installed
                    Ex:- Docker, CRIO, Rocket

Kubectl agent - responsible for interacting with master to provide health information of the worker node and carry out actions 
requested by the master on the worker node.

Key value store - all the information gathered from are stored in a key-value store in the master node.
key value stored is based on the popular etcd framework

command line utilities known as the kube command line tool or kubectl or kube control and also called as kube control tool.
is used to deploy and manage applications on a kubernetes cluster, to get cluster information, get status of the nodes 

we can set up kubernetes on local by using solutions like
      - MiniKube
      - KubeAdmin
Minikube  - used to setup a single instance of kubernetes in all-in-one set up
KubeAdmin - used to configure multi-node set up

Minikube provides an executable command line utility that will automatically download the ISO and deploy it on a virtualized platform
such as oracle virtual box or vmware fusion { we must have hypervisor installed on our system}
ISO - minikube bundles all of the different components

finally to interact with the kubernetes cluster we must ned kubectl or command line tool in our system
3 things to get this working
    - You must have virtualization driver installed on your system ( Ex: kvm2, docker, virtual box, podsman etc)
    - Kubectl installed
    - Minikube executable installed 
Installing kubectl before installation of minikube, will allow minikube to configure the kubectl utility to work with cluster when it provisons it

drivers used to setup the underlying virtualization environment for runningg kubernetes clusters on your local machine
    Ex: docker(container based), KVM2 ( VM based), Virtual box ( VM), podman ( container), SSH ( remote ssh), none (bare metal)