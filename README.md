# docker-build-and-run

Shell script to save time when building and running docker images locally.

## Usage

`bash ../bash-practise/docker-build-and-run.sh -a IMAGE_NAME -b HOST_PORT -c CONTAINER_PORT`

1. Script builds docker image using DOCKERFILE in current directory giving the image the title IMAGE_NAME

2. Script runs the image:

   - --rm flag sets cleanup
   - -it flag sets interactive and tty
   - --name sets container name to IMAGE_NAME
   - -p maps host port to container port eg 3000:8080

3. Final part of the script manipulates output of docker images using awk to return the third column of the result then shortens to first row leaving us with just the IMAGEID of the most recently built image

### Checked with [ShellCheck](https://github.com/koalaman/shellcheck)
