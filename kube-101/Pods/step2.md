You can create a namespace with a single command. Lets create a **team-a** namespace in our cluster:

``kubectl create namespace team-a``{{execute}}

Alternatively, like with any Kubernetes resource, we could have specified the namespace in a yaml file. Take a look at **manifests/team-b-namespace.yaml**

``cat manifests/team-b-namespace.yaml``{{execute}}

## Create team-b Namespace

Let's create the team-b namespace using the yaml file.

``kubectl apply -f manifests/team-b-namespace.yaml`` {{execute}}

## List Namespaces

Let's check the namespaces we have now:

``kubectl get namespaces``{{execute}}