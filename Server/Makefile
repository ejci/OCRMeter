NAME=ocrmeter
REPO=makasim
REPONAME=$(REPO)/$(NAME)

build:
	docker build --rm --tag $(REPONAME) .

run:
	docker run --rm --interactive --tty -p 9090:9090 --name $(NAME) $(REPONAME)

rundev:
	docker run --rm --interactive --tty -p 9090:9090 --volume `pwd`:/app --name $(NAME) $(REPONAME) /bin/bash

runbash:
	docker run --rm -it --name $(NAME) $(REPONAME) /bin/bash

stop:
	docker rm --force $(NAME)

drop:
	docker rmi $(REPONAME)

rerun: stop run
