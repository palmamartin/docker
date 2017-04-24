# Dockerfile for version Geotop version 2.0
# To be used and run just for reference 
# 
# 

FROM debian:jessie-slim

MAINTAINER Francesco Serafin <francesco.serafin.3@gmail.com>, Olaf David <odavid@colostate.edu> Stefano Cozzini <stefano.cozzini.exact-lab.it>

RUN set -x \
        \
        && apt-get -y update \
        \
        # installation of required packages
        && apt-get install --no-install-recommends -y \
            ca-certificates \
            wget \
            binutils \
            make \
            cmake \
            g++ \
            gcc \
            git \
        \
        # download and unpack GEOtop 2.0
        && git clone https://github.com/se27xx/GEOtop \
        # build and install GEOtop 2.0
        && ( \
            cd GEOtop \
            && mkdir bin \
            && make -f geotop.make \
            ) \
        \
        # purge obsolete packages
        && apt-get -y remove --purge \
            ca-certificates \
            wget \
            binutils \
            make \
            cmake \
            g++ \
            gcc \
        \
        # purge not needed packages
        && apt-get -y autoremove --purge

RUN mkdir /work
CMD ["/GEOtop/bin/geotop-2.0.0", "/work" ]
