```bash
kubectl create -f 1-db-postgres-pv.yaml
# persistentvolume/db-postgres created

kubectl get pv
# NAME          CAPACITY   ACCESS MODES   RECLAIM POLICY   STATUS      CLAIM   STORAGECLASS   REASON   AGE
# db-postgres   5Gi        RWX            Retain           Available           standard                4s

kubectl create -f 2-db-postgres-pvc.yaml
# persistentvolumeclaim/db-postgres created

kubectl get pvc
# NAME          STATUS   VOLUME        CAPACITY   ACCESS MODES   STORAGECLASS   AGE
# db-postgres   Bound    db-postgres   5Gi        RWX            standard       19s

kubectl get pv
# NAME          CAPACITY   ACCESS MODES   RECLAIM POLICY   STATUS   CLAIM                 STORAGECLASS   REASON   AGE
# db-postgres   5Gi        RWX            Retain           Bound    default/db-postgres   standard                76s

kubectl apply -f 3-db-postgres.yaml
# secret/postgresql created
# deployment.apps/db-postgres unchanged
# service/db-postgres unchanged

```