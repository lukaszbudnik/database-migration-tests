# database-migration-tests

With docker I now install containers rather than applications and frameworks. I don't have to juggle home dirs, classpaths, rvms, pyenvs, etc. I just drop in a container and discard it when no longer needed. My OS stays tidy.

And this project is basically a simple `docker-compose.yml` which I used for performance testing of 2 DB migration frameworks. The docker-compose creates the following containers:

* postgres - the database
* pgadmin4 - UI for PostgreSQL
* ruby - test environment #1 with `stdin_open` and `tty` set to `true` allowing attaching to running container
* golang - test environment #2 with `stdin_open` and `tty` set to `true` allowing attaching to running container

## usage

Run it with `CODE_DIR` variable:

```
CODE_DIR="$HOME/xxx" docker-compose up -d
```

Attach to container with ruby installed (the `databasemigrationtests` is the default prefix generated from `database-migration-tests` directory name):

```
bash -c "clear && docker exec -it databasemigrationtests_ruby_1 sh"
```

Attach to container with golang installed:

```
bash -c "clear && docker exec -it databasemigrationtests_golang_1 sh"
```

Once finished bring down the containers:

```
CODE_DIR="$HOME/xxx" docker-compose down
```
