### Create namespace

kubectl create namespace chillplus-catalog -o yaml > namespace.yml

### Create configMap on namespace

kubectl create configmap <demo-config> --from-file=config.yaml -n <namespace>
kubectl create configmap <demo-config> --from-literal=POSTGRES_DB=catalog --from-literal=POSTGRES_USER=catalog-user --from-literal=POSTGRES_HOST=postgres

### Describe configmap

kubectl describe configmap postgres-config -n chillplus-catalog

### Create secret 

kubectl create secret generic postgres-secret -n chillplus-catalog --from-file=secrets.yaml -o yaml > postgre-secret.yaml

kubectl create secret generic postgres-secret -n chillplus-catalog --from-literal=POSTGRES_PASSWORD=paraguay -o yaml > postgre-secret.yml

### Access on minkube postgresql

psql -h 192.168.49.2  -p 31161  -U catalog-user -W catalog

### Access pod 

 kubectl exec -it <pod> bash -n <namespace>


### Inside container

psql -h $(hostname)  -U catalog-user -p 5432 catalog -W
