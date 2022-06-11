### Create namespace

kubectl create namespace chillplus-catalog -o yaml > namespace.yml

### Create configMap on namespace

kubectl create configmap <demo-config> --from-file=config.yaml -n <namespace>

### Describe configmap

kubectl describe configmap postgres-config -n chillplus-catalog

### Create secret 

kubectl create secret generic postgres-secret -n chillplus-catalog --from-file=secrets.yaml -o yaml > postgre-secret.yaml
