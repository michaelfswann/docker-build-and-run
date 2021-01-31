# docker-build-and-run

Shell script to save time when building and running docker images locally.

## Usage

`bash ../bash-practise/docker-build-and-run.sh -a IMAGE_NAME -b HOST_PORT -c CONTAINER_PORT`

1. Script builds docker image using DOCKERFILE in current directory giving the image the title IMAGE_NAME

         `docker build -t "${IMAGE_NAME}"` .

2. Script runs the image using following flags:

   - --rm flag sets cleanup
   - -it flag sets interactive and tty
   - --name sets container name to IMAGE_NAME
   - -p maps host port to container port eg 3000:8080

         `docker run --rm -it --name "${IMAGE_NAME}" -p "${MAP_HOST_PORT}:${MAP_CONTAINER_PORT}" "$(docker images | awk '{print $3}' | awk 'NR==2')"`

3. Final part of the script manipulates output of docker images using awk to return the third column of the result then shortens to first row leaving us with just the IMAGEID of the most recently built image:

         this part => `$(docker images | awk '{print $3}' | awk 'NR==2')`

### Checked with [ShellCheck](https://github.com/koalaman/shellcheck)
