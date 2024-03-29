**Pods** are generally the lowest level object we interact with during daily use of Kubernetes. Pods are a logical grouping of one or more containers.

**Namespaces** can be thought of as virtual boundaries within your Kubernetes cluster ensuring objects within one namespace are isolated from those within another. Namespaces can be leveraged to improve organisation, security and performance. When deploying pods, we define which namespace they should reside in.

**Labels** are pieces of metadata which we attatch to objects in Kubernetes. Labels can then be used when we query the cluster to interact or retrieve information about those objects.

**kubectl** is a CLI tool which we use to communicate with the Kubernetes API. You wil generally use this tool in conjunction with various YAML files in order to create cluster configuration and objects.