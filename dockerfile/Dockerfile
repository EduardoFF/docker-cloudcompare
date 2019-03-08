FROM ubuntu:xenial

ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update                                          &&\
    apt-get install -y git-core vim binutils                &&\
    apt-get install -y cmake g++ gcc                        &&\
    apt-get install -y libgdal-dev libfreenect-dev          \
                        libeigen3-dev libtbb-dev            \
                        libavcodec-dev libavformat-dev      \
                        libavutil-dev libboost-thread-dev   \
                        libboost-program-options-dev        \
                        libcgal-dev libcgal-qt5-dev         \
                        libdlib-dev libswscale-dev          \
                        libtbb-dev libqt5opengl5-dev        \
                        qt5-default qttools5-dev            \
                        qttools5-dev-tools libqt5svg5-dev   \
                        libproj-dev libdlib-dev             &&\
    apt-get clean

RUN git clone --branch v2.10.2 --single-branch --recursive \
        https://github.com/CloudCompare/CloudCompare.git

ADD build /CloudCompare/build
RUN cd /CloudCompare/build  &&\
    ./configure.sh          &&\
    make                    &&\
    make install            &&\
    make clean
        
# Add our special entrypoint
#
RUN git clone -b stable https://github.com/chbrandt/docker_entrypoint.git && \
    ln -sf docker_entrypoint/entrypoint.sh /.
#
ENTRYPOINT ["/entrypoint.sh"]

ENV EXECAPP "CloudCompare"

