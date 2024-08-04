# Kubernetes Dashboard auth

## How?

Run them first.
```sh=
kubectl apply -f admin_user_service_account.yaml
kubectl apply -f admin_user_cluster_role_binding.yaml
kubectl apply -f admin_user_secret_account.yaml
kubectl get secret admin-user -n kubernetes-dashboard -o jsonpath={".data.token"} | base64 -d
```
Copy the token then run
```sh=
kubectl -n kubernetes-dashboard port-forward svc/kubernetes-dashboard-kong-proxy 8443:443
```
Access https://localhost:8443, then paste the token into the input. That's all!