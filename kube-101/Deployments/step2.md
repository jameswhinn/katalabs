When we asked kubernetes to create our deployment, it performed several step to achieve it. We can see that steps using a command

``kubectl get events``{{execute}}

As mentioned in previous scenarios, Kubernetes objects may be created directly at the CLI, as we just did with our deployment, or they can be created with a yaml file. We can export the configuration of our deployment so going forward we have the yaml config to replicate it.

``kubectl get deployment nginx -o yaml``{{execute}}

Let's save the output so we can use it:

``kubectl get deployment nginx -o yaml > first.yaml``{{execute}}

Now we need to clean the deployment file from arbartary config effects reusability. Open a file using ``vim first.yaml``{{command}} and remove creationTimestamp, resourceVersion, selfLink and uid lines. Also remove all lines including and after status. 

The resulting file should look similar to this:

```
apiVersion: extensions/v1beta1
kind: Deployment
metadata:
  annotations:
    deployment.kubernetes.io/revision: "1"
  creationTimestamp: 2019-05-20T12:53:41Z
  generation: 1
  labels:
    app: nginx
  name: nginx
  namespace: default
  spec:
  progressDeadlineSeconds: 600
  replicas: 1
  revisionHistoryLimit: 10
  selector:
    matchLabels:
      app: nginx
  strategy:
    rollingUpdate:
      maxSurge: 25%
      maxUnavailable: 25%
    type: RollingUpdate
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - image: nginx
        imagePullPolicy: Always
        name: nginx
        resources: {}
        terminationMessagePath: /dev/termination-log
        terminationMessagePolicy: File
      dnsPolicy: ClusterFirst
      restartPolicy: Always
      schedulerName: default-scheduler
      securityContext: {}
      terminationGracePeriodSeconds: 30
```

Now delete the existing deployment:

``kubectl delete deployment nginx``{{execute}}

Create a new deployment from our yaml file we just created:
 
``kubectl create -f first.yaml``{{execute}}

Now let's export the config of our new deployment and store it to file:

``kubectl get deployment nginx -o yaml > second.yaml``{{execute}}

Compare both files:

``diff first.yaml second.yaml``{{execute}} 

Notice the time stamp, resource version and uid we had deleted are in the new file. These are generated for each resource we create, so we need to delete them from yaml files to avoid conflicts or false information.