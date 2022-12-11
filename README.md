# kubernetes-postgresql
Kubernetes Statefullset manifests for PostgreSQL

For full documentation, refer https://devopscube.com/deploy-postgresql-statefulset/

- Deploy PostgreSQL Statefulset in Kubernetes With High Availability :
 ## Prequistion :
 ****
 - Kubernetes cluster
 - Glusterfs storage for persist data out of the kubernetes cluster
 - Prometheus and Grafna for monitoring Postgresql culster
 ****
 - git clone https://github.com/meisammaleki/postgresql-cluster-in-kubernetes-with-prometheus-and-grafana-.git
 - kubectl create namespace database
 - cd to postgresql
 - kubectl apply -f postgres-configmap.yaml -n database
 - kubectl apply -f postgres-headless-svc.yaml -n database 
 ### note : we require a headless service because it is a requirement for the PostgresSQL statefulset.
 - https://kubernetes.io/docs/concepts/services-networking/service/#headless-services
 - kubectl apply -f postgres-secrets.yaml -n database
 - kubectl apply -f postgres-statefulset.yaml -n database
 
 ****
 #### Connect to PostgreSQL Cluster From Client :
 - kubectl apply -f psql-client.yaml -n database
 #### get encoded password to login in database with below command :
 - kubectl get secret postgres-secrets -n database -o jsonpath="{.data.postgresql-password}" | base64 --decode
 - kubectl exec -it pg-client -n database -- /bin/bash
 ****
 ### For monitoing we use grafana and prometheus
 #### first we have to install posgresql-exporter in kubernetes cluster that we do that by Helm installation :
 - helm install my-release prometheus-community/prometheus-postgres-exporter
 
#### default port is 80 , change it to another like 8880
#### add psql metric as a new scrab to prometheus config file :

 # scrape_config job
    - job_name : postgres
      static_configs :
       - targets: ['Nodeip:8880']

finally add it to Grafna

****

####

