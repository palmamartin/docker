# Supported tags and respective ```Dockerfile``` links
* (Triest) [```2.1.0```, (2.1/Dockerfile)][]

# What is GEOtop?

GEOtop is a distributed model which numerically integrates mass and energy
balances of the hydrological cycle. It is mostly used for continuum simulations
in small catchments. GEOtop treats the topografical effects as a variable on the
interaction between energy balance and hydrological cycle. The whole problem is
solved with unique solutions.

> [www.geotop.org][]

![GEOtop logo](https://github.com/GrowWorkingHard/logos/blob/master/geotop/GEOtop_200x250.jpg "GEOtop logo")

# How to use this image

The containerized version of GEOtop runs on every machine (Windows, Mac OS X, GNU/Linux) and cloud
platforms (AWS, GOOGLE). To set up the working environment follow these simple
steps.

## Install Docker

Docker is required to run the containerized version of GEOtop. Install Docker
following the instructions, depending on your platform:

* [GNU/Linux][] (then choose your distribution)
* [Mac OS X][]
* [Windows][]

## Download the [small_example][] dataset

Running GEOtop is pretty easy, but if you have never set up the working
directory and the included dataset, please donwload the [small_example][]
dataset and unpack it. In this way you can quickly try how easy is to run GEOtop
now.

For further improvements, please consider to look into the [geotop_examples][]
repository or into the [tests folder][] into the main GEOtop repo.

## Run GEOtop

Running GEOtop on all platforms

```
$ cd <path>/<to>/small_example
$ docker run --rm  -v $(pwd):/work omslab/geotop:2.1
```

#Output

#Summary

# Supported Docker versions

# User Feedback

# Known Issues

## Bibliography

[```2.1.0```, (2.1/Dockerfile)]: https://github.com/geotopmodel/docker/blob/master/2.1/Dockerfile
[www.geotop.org]: http://geotopmodel.github.io/geotop/
[GNU/Linux]: https://docs.docker.com/engine/installation/
[Mac OS X]: https://docs.docker.com/docker-for-mac/
[Windows]: https://docs.docker.com/docker-for-windows/
[small_example]: https://github.com/geotopmodel/docker/blob/master/small_example.tar.gz?raw=true
[geotop_examples]: https://github.com/geotopmodel/geotop_examples
[tests folder]: https://github.com/geotopmodel/geotop/tree/master/tests
