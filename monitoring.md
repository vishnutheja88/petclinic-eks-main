helm install prometheus prometheus-community/prometheus \
    --namespace prometheus \
    --set alertmanager.persistentVolume.storageClass="gp2" \
    --set server.persistentVolume.storageClass="gp2"

prometeheus namespace
pod -- Deployment ---svc --prometheus-server
namespace: prometheus 


grafana 
pod -- servicename.namespace.svc.cluster.local











app
appp

servicename.ns.svc.cluster.local

db-svc.db.svc.cluster.local




db
ns: db
service: db-svc















a

b-svc.svc.cluster.local


b 
ns:b
svc: b-svc



helm install grafana grafana/grafana \
    --namespace grafana \
    --set persistence.storageClassName="gp2" \
    --set persistence.enabled=true \
    --set adminPassword='EKS!sAWSome' \
    --values ${HOME}/environment/grafana/grafana.yaml 
