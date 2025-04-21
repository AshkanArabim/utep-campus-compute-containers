# BASE IMAGE REQUIREMENTS:
# - Debian-based (because I've hardcoded "apt" for installing packages)
# - Cuda should already be installed
# - Cuda version < 12.6 should be installed. 12.6 and above are broken: https://github.com/icl-utk-edu/papi/issues/225
ARG BASE_IMAGE
FROM ${BASE_IMAGE}

# install some utils...
RUN apt update
RUN apt install -y git
RUN apt install -y python3
RUN apt install -y python3-pip

# clone, compile, and install PAPI
# instructinos pulled from:
    # installation docs: https://github.com/icl-utk-edu/papi/wiki/Downloading-and-Installing-PAPI
    # cuda-specific installation docs: https://github.com/icl-utk-edu/papi/tree/master/src/components/cuda
ENV PAPI_DIR=/usr/local
WORKDIR /root
RUN git clone https://github.com/icl-utk-edu/papi.git
WORKDIR /root/papi/src
RUN ./configure --with-components="cuda"
RUN make
RUN make install

# delete the cloned papi repo
WORKDIR /root
RUN yes | rm -r ./papi

# set papi environment variables
ENV PATH=${PAPI_DIR}/bin:$PATH
ENV LD_LIBRARY_PATH=${PAPI_DIR}/lib:$LD_LIBRARY_PATH

# install cyPAPI
# instructions: https://github.com/icl-utk-edu/cyPAPI
ENV PAPI_PATH=/usr/local
RUN git clone https://github.com/icl-utk-edu/cyPAPI.git
WORKDIR /root/cyPAPI
RUN make install
WORKDIR /root
RUN yes | rm -r cyPAPI
