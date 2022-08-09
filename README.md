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

## TLS traffic

### mtls between DB client and istio-egressgateway
```
tls:
  mode: ISTIO_MUTUAL
```
### mtls between istio-egressgateway and DB server



References:
[1] https://istio.io/v1.12/blog/2018/egress-mongo/
[2] https://istio.io/latest/blog/2019/egress-traffic-control-in-istio-part-1
[3]https://istio.io/latest/docs/tasks/traffic-management/egress/egress-gateway-tls-origination/#perform-tls-origination-with-an-egress-gateway
[4] https://luppeng.wordpress.com/2021/08/07/create-and-install-ssl-certificates-for-postgresql-database-running-locally/