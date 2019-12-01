You can create a namespace with a single command. Lets create a **team-a** namespace in our cluster:

``kubectl create namespace team-a``{{execute}}

Alternatively, like with any Kubernetes resource, we could have specified the namespace in a yaml file. Take a look at **manifests/team-b-namespace.yaml**

``cat manifests/team-b-namespace.yaml``{{execute}}

## Create team-b Namespace

Let's create the team-b namespace using the yaml file.

``kubectl apply -f manifests/team-b-namespace.yaml``{{execute}}

## List Namespaces

Let's check the namespaces we have now:

``kubectl get namespaces``{{execute}}

You can see that our additional two namespaces have now been created!!

## Delete Namespaces

To delete a namespace there are two options, as with resource creation we can use a yaml file or a specify the namespace at the commandline:

``kubectl delete -f /pods-manifests/team-b-namespace.yaml``{{execute}}

or 

``kubectl delete namespace team-b``{{execute}}

Let's check the team-b has been deleted successfully:

``kubectl get namespaces``{{execute}}

**NOTE** We will use the team-a namespace in the remainder of this scenario so do not delete this. If you have deleted, recreate before continuing.