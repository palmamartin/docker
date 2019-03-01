FROM debian:jessie-slim
RUN apt-get -y update && \
    apt-get install -y build-essential \
    	git \
	cmake
RUN git clone https://github.com/geotopmodel/geotop.git /usr/src/geotop
WORKDIR /usr/src/geotop
RUN git checkout -b v3.0 origin/v3.0
RUN mkdir cmake-build
WORKDIR /usr/src/geotop/cmake-build
RUN cmake -DCMAKE_EXE_LINKER_FLAGS="-static" ..
RUN make

FROM scratch
COPY --from=0 /usr/src/geotop/cmake-build/geotop .
ENTRYPOINT ["/geotop"]
