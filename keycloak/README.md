# Keycloak

https://www.keycloak.org/

helmchart https://github.com/codecentric/helm-charts/tree/master/charts/keycloak

    kubectl -n keycloak create secret tls kube-ca-secret \
    --cert=/etc/kubernetes/ssl/ca.crt \
    --key=/etc/kubernetes/ssl/ca.key
    helm repo add codecentric https://codecentric.github.io/helm-charts
    helm template keycloak codecentric/keycloak -f values.yaml > manifests/02-keykloak.yaml
    kubectl -n keycloak apply -f manifests/00-certs.yaml
    kubectl -n keycloak apply -f manifests/01-secrets.yaml
    kubectl -n keycloak apply -f manifests/02-keykloak.yaml
    kubectl -n keycloak apply -f manifests/03-ingress.yaml