FROM nvcr.io/nvidia/cuda:12.5.1-cudnn-devel-ubuntu22.04
# Does NOT work for CUDA 12.6 and above (https://github.com/icl-utk-edu/papi/issues/225)

# install some utils...
RUN apt update
RUN apt install -y git

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

# set environment variables
ENV PATH=${PAPI_DIR}/bin:$PATH
ENV LD_LIBRARY_PATH=${PAPI_DIR}/lib:$LD_LIBRARY_PATH
