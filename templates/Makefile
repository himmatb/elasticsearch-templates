TEMPLATE_NAME = com.redhat.viaq-openshift

.PHONY: all templates index_pattern

INDEX_PATTERN_DIRS = openshift,collectd_metrics

all: templates index_pattern

templates:
	for dir in {$(INDEX_PATTERN_DIRS)}; do \
		cd $$dir ; \
		make all; \
		cd .. ; \
	done

index_pattern:
	python ../scripts/concat_index_pattern_fields.py \
		"$(INDEX_PATTERN_DIRS)" "*.index-pattern.json" \
		"$(TEMPLATE_NAME).<ES_VERSION>.index-pattern.json"
