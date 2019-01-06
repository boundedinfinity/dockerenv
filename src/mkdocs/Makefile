makefile_dir 	:= $(abspath $(shell pwd))

docker_service	:= mkdocs
docker_tag		:= $(shell cat docker-compose.yml | grep image | grep $(docker_service) | sed 's/.*image://' | tr -d ' ')

.PHONY: list docker-build docker-run docker-push

list:
	@grep '^[^#[:space:]].*:' Makefile | grep -v ':=' | grep -v '^\.' | sed 's/:.*//g' | sed 's/://g' | sort

tag:
	@echo $(docker_tag)

up:
	docker-compose up $(docker_service)

stop:
	docker-compose stop $(docker_service)

build:
	docker-compose build $(docker_service)

ash:
	docker-compose run --rm $(docker_service) ash

push:
	cat $(DOCKER_PASSWORD_FILE) | docker login $(DOCKER_REPO) --username '$(DOCKER_USERNAME)' --password-stdin
	docker push $(docker_tag)

bumpversion:
	docker-compose run --rm bumpversion tini bumpversion patch --allow-dirty
