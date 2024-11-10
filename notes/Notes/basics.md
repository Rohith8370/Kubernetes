# Kubernetes cluster

A Kubernetes cluster consists of a control plane plus a set of worker machines, called nodes, that run containerized applications. Every cluster needs at least one worker node in order to run Pods.

# Nodes

A Kubernetes node can be defined as a machine (either physical or virtual) that runs one or more containers organized into pods. Each node is equipped with the necessary services to manage these pods and communicate with the Kubernetes control plane.
## Types of Nodes
1. Control Plane Node (Master Node):
    * This node contains the core components of Kubernetes, including the API server, etcd (a key-value store for cluster state), controller manager, and scheduler. It manages the cluster's overall state and makes decisions about scheduling and scaling.
  
2. Worker Node:
   * Worker nodes are where application pods are deployed. Each worker node runs a kubelet, which is responsible for managing the pods on that node, ensuring they are running correctly, and communicating with the control plane.
  
# Pod

Pods serve as the basic building blocks for deploying applications in Kubernetes. They are scheduled onto nodes (the worker machines in a Kubernetes cluster) by the Kubernetes scheduler