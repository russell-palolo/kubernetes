## iterate services and call default make target
init:
	@# find . -type d -maxdepth 1 -exec make -C {} \;
	@for f in $(shell ls -d */); do echo "Initializing $$f ..."; make -C $$f; done
_PHONY: init

## prepare sealed secrets for selected context
secrets:
	@for f in $(shell ls -d */); do echo "Sealing Secrets for $$f ..."; make -C $$f seal; done
_PHONY: secrets

## prepare sealed secrets for selected context
update:
	@for f in $(shell ls -d */); do echo "Searching for update for $$f ..."; make -C $$f update; done
_PHONY: update
