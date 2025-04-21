This Dockerfile adds PAPI and cyPAPI to any Docker container that meets the
requirements. See the first few lines of the Dockerfile to see those
requirements.

# Usage
`docker build --build-arg BASE_IMAGE=<your_img_repo>:<your_img_tag> -t <new_img_name> .`

You can find both your image repo and your image tag through `docker images`.
Example:
```
$ docker images
REPOSITORY                    TAG          IMAGE ID       CREATED          SIZE
example                       latest       1a8c3eb59bec   25 minutes ago   7GB
```
