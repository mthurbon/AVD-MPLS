### Generic Variables
SHELL := /bin/zsh

.PHONY: help
help: ## Display help message (*: main entry points / []: part of an entry point)
	@grep -E '^[0-9a-zA-Z_-]+\.*[0-9a-zA-Z_-]+:.*?## .*$$' $(MAKEFILE_LIST) | sort | awk 'BEGIN {FS = ":.*?## "}; {printf "\033[36m%-30s\033[0m %s\n", $$1, $$2}'

.PHONY: mpls-build
mpls-build: ## Build all mpls
	ansible-playbook playbooks/mpls-build.yml --diff

.PHONY: mpls-build-cv-studios
mpls-build-cv-studios:
	ansible-playbook playbooks/mpls-build-cv-studios.yml --diff

.PHONY: mpls-fabric-validate
mpls-fabric-validate:
	ansible-playbook playbooks/mpls-fabric-validate.yml

.PHONY: mpls-build-deploy-eapi
mpls-build-deploy-eapi:
	ansible-playbook playbooks/mpls-build-deploy-eapi.yml --diff