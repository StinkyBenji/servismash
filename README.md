# Service Mesh

Base example: bookinfo application
Please follow [the documentation](https://docs.openshift.com/container-platform/4.6/service_mesh/v2x/ossm-create-mesh.html)
for deploying the bookinfo example.

## TCP traffic
1. deploy posgresql in `bookinfo` (db client) and `bookinfo-db` (db server) namespace 
[Base documentation](https://istio.io/v1.12/docs/tasks/traffic-management/egress/egress-gateway/)

2. remember to enable sidecar injection for DB client 
by adding the following to the postgresql deploymentconfig:
```
spec:
  template:
    metadata:
      annotations:
        sidecar.istio.io/inject: 'true'
```

3. add port 5432 to smcp
[smcp configuration](https://docs.openshift.com/container-platform/4.7/service_mesh/v2x/ossm-reference-smcp.html)