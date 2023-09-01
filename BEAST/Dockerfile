FROM openjdk:8

RUN apt-get update
# Install stuff required later
RUN apt-get install -y curl git

ARG DEBIAN_FRONTEND=noninteractive

ENV USER root

WORKDIR /root/


# Add BEAST 2
RUN curl -fsSLO https://github.com/beast-dev/beast-mcmc/releases/download/v1.10.4/BEASTv1.10.4.tgz \
	&& tar fxz BEASTv1.10.4.tgz

ENV PATH=/root/beast/bin:$PATH

# Install BEAGLE
RUN apt-get update && apt-get install -y cmake build-essential autoconf automake libtool pkg-config
RUN git clone --depth=1 https://github.com/beagle-dev/beagle-lib.git

RUN cd beagle-lib \
    && mkdir build \
    && cd build \
    && cmake -DBUILD_SSE=OFF -DBUILD=_CUDA=OFF .. \
    && make install \
    && ldconfig

ENV LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH

#RUN echo "#!/bin/bash\n" \
#        "export USER=root\n" > entrypoint.sh
#
#RUN chmod a+x entrypoint.sh
#
#ENTRYPOINT ["./entrypoint.sh"]
