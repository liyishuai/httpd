REPO=ysli/httpd
BRANCH=$(shell git rev-parse --abbrev-ref HEAD)
IMAGES=$(shell docker images $(REPO) -q)
CONTAINERS=$(shell docker ps -f name=$(REPO) -q)

ifneq ($(BRANCH), master)
	REPO:=$(REPO):$(BRANCH)
endif

all: clean
	docker build -t $(REPO) .
	docker push $(REPO)

clean:
	-docker rm  -f $(CONTAINERS)
	-docker rmi -f $(IMAGES)
