# This is only temporary, need to find a better way to figure this out.

1. Apply Namespace file
2. Apply NodePort file
3. Apply Ingress file
4. Run the following commands

## Install the PostgreSQL

Install PostgreSQL
helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo update
helm install coder-db bitnami/postgresql \
    --namespace coder \
    --set auth.username=coder \
    --set auth.password=coder \
    --set auth.database=coder \
    --set persistence.size=10Gi

# Add the helm repo for coder
helm repo add coder-v2 https://helm.coder.com/v2

# Update Helm Repo
helm repo update

# Create the secret that links to database
kubectl create secret generic coder-db-url -n coder \
   --from-literal=url="postgres://coder:coder@coder-db-postgresql.coder.svc.cluster.local:5432/coder?sslmode=disable"

# Apply changes and install coder
helm install coder coder-v2/coder \
    --namespace coder \
    --values values.yaml