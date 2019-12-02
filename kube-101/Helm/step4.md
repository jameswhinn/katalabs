Helm deploys all the pods, replication controllers and services. The pod will be in a pending state while the container image is downloaded and until a Persistent Volume is available. Once complete it will move into a running state.

Use the get command to find out what was deployed.

``watch kubectl get deployments,pods,services``{{execute}}

The Pod will be in a pending state while the container image is downloaded and until a Persistent Volume is available. You will see a master and two slave[^1] pods. Use this clear to break out of the watch or press +.

``kubectl apply -f pv.yaml``{{execute}}

Redis needs permissions to write to these mount points.

``mkdir /mnt/data1 /mnt/data2 /mnt/data3 --mode=777``{{execute}}

``watch kubectl get deployments,pods,services``{{execute}}

The Pods will move to the ContainerCreating state then once complete, the Pods will move to the running state. It will be a few moments and all the Deployments will eventually move to the available (1) state. Use this clear to break out of the watch or press +.

You have successfully installed a Redis cluster on Kubernetes.