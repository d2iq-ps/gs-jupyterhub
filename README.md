# DKP Custom Catalog Application: JupyterHub

Your custom catalog is ready to deploy to DKP. Set the namespace to the relevant project, as an environmental variable:

```bash
export NAMESPACE=[your_namespace]
````

Copy and paste the following into the terminal to deploy the catalog:

```bash
kubectl apply -f - <<EOF
apiVersion: source.toolkit.fluxcd.io/v1beta1
kind: GitRepository
metadata:
  name: ajb-juppy
  namespace: ${NAMESPACE}
  labels:
    kommander.d2iq.io/gitapps-gitrepository-type: catalog
    kommander.d2iq.io/gitrepository-type: catalog
spec:
  interval: 1m0s
  ref:
    branch: master
  timeout: 1m0s
  url: https://github.com/bovan01/ajb-juppy
EOF
```
