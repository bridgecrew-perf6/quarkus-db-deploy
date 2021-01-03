# quarkus-db-deploy


# Sealed Secret

https://github.com/bitnami-labs/sealed-secrets

## install:

Operator:
kubectl apply -f https://github.com/bitnami-labs/sealed-secrets/releases/download/v0.13.1/controller.yaml

cli:
brew install kubeseal 


Create a sealed secret:

```
kubectl create secret generic quarkus-secret --from-file=../../quarkus-scratch-orm/config/security.properties -o yaml --dry-run=client | kubeseal -o yaml > sealed/db-credentials-sealed-secret.yaml
k apply -f sealed/db-credentials-sealed-secret.yaml

kubeseal --fetch-cert
```
