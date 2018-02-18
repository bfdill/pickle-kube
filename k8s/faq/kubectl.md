# Random Notes

## k8s links
* [kubectl commands](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands)
* [cheatsheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)

## random commands
These commands should return the same result when run on any node in the cluster

### get
Display resources on the cluster.  By default, you only see your current namespace.  Probably default...  If you want to see all namespaces, no problem add --all-namespaces.

```bash
kubectl get all

# view cluster nodes
kubectl get nodes

# view pods
# shaving yaks? use po instead of pods
kubectl get pods

# this should be all the pods in all the namespaces
kubectl get pods --all-namespaces

# shows the pods that have been deployed to the cluster along with their desired, current, up-to-date, and available status.
kubectl get deployments

# shows the port mappings for services (svc)
kubectl get services

# details of the deployments that are, uh, deployed
kubectl describe deployments
```