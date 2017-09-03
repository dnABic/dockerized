NAME = dnabic/saltstack
VERSION = 0.1.1

all: build

build:
	docker build -f Dockerfile.systemd -t $(NAME):$(VERSION) .

run:
	docker run --name=saltsystemdtest \
		--cap-add=SYS_ADMIN \
		--detach \
		--volume /sys/fs/cgroup:/sys/fs/cgroup:ro \
		--tmpfs /run \
		--tmpfs /run/lock \
		$(NAME):$(VERSION)

compose:
	docker-compose up -d

.PHONY: all build run compose
