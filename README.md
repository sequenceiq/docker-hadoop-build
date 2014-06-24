docker-hadoop-build
===================

## Build Apache Hadoop on OSX

Often when we use Apache Hadoop and would like to change versions you'll have to rebuild the whole Hadoop, native libs, etc ... which takes 30+ minutes, and carries lots of dependencies (libraries, protobuf, etc - at a given version).

This Docker image contains a Hadoop 2.4 nativelibs build.

## Build the image 
docker build -t sequenceiq/hadoop-nativelibs .

## Run the container
docker run -it sequenceiq/hadoop-nativelibs /bin/bash

## Copy files from the container
docker cp ID_OF_THE_CONTAINER:/tmp/hadoop-2.4.0-src/hadoop-dist/target/hadoop-2.4.0/lib/native/ DESTINATION
