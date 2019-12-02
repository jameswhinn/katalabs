The newly deployed nginx container is a light weight web server. We will need to create a service to view the default welcome page.

To expose a deployment we use the ```expose``` command:

``kubectl expose deployment/nginx``{{execute}}

## OOPS!! Error!!

As we have not declared port to use we will get following error.

```
error: couldn't find port via --port flag or introspection
See 'kubectl expose -h' for help and examples.
```

This is because we haven't described the port for our pod to listen on. To do this open first.yaml 

``vim first.yaml``{{execute}}

Locate the container configuration block and add the port declaration as shown below.

```
spec:
    containers:
    - image: nginx
        imagePullPolicy: Always
        name: nginx
        ports:                               # Add these
        - containerPort: 80                  # three
            protocol: TCP                      # lines
        resources: {}
```

Save the file and replace old file with new one:

``kubectl replace -f first.yaml``{{execute}}

View the Pod and Deployment: 

``kubectl get deploy,pod``{{execute}} 

**Note**  the AGE shows the Pod was re-created.

Now let's try to expose the resource again:
 
``kubectl expose deployment nginx``{{execute}}

Verify the service configuration:

``kubectl get svc nginx``{{execute}} 

The output should show something similar to below.

```
NAME      TYPE         CLUSTER-IP      EXTERNAL-IP   PORT(S)   AGE
nginx     ClusterIP    10.100.61.122   <none>        80/TCP    3
```

Also have a look at endpoint information:

``kubectl get ep nginx``{{command}}

Take a note of a current endpoint IP. We can test access to the Cluster IP by using curl:
 
``curl <cluster-ip>``{{execute}}