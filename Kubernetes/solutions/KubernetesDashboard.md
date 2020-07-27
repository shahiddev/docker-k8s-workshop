## Accessing the Kubernetes Dashboard

The Kubernetes Dashboard component is due to be switched off in AKS clusters from v1.18 onwards.

Please see the AKS documentation around accessing the dashboard, the approach you need to take will depend on the version of AKS you're running.

https://docs.microsoft.com/en-us/azure/aks/kubernetes-dashboard

**Important** Do not be tempted to expose the Kubernetes dashboard publicly (via a loadbalancer service) without first understanding the risks - there have been several cluster hijacks (e.g. for crypto mining due to people doing this)