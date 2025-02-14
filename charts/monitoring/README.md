helm upgrade --install loki grafana/loki -n monitoring -f loki/values.yaml \
--set loki.storage.s3.secretAccessKey=$MINIO_SECRET_KEY

helm upgrade --install grafana . -n monitoring -f values.yaml \
--set tempo.storage.trace.s3.secret_key=$MINIO_SECRET_KEY \
--set loki.loki.storage.s3.secretAccessKey=$MINIO_SECRET_KEY \
--set mimir.mimir.structuredConfig.common.storage.s3.secret_access_key=$MINIO_SECRET_KEY
```

kubectl create -f https://raw.githubusercontent.com/prometheus-operator/prometheus-operator/master/bundle.yaml
