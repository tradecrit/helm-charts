helm upgrade --install \
--namespace minio-operator \
--create-namespace \
operator . \
--values ./values.yaml
