```bash
helm create namespace monitoring

helm dependency update . && \

helm upgrade --install grafana . -n monitoring -f values.yaml

kubectl get pods -n monitoring | grep alloy | awk '{print $1}' | xargs kubectl delete -n monitoring pod

kubectl rollout restart deployment grafana
```


helm upgrade --install grafana . -n monitoring -f values.yaml \
kubectl get pods -n monitoring | grep alloy | awk '{print $1}' | xargs kubectl delete -n monitoring pod


docker run ghcr.io/open-telemetry/opentelemetry-collector-contrib/telemetrygen logs --duration 5s --otlp-insecure

kubectl port-forward grafana-alloy-jqhn7 4317:4317
