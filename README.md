# UTEP Campus Compute Containers

This is a repository of with different tools, created to be used for scientific high-performance computing.

# Usage
Navigate to the folder corresponding to the tool you need. Then, you have two options:
- Option 1: Get the Dockerfile, build the container locally
- Option 2: Use the link in the folder's README to download the built container directly from Dockerhub

## Docker cheatsheet
Here are some useful commands in case you've forgotten how to build & run docker containers:
- Build an image: Navigate to the desired Dockerfile directory, then `docker build -t <container_name> .`
- Running an image: `docker run -it <container> /bin/bash`
    - `--gpus=all` to enable GPU access

# Appendix
For any questions, feel free to email me at ashkan.arabim@gmail.com. Alternatively, reach out through any other social media platform (see my GitHub profile to see my handles).
