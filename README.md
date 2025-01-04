# devops_project_bookinfo


kubectl apply -f https://raw.githubusercontent.com/istio/istio/release-1.24/samples/bookinfo/platform/kube/bookinfo.yaml
kubectl port-forward svc/productpage 80:9080
http://127.0.0.1/productpage

https://argo-cd.readthedocs.io/en/stable/getting_started/
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
kubectl config set-context --current --namespace=argocd
argocd login --core
argocd admin initial-password -n argocd

kubectl port-forward svc/argocd-server -n argocd 8080:443



https://github.com/istio/istio/releases/tag/1.24.2

# istioctl install --set profile=demo

# kubectl get all -n istio-system

https://istio.io/latest/docs/examples/bookinfo/

# kubectl label namespace default istio-injection=enabled

# kubectl apply -f samples/bookinfo/platform/kube/bookinfo.yaml

kubectl apply -f samples/bookinfo/networking/bookinfo-gateway.yaml

kubectl get gateway

kubectl get svc -n istio-system

http://a595ada2277ff4df7a7f9752a966ec06-1616514819.ap-south-1.elb.amazonaws.com/productpage

kubectl apply -f samples/bookinfo/networking/destination-rule-all.yaml

kubectl get destinationrules -o yaml



kubectl apply -f samples/addons
kubectl rollout status deployment/kiali -n istio-system

kubectl -n istio-system get svc kiali

curl  -o /dev/null  -s -w %{http_code} http://a595ada2277ff4df7a7f9752a966ec06-1616514819.ap-south-1.elb.amazonaws.com/productpage


istioctl dashboard kiali

kubectl -n istio-system get svc prometheus

istioctl dashboard prometheus

istio_requests_total
Total count of all requests to the productpage service:

istio_requests_total{destination_service="productpage.default.svc.cluster.local"}

Total count of all requests to v3 of the reviews service:

istio_requests_total{destination_service="reviews.default.svc.cluster.local", destination_version="v3"}

Rate of requests over the past 5 minutes to all instances of the productpage service:

rate(istio_requests_total{destination_service=~"productpage.*", response_code="200"}[5m])

https://prometheus.io/docs/prometheus/latest/querying/basics/


kubectl -n istio-system get svc grafana

istioctl dashboard grafana





kubectl apply -f samples/bookinfo/networking/virtual-service-all-v1.yaml -n default

kubectl apply -f samples/bookinfo/networking/virtual-service-reviews-50-v3.yaml -n default

kubectl apply -f samples/bookinfo/networking/virtual-service-reviews-v3.yaml -n default





https://istio.io/latest/docs/tasks/observability/metrics/querying-metrics/

https://istio.io/latest/docs/tasks/observability/metrics/using-istio-dashboard/

https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing


https://istio.io/latest/docs/examples/bookinfo/

https://github.com/istio/istio/tree/master/samples/bookinfo



