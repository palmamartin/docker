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
        && wget https://github.com/geotopmodel/geotop/archive/TRIEST_release.tar.gz \
        && tar xvf TRIEST_release.tar.gz \
        # build and install GEOtop 2.0
        && ( \
            cd geotop-TRIEST_release \
            && cmake -DBUILD_STATIC:BOOL=OFF \
                     -DCMAKE_BUILD_TYPE="minsizerel" \
                     -DCMAKE_INSTALL_PREFIX="/usr" \
                     -DENABLE_INTERNAL_METEODISTR:BOOL=ON \
                     -DMETEOIO_OUTPUT:BOOL=OFF \
                     -DMETEOIO_PATH="/usr" \
                     -DVERBOSE:BOOL=OFF \
                     -DVERY_VERBOSE=OFF \
                     -DCMAKE_CXX_FLAGS_RELEASE="-Wextra -Wall -O2 -Wno-unused-parameter \
                        -Wno-unused-function -Wno-unused-result \
                        -Wno-unused-but-set-variable" . \
            && make -j4 install \
            ) \
        \
        # clean up donwloaded packages and installation folders
        && rm -rf meteoio \
                  geotop-TRIEST_release \
                  MeteoIO-2.5.1-src.tar.gz \
                  TRIEST_release.tar.gz \
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
        && apt-get -y autoremove --purge \
        \
        # install only required libraries without API
        && apt-get install --no-install-recommends -y \
            libboost-regex1.55.0 \
            libboost-program-options1.55.0 \
            libboost-filesystem1.55.0 \
            libboost-system1.55.0 \
            libboost-iostreams1.55.0 

RUN mkdir /work
CMD ["/usr/bin/geotop", "/work" ]
