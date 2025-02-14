helm upgrade --install grafana . -n monitoring -f values.yaml \
--set loki.loki.storage.s3.accessKeyId=$SPACES_ACCESS_KEY_ID \
--set loki.loki.storage.s3.secretAccessKey=$SPACES_SECRET_ACCESS_KEY


kubectl create -f https://raw.githubusercontent.com/prometheus-operator/prometheus-operator/master/bundle.yaml
