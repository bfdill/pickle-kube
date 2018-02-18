# kubernetes dashboard

[Github repo](https://github.com/kubernetes/dashboard/tree/master/src/deploy)

## installation

This command will install the latest version of the dashboard
```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/master/src/deploy/recommended/kubernetes-dashboard-arm.yaml
```

## access

Finding your dashboard
```bash
kubectl get svc --namespace=kube-system
```

  NAME                   TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)         AGE
  kube-dns               ClusterIP   10.96.0.10       <none>        53/UDP,53/TCP   33d
  kubernetes-dashboard   NodePort    10.100.234.213   <none>        443:31821/TCP   17d

You should be able to hit your dashboard at http://clusterip:31821 (in think example).

In order to [access](https://github.com/kubernetes/dashboard/wiki/Accessing-Dashboard---1.7.X-and-above) the [dashboard](https://github.com/kubernetes/dashboard), you'll need to have a [bearer token](https://kubernetes.io/docs/admin/authentication/#putting-a-bearer-token-in-a-request)

```bash
# get the token needed for bearer authentication
kubectl get secret $(kubectl get serviceaccount dashboard -o jsonpath="{.secrets[0].name}") -o jsonpath="{.data.token}" | base64 --decode
```

## editing the service
changing type from nodeport to cluster ip for e.g.

```bash
kubectl -n kube-system edit service kubernetes-dashboard
```