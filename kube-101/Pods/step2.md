You can create a namespace with a single command. Lets create a **Team-A** namespace in our cluster:

``kubectl create namespace Team-A``{{execute}}

Alternatively, like with any Kubernetes resource, we could have specified the namespace in a yaml file. Take a look at **manifests/Team-B-namespace.yaml**

``cat manifests/Team-B-namespace.yaml``{{execute}}

## Create Team-B Namespace

Let's create the team-b namespace using the yaml file.

``kubectl apply -f manifests/Team-B-namespace.yaml`` {{execute}}