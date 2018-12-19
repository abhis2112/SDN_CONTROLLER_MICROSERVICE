![image](https://user-images.githubusercontent.com/42255118/50248870-42f4ee00-0391-11e9-85b8-c50e2e2d7811.png)

# SDN_MICROSERVICE
A Floodlight Controller Deployed in Kubernetes Cluster as a Mircoservice

# Background
In the Software Defined Networking (SDN) Architecture, the control plane and data plane are decoupled which makes the control plane manage the underlying southbound data plane in a localized centralized method. However, the problem comes when to scale the SDN controller, facilitate High Availability and provide Resiliency.

This project delivers the concept of self-adjusting architecture for SDN network where the controller can be easily Scaled, perform High-Availability, and be Self-Resilient. This idea originates from deploying and running the Controller function as a Microservice (Running Controller inside a Pod) inside the Kubernetes Cluster and exposing the pod i.e. access to the outside network via service called NodePort. 

Kubernetes is an Open Source System for managing containerized application across multiple machines and provide the mechanism to easily deploy, manage, schedule and scale the application within the network.

However, there is a fair share of other container orchestration engine option like Mesos, Docker Swarm, and Nomad but currently, Kubernetes have the highest adoption rate and support large clusters running complex applications efficiently.

# Objective:
The goal of the project is to provide an architecture for SDN controller application which is scalable, Highly available and self-resilient. This will be done by deploying SDN controller as a container inside the Pod, run it as Microservice and provide the aforementioned features to the controller.


# Benefits:

1.	Efficient System Resources Utilization: As we are running the application as a containerized application that is light-weight and simple, we can deploy multiple instances sharing the same OS resource in a single virtual machine. Rather than providing whole VM to run just a single controller application that does not require that much CPU memory during idle time and do waste of bandwidth. 

2.	Scalability: The application deployed as a deployment can be scaled by mentioning a number of replicas in the kubectl command/manifest file. This will immediately spawn new pods to the number of replicas mentioned running the Controller Application.

3.	High Availability: The High-Availability is achieved by creating a Service in kubernetes. The service endpoint ensures that the user request reaches to either one of the pod from a group of pods running the identical application. This ensures unbroken application accessibility even if one pod is deleted/broken. The request will be diverted to the other pod.

4.	Resiliency: The replicas of an application deployed is maintained by the Replica-set which is the next generation Replication Controller. A Replica-Set ensures that the specified number of pod replicas should be running at any given time. Thus, if any pod gets destroyed or deleted somehow, the Replica-Set will come into action and deploy a new pod immediately ensuring the specified number. This facilitates faster and reliable resilient architecture with accepted bandwidth.
