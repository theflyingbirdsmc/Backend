## Setting up PostgreSQL and Coder

1. Apply the Namespace file:
   - This file creates a namespace to isolate the resources. It helps organize and manage the components. You can use the following command to apply it:
     ```shell
     kubectl apply -f namespace.yaml
     ```

2. Apply the NodePort file:
   - The NodePort file defines the configuration for exposing the Coder service using a NodePort. This allows external access to Coder. Apply the file by running the following command:
     ```shell
     kubectl apply -f nodeport.yaml -n coder
     ```

3. Apply the Ingress file:
   - The Ingress file sets up an Ingress resource to enable access to Coder using an Ingress controller. Apply the file using the following command:
     ```shell
     kubectl apply -f ingress.yaml -n coder
     ```

4. Install PostgreSQL:
   - PostgreSQL is a powerful open-source relational database management system. We'll use Helm to install it. Run the following commands to install PostgreSQL:
     ```shell
     helm repo add bitnami https://charts.bitnami.com/bitnami
     helm repo update
     helm install coder-db bitnami/postgresql \
         --namespace coder \
         --set auth.username=coder \
         --set auth.password=coder \
         --set auth.database=coder \
         --set persistence.size=10Gi
     ```

5. Create a secret for the PostgreSQL connection URL:
   - We need to create a secret that contains the connection URL to the PostgreSQL database. Use the following command to create the secret:
     ```shell
     kubectl create secret generic coder-db-url -n coder \
         --from-literal=url="postgres://coder:coder@coder-db-postgresql.coder.svc.cluster.local:5432/coder?sslmode=disable"
     ```

6. Install Coder:
   - Coder is a platform that allows you to develop code remotely. We'll use Helm to install it. Run the following commands:
     ```shell
     helm repo add coder-v2 https://helm.coder.com/v2
     helm repo update
     helm install coder coder-v2/coder \
         --namespace coder \
         --values values.yaml
     ```

Congratulations! You've successfully set up PostgreSQL and installed Coder in your Kubernetes cluster. The NodePort and Ingress configurations have been applied to enable external access to Coder.

Note: Make sure to adjust the commands according to your specific environment and requirements.
