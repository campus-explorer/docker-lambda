# docker-lambda

Docker images for working with lambda

## Updating

To build and push an individual image, change to that image's directory, then run:

    docker build -t campusexplorer/${PWD##*/} .
    docker login
    docker push campusexplorer/${PWD##*/}

## base-node8

- node 8 lambda environment
- yarn installed
- `APPDIR` and `APPUSER` initialized

## psql

- installed Postgres client to lambda environment OS.

Use like so:

```
COPY --from=campusexplorer/psql:latest /usr/local/pgsql /usr/local/pgsql
ENV PATH=$PATH:/usr/local/pgsql/bin
```
