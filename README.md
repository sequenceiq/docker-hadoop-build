docker-hadoop-build
===================

## Build Apache Hadoop
Often when we use Apache Hadoop and would like to make a custom build (stock or forked) you'll have to 
rebuild the whole Hadoop, native libs, etc ... which takes 30+ minutes, and carries lots of dependencies
(libraries, protobuf, etc - at a given version).

This Docker image contains the build process of Hadoop 2.7.0 nativelibs. Also the 64b version of `nativelibs`
is released at our [RPM repository](http://dl.bintray.com/sequenceiq/sequenceiq-bin/hadoop-native-64-2.7.0.tar).

## Build the image
```
docker build -t sequenceiq/hadoop-nativelibs .
```

## Release libs to bintray

Steps needed:
- Copy the tarred libs from docker container
- Create a new version on bintray
- Upload the tarred libs to bintray

```
docker run --rm  sequenceiq/hadoop-nativelibs > hadoop-native-64-2.7.0.tar
curl -Lo /tmp/bintray-functions j.mp/bintray-functions && . /tmp/bintray-functions
bint-upload-with-version sequenceiq sequenceiq-bin hadoop-native-64bit 2.7.0 hadoop-native-64-2.7.0.tar
```

## TODO

create a Makefile to fully automate the release
