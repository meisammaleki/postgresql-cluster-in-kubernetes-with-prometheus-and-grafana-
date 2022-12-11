# kubernetes-postgresql
Kubernetes Statefullset manifests for PostgreSQL

For full documentation, refer https://devopscube.com/deploy-postgresql-statefulset/

- Deploy PostgreSQL Statefulset in Kubernetes With High Availability :
 ## Prequistion :
 ****
 ### Kubernetes cluster
 ### Glusterfs storage for persist data out of the kubernetes cluster
 ### Prometheus and Grafna for monitoring Postgresql culster
 ****
 git clone https://github.com/meisammaleki/postgresql-cluster-in-kubernetes-with-prometheus-and-grafana-.git

 ****
default port is 80 , change it to another like 8880
add psql metric  it as a new job to prometheus config file

####

### postgresql exporter :
#### helm install my-release prometheus-community/prometheus-postgres-exporter
