
export BASE = helm
export CHART = postgresql
export NAMESPACE = postgresql
export REPO = bitnami
export URL = https://charts.bitnami.com/bitnami
export VERSION = 12.2.1

include ../Makefile.kustomize

preinstall:
_PHONY: preinstall

seal:
	@kubectl create configmap postgresql-init \
		--from-file=seed.sql=envs/$(K8S_CTX)/seed.sql \
		--namespace=$(NAMESPACE) --output yaml --dry-run=client > "envs/$(K8S_CTX)/configmap.yaml"
	@kubectl create secret generic postgresql \
		--from-literal=postgres-password="$(POSTGRES_PASSWORD)" \
		--namespace $(NAMESPACE) --output yaml --dry-run=client | \
		kubeseal --cert="$(K8S_CTX_CERT)" --format=yaml > "envs/$(K8S_CTX)/secret.yaml"
_PHONY: seal

