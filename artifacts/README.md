# README


Fetch
```bash
helm repo add vmware-tanzu https://vmware-tanzu.github.io/helm-charts
helm repo update
helm pull vmware-tanzu/velero --untar
```

Run
```bash
# create secret 
kubectl create secret generic cloud-credentials \
  --from-env-file=cloud-credentials \
  --namespace velero


helm install velero ./velero  --namespace velero --create-namespace --values override.yaml

# or if already exists
helm list --namespace velero
helm status velero -n velero

helm upgrade velero ./velero --namespace velero --values override.yaml
```