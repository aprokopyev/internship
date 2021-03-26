## Prerequsite

* Minikube v1.6.2 or greater with ingress plugin enabled

* Helm 3.2.3 or greater

## Questions

1. What is Kubernetes and what is it for?  
A:  
	Kubernetes (aka K8s) is an open-source container-orchestration system for automating computer application deployment, scaling, and management.
	It was originally designed by Google and is now maintained by the Cloud Native Computing Foundation. 
	It aims to provide a "platform for automating deployment, scaling, and operations of application containers across clusters of hosts".
	It works with a range of container tools and runs containers in a cluster, often with images built using Docker. 
	Kubernetes originally interfaced with the Docker runtime through a "Dockershim"; however, the shim has since been deprecated in favor of directly interfacing with containerd or another CRI-compliant runtime.  
	Above is an excerpt from: https://en.wikipedia.org/wiki/Kubernetes


2. What Kubernetes entities can you list and what is their purpose?  
A:  
	Configmap: can be anything as fine-grained as individual properties or coarse-grained information like entire configuration files or JSON / XML documents.  
	Daemonset: Normally, the locations where pods are run are determined by the algorithm implemented in the Kubernetes Scheduler. For some use cases, though, there could be a need to run a pod on every single node in the cluster. This is useful for use cases like log collection, ingress controllers, and storage services. The ability to do this kind of pod scheduling is implemented by the feature called DaemonSets.  
	Deployment: manages what happens to the ReplicaSet - whether an update has to be rolled out, or rolled back, etc.   
	Ingress: is for load balancing and virtual hosting  
	Namespace: cluster resources grouping.  
	Pod: one or more containers sharing the same pod resources.  
	Replicaset: declares the number of instances of a pod that is needed, and a Replication Controller manages the system so that the number of healthy pods that are running matches the number of pods declared in the ReplicaSet (determined by evaluating its selector).  
	Secret: the biggest difference between a secret and a configmap is that the content of the data in a secret is base64 encoded. Recent versions of Kubernetes have introduced support for encryption to be used as well. Secrets are often used to store data like certificates, passwords, pull secrets (credentials to work with image registries), and ssh keys.  
	Service: a Kubernetes service is a set of pods that work together, such as one tier of a multi-tier application.  
	Statefulset: are controllers that are provided by Kubernetes that enforce the properties of uniqueness and ordering amongst instances of a pod and can be used to run stateful applications  

3. What tools did you use to work with Kubernetes and what tasks did you solve?  
A:  
	I have tried only kubectl which is a CLI for Kubernetes HTTP REST API.

4. What is helm chart?  
A:  
	Helm chart is a set of files describing corresponding Kubernetes resources. It may be thought as an apt package while Helm tool is used to manage packages (charts).


5. What is an umbrella chart?  
A:  
	An umbrella chart is a complex chart having several other charts inside it. It can be used to compose more complex charts from other small charts.

## Tasks

* create helm charts for applications from [docker-compose](../03%20-%20docker-compose) task

* create an umbrella helm chart for you helm charts

* `*` Lint and deploy the umbrella helm chart

* `*` Deploy logging and monitoring tools for your users

A:
	Will be done.

