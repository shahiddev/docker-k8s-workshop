# Autoscaling

This exercise gives you an introduction to autoscaling, it is based the autoscaling example found in the Kubernetes documentation.

## Horizontal pod autoscaling

In this walkthrough we are going to deploy an application which is going to demonstrate horizontal scaling, this is achieved by increasing the number of pods (e.g instances) of the application so we can handle the load.

The sample app is doing nothing more than a bit of computation which is going to generate some CPU load, we will run a pod which is going to repeatedly hit that application and cause the load.

### Steps

1. Deploy the manifest files in this folder (these are a deployment and service and the horizontal pod autoscaler)
2. Run the following command to create a temporary pod which is going to be used to generate the load `kubectl run -it --rm load-generator --image=busybox /bin/sh`
3. Once you are in the pod you can execute the following command `while true; do wget -q -O- http://php-apache; done` this command is going to call the application we deployed in step 1 repeatedly in a loop until we break out of the loop
4. Open a new terminal and query the hpa by running `kubectl get hpa` you should see something similar to this 

   ```cmd
    NAME             REFERENCE               TARGETS   MINPODS   MAXPODS   REPLICAS   AGE
    php-apache-hpa   Deployment/php-apache   0%/50%    1         10        1          2m51s

   ```
5. It may take a minute or two but eventually you should see the HPA showing the load is above the target 50% and the replica count should start increasing
   
   ```cmd
    NAME             REFERENCE               TARGETS    MINPODS   MAXPODS   REPLICAS   AGE
    php-apache-hpa   Deployment/php-apache   249%/50%   1         10        4          4m
   ```
6. You can query the number of pods by running `kubectl get pods` and you should see the additional replicas
7. Kill the load by pressing `CTRL+C` in the terminal which is currently running the load test


### Clean up

The load test pod will automatically be removed (note the `--rm`) but you will need to delete the deployment, service and hpa. You can do this by running `kubectl delete -f .` if you are still in the same folder as the manifest files