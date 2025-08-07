# Setup

Fetch `v1.16.1` 
```bash
helm repo add vmware-tanzu https://vmware-tanzu.github.io/helm-charts
helm repo update
helm pull vmware-tanzu/velero --version 1.16.1 --untar
```

Run
```bash
# create secret (ping Daniel)
kubectl create ns velero
kubectl create secret generic cloud-credentials \
--from-env-file=cloud-credentials \
--namespace velero

# install
helm install velero ./velero  --namespace velero --values override.yaml

# or if already exists
helm upgrade velero ./velero --namespace velero --values override.yaml
```