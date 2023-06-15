# Build Stage
FROM --platform=linux/amd64 ubuntu:20.04 as builder

## Install build dependencies.
RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y cmake clang

## Add source code to the build stage.
ADD . home/jfsil/libjpeg-turbo/fuzz
WORKDIR home/jfsil/libjpeg-turbo/fuzz

## TODO: ADD YOUR BUILD INSTRUCTIONS HERE.
RUN mkdir build
RUN cd build/
RUN export CC=clang
RUN export CXX=clang++
RUN pwd
RUN cmake ..
RUN make

# Package Stage
FROM --platform=linux/amd64 ubuntu:20.04

## TODO: Change <Path in Builder Stage>
COPY --from=builder /libjpeg-turbo/fuzz/build/fuzzme /

