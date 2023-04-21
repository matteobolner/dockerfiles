FROM ubuntu
ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update && \
    apt-get -y install gcc build-essential libz-dev git python3 python3-setuptools && git clone https://github.com/millanek/Dsuite.git && cd Dsuite && make && cd utils && python3 setup.py install --user --prefix= && cd 
