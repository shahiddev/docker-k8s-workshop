## Accessing the Kubernetes Dashboard

Before you can access the Kubernetes dashboard you need to grant permissions

Firstly ensure you have set the local context by getting the credentials:

```cmd
az aks get-credentials -n k8s-workshop -g k8s-workshoprg
```

Create the permissions by running:

```cmd
kubectl create clusterrolebinding kubernetes-dashboard --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
```

We can now view the dashboard by executing:

```cmd
az aks browse -n k8s-workshop -g k8s-workshoprg
```

This command will create a secure tunnel from your machine to the cluster and pop open a browser to display the Kubernetes dashboard.

**Important** Do not be tempted to expose the Kubernetes dashboard publicly (via a loadbalancer service) without first understanding the risks - there have been several cluster hijacks (e.g. for crypto mining due to people doing this)