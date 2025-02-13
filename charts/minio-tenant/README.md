helm upgrade --install \
--namespace minio-tenant \
--create-namespace \
tenant . \
--values ./values.yaml
