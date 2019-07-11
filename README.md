# docker-lambda

Docker images for working with lambda

## Updating

To build and push an individual image, change to that image's directory, then run:

    docker build -t campusexplorer/${PWD##*/} .
    docker login
    docker push campusexplorer/${PWD##*/}

## base-node8

IMPORTANT: This is a public image

- node 8 lambda environment
- yarn installed
- `APPDIR` and `APPUSER` initialized

## psql

IMPORTANT: This is a public image

- installed Postgres client to lambda environment OS.

Use like so:

```
COPY --from=campusexplorer/psql:latest /usr/local/pgsql /usr/local/pgsql
ENV PATH=$PATH:/usr/local/pgsql/bin
```

## jq

IMPORTANT: This is a public image

- installed jq to lambda environment OS.

Use like so:

```
COPY --from=campusexplorer/jq:latest /usr/bin/jq /usr/bin/jq
```
