makefile_dir 	:= $(abspath $(shell pwd))

docker_service	:= mkdocs
docker_tag		:= $(shell cat docker-compose.yml | grep image | grep $(docker_service) | sed 's/.*image://' | tr -d ' ')
docker_compose 	:= docker-compose run --rm --service-ports mkdocs tini mkdocs

.PHONY: list docker-build docker-run docker-push

list:
	@grep '^[^#[:space:]].*:' Makefile | grep -v ':=' | grep -v '^\.' | sed 's/:.*//g' | sed 's/://g' | sort

serve:
	$(docker_compose) serve
