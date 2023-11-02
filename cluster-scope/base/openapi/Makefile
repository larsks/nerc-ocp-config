SOURCES = $(shell find resources -name schema.yaml -o -name kustomization.yaml)

all: openshift-api-schema.json

openshift-api-schema.json: $(SOURCES)
	kustomize build resources | \
		yq -s '{"definitions": [.[].definitions]|add}' > $@ || { rm -f $@; exit 1; }
