helm upgrade --install loki grafana/loki -n monitoring -f loki/values.yaml
--set loki.storage.s3.secretAccessKey=$MINIO_SECRET_KEY
