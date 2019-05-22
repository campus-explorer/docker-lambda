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
