# helm-promgraf
## Prerequisite

- Helm3
- Kubernetes cluster (minikube)
- ✨Magic ✨

## Features - kube-prometheus-stack

- Prometheus operator
- Prometheus
- Alertmanager
- Prometheus node-exporter
- Prometheus Adapter
- kube-state-metrics
- Grafana

Add to helm3 repository:
```sh
$ helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
```

Create namespace 
```sh
$ kubectl create ns prom
```

Install prom stack
```sh
$ helm install prometheus prometheus-community/kube-prometheus-stack -n prom
```

Access prometheus dashboard
```sh
$ kubectl port-forward -n prom prometheus-prom-kube-prometheus-stack-prometheus-0 9090
```

Access grafana dashboard
username: admin
password: prom-operator
```sh
$ kubectl port-forward -n prom prom-grafana-6c578f9954-rjdmk 3000
```

Uninstall
```sh
$ helm uninstall prom -n prom
```

Remove CRDs
```sh
$ kubectl delete crd alertmanagerconfigs.monitoring.coreos.com
$ kubectl delete crd alertmanagers.monitoring.coreos.com
$ kubectl delete crd podmonitors.monitoring.coreos.com
$ kubectl delete crd probes.monitoring.coreos.com
$ kubectl delete crd prometheuses.monitoring.coreos.com
$ kubectl delete crd prometheusrules.monitoring.coreos.com
$ kubectl delete crd servicemonitors.monitoring.coreos.com
$ kubectl delete crd thanosrulers.monitoring.coreos.com
```
