release_name = cert-manager
chart_repo = https://charts.jetstack.io
chart_name = cert-manager
chart_version = 1.6.1
namespace = cluster-service-cert-manager

template:
	mkdir -p base
	helm template $(release_name) $(chart_name) --version $(chart_version) --namespace $(namespace) --repo ${chart_repo} --values values.yaml > base/template.yaml

values: 
	helm show values $(chart_name) --version $(chart_version) --repo ${chart_repo} > values.yaml

install:
	kustomize build base | kubectl apply -f -

uninstall:
	kustomize build base | kubectl delete -f -