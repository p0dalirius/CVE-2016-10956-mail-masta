.PHONY: all build

all: build run

build:
	docker build -t cve-2016-10956 -f Dockerfile .

run:
	docker run --rm -it \
		-p 8000:80 \
		cve-2016-10956
