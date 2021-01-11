kubectl apply -f namespace.yaml

kubectl apply -f configmap.yaml

kubectl apply -f headless.yaml

kubectl apply -f service.yaml

kubectl apply -f nfs-client-provisioner.yaml

kubectl apply -f rbac.yaml

kubectl apply -f storageclass.yaml

kubectl apply -f statefulset.yaml

kubectl exec -it -n redis-cluster redis-statefulset-0 -- redis-cli --cluster create --cluster-replicas 1 $(kubectl -n redis-cluster get pods -l app=redis -o jsonpath='{range.items[*]}{.status.podIP}:6379 ')
