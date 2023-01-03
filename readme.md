# general
Goal of repository is to provide convenient source for getting config for devenv by author and, maybe, people who find it useful.

# usage and, possible, (part of) readme of future project

## local docker
docker should be installed to run commands below

## database
db name: app<br>
test db name: app_test<br>
user: app<br>
password: pass<br>

## xdebug
to xdebug expect port 9001

### prerequisites
in dev env container nginx and fpm workers works under app:app user that is 1000:1000 corresponding to default ubuntu user UID:GID, so no right issues expected. familiarize with Dockerfile precisely to understand how it work so
### to build and launch
```
docker build -t app .
docker run -d -p80:80 --add-host=host.docker.internal:host-gateway --name app -v ${PWD}:/var/www/html app
```

### to launch after built and launched
```
docker start app
```

### to enter for cli commands
with xdebug
```
docker exec -u${UID} -it -w /var/www/html app /bin/bash
```

without xdebug
```
docker exec -u${UID} -it -w /var/www/html -e XDEBUG_MODE=off app /bin/bash
```