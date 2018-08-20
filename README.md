# kubernetes cluster monitoring stack

## kubernetes dashboard

1. `helm install stable/kubernetes-dashboard --name k8s-dashboard --namespace=monitoring`
1. `helm install stable/oauth2-proxy --namespace=monitoring -f k8s-dashboard/proxy.yaml --name=k8s-dashboard-oauth2`
1. `helm upgrade --namespace=monitoring k8s-dashboard stable/kubernetes-dashboard -f k8s-dashboard/values.yaml`

## metrics

1. `helm repo add coreos https://s3-eu-west-1.amazonaws.com/coreos-charts/stable/`
1. `helm install coreos/prometheus-operator --name prometheus-operator --namespace monitoring`
1. `helm install stable/oauth2-proxy --namespace=monitoring -f kube-prometheus/proxy-grafana.yaml --name=k8s-prometheus-grafana-oauth2`
1. `helm install coreos/kube-prometheus --name k8s-prometheus --namespace monitoring -f kube-prometheus/values.yaml`
