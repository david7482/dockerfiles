# Codecvisa 
# A real-time video analyzer for H.265/HEVC, H.264/AVC/MVC, GOOGLE VP9/VP8 and YUV video codecs
#
# To build:
# docker build -t codecvisa .
#
# To run:
# docker run -d \
#       -v /tmp:/tmp
#       -v /etc/localtime:/etc/localtime:ro \
#       -v /tmp/.X11-unix:/tmp/.X11-unix \
#       -e DISPLAY=unix$DISPLAY \
#       --name codecvisa \
#       codecvisa

FROM ubuntu:16.04

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        libqtgui4 \
        wget \
        && rm -rf /var/lib/apt/lists/*

RUN cd /tmp && \
    wget http://www.codecian.com/downloads/codecvisa.tar.gz && \
    tar -xvzf codecvisa.tar.gz && \
    mv codecvisa/* /usr/bin/ && \
    rm -rf codecvisa*

ENV HOME /home/codecvisa
RUN useradd --create-home --home-dir $HOME codecvisa && \
    chown -R codecvisa:codecvisa $HOME

WORKDIR $HOME
USER codecvisa

ENTRYPOINT [ "codecvisa" ]
