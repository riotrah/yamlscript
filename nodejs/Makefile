include ../common/base.mk

COFFEE := $(shell find src -type f -name '*.coffee')
JS := $(COFFEE:%.coffee=%.js)
JS := $(JS:src/%=lib/%)

NODE_MODULES := ../node_modules

export PATH := $(NODE_MODULES)/.bin:$(PATH)


#------------------------------------------------------------------------------
build:: $(JS)

lib/%.js: src/%.coffee ../node_modules
	@mkdir -p $(dir $@)
	coffee -c -p $< > $@

publish: build
	npm $@

clean::
	$(RM) package*

realclean:: clean
	$(RM) -r $(NODE_MODULES)

$(NODE_MODULES):
ifeq (,$(shell command -v npm))
	$(error *** 'npm' is required but not installed)
endif
	npm install --prefix=.. coffeescript
