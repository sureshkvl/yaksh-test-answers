REPOSITORY ?= yaksh-web
VERSION    ?= 1
BUILD_ID   ?= 2

REGISTRY   ?= sureshkvl
IMAGE      ?= $(REGISTRY)/$(REPOSITORY):$(VERSION).$(BUILD_ID)

BUILD_OPTIONS = -t $(IMAGE)

default: build

build:
	docker build $(BUILD_OPTIONS) .
	docker tag $(IMAGE) $(REGISTRY)/$(REPOSITORY):latest

push:
	docker push $(IMAGE)
	docker push $(REGISTRY)/$(REPOSITORY):latest

