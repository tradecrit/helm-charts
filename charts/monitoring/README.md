```bash
helm create namespace monitoring

helm dependency update .

helm upgrade --install grafana . -n monitoring -f values.yaml \
--set loki.loki.storage.s3.accessKeyId=$SPACES_ACCESS_KEY_ID \
--set loki.loki.storage.s3.secretAccessKey=$SPACES_SECRET_ACCESS_KEY \
--set mimir.mimir.structuredConfig.common.storage.s3.access_key_id=$SPACES_ACCESS_KEY_ID \
--set mimir.mimir.structuredConfig.common.storage.s3.secret_access_key=$SPACES_SECRET_ACCESS_KEY \
--set tempo.storage.trace.s3.access_key=$SPACES_ACCESS_KEY_ID \
--set tempo.storage.trace.s3.secret_key=$SPACES_SECRET_ACCESS_KEY;

kubectl get pods -n monitoring | grep alloy | awk '{print $1}' | xargs kubectl delete -n monitoring pod

kubectl rollout restart deployment grafana
```


helm upgrade --install grafana . -n monitoring -f values.yaml \
--set loki.loki.storage.s3.accessKeyId=$SPACES_ACCESS_KEY_ID \
--set loki.loki.storage.s3.secretAccessKey=$SPACES_SECRET_ACCESS_KEY \
--set mimir.mimir.structuredConfig.common.storage.s3.access_key_id=$SPACES_ACCESS_KEY_ID \
--set mimir.mimir.structuredConfig.common.storage.s3.secret_access_key=$SPACES_SECRET_ACCESS_KEY \
--set tempo.storage.trace.s3.access_key=$SPACES_ACCESS_KEY_ID \
--set tempo.storage.trace.s3.secret_key=$SPACES_SECRET_ACCESS_KEY && \
kubectl get pods -n monitoring | grep alloy | awk '{print $1}' | xargs kubectl delete -n monitoring pod
