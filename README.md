
To make sure you can execute the RBAC roles and bindings make sure your own account is admin in the Kubernetes cluster.

```
ACCOUNT=$(gcloud info --format='value(config.account)')
kubectl create clusterrolebinding owner-cluster-admin-binding \
    --clusterrole cluster-admin \
    --user $ACCOUNT
```

To install kubernetes-cloudflare-sync run the following command:

```
cat kubernetes.yaml | HOSTNAME=nginx.myserver.com CF_API_EMAIL=*** CF_API_KEY=*** envsubst \$HOSTNAME,\$CF_API_EMAIL,\$CF_API_KEY | kubectl apply -f -
```