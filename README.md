# Supported tags and respective ```Dockerfile``` links
* (Triest) *[```2.1```, (2.1/Dockerfile)][]*
* (2.0-0) *[```2.0```, (2.0/Dockerfile)][]*

# GEOtop

GEOtop is a distributed hydrological model. It numerically integrates mass and energy balances of the hydrological cycle. GEOtop is mainly used for continuum simulations in small catchments. GEOtop treats the topographical effects as a variable of the interaction between energy balance and hydrological cycle and solves it with unique solutions.

> [www.geotop.org][]

![GEOtop logo](https://raw.githubusercontent.com/GrowWorkingHard/logos/master/geotop/GEOtop_200x250.jpg) 

# How to use this image?

This image packages the GEOtop model executable and depending libraries, such as ```libboost``` and ```meteoio```. Its availability makes downloading GEOtop sources and building/linking them on a local box obsolete. Since the *same* image runs on all platforms, using the *same* model binary and libraries, producing the *same* output, thus representing a big step towards better reproducibility of GEOtop runs.

Follow these steps to set up Docker for GEOtop. 

## 1. Install Docker

Installing Docker is first required to run this (and any ohther) image. Docker works on most operating systems (Windows, Mac OS X, GNU/Linux) and cloud platforms (AWS, Google).


Install Docker and follow the instructions for your platform:

* [GNU/Linux][] (choose your distribution)
* [Mac OS X][]
* [Windows][] 


## 2. Download the [small_example][] dataset

If you have never used GEOtop before, please the [small_example][] dataset and unpack it. 

```$ tar xzvf small_example.tar.gz```

This small data helps exercising a GEOtop run. More data sets can be found for various geographical regions at [geotop_examples][] or in the [tests folder][] of the main GEOtop repository.


## 3. Run GEOtop

To run GEOtop, open a terminal and change into the [small_example][] folder.


```$ cd small_example```

Copy and paste the following command. This should work on all platforms. 

```$ docker run --rm -v $(pwd):/work omslab/geotop```

Options:

* ```run``` will download the image and executes it afterwards.
* ```--rm``` will remove the container when the model is finished.
* ```-v $(pwd):/work``` maps the current folder as the internal data folder 
  for GEOtop.
* ```omslab/geotop```: this is the image name ```<organization_name>/<image_name>```
  to run.

The command above will automatically download the **latest** Docker image of GEOtop from DockerHub (the download is required just for the very first time) and run it. Next time you invoke the ```run``` command, GEOtop will just simply start on your machine.


To run a specific version of GEOtop, just add ```:<tag>``` to the image name.

```$ docker run --rm -v $(pwd):/work omslab/geotop:2.1```


## Output

The following output shows the final part of a GEOtop run:


```
$ docker run --rm -v $(pwd):/work omslab/geotop
 ...
 ... 
[NOTICE]: Close files
[NOTICE]: Deallocating global variables
[NOTICE]: Deallocating soil
[NOTICE]: Deallocating top
[NOTICE]: Deallocating land
[NOTICE]: Deallocating water
[NOTICE]: Deallocating channel network
[NOTICE]: Deallocating UV
[NOTICE]: Deallocating egy
[NOTICE]: Deallocating snow
[NOTICE]: Deallocating glacier
[NOTICE]: Deallocating met
[NOTICE]: Deallocating times
[NOTICE]: Deallocating par
[NOTICE]: Deallocating novalues
[NOTICE]: End of simulation!
$ _
```

# Supported Docker versions

This image is officially supported on Docker version 1.13.0.

Support for older versions (down to 1.6) is provided on a best-effort basis. Please see [the Docker installation documentation][] for details on how to upgrade your Docker daemon.


# Summary

Following a summary of the steps to take for installing and running GEOtop.

1. Install [Docker][]:
   [GNU/Linux][], [Mac OS X][], [Windows][] 
2. Download and unpack the [small_example][] dataset:
   ```$ tar xzvf small_example.tar.gz```
3. Open a terminal and change into the [small_example][] directory:
   ```$ cd small_example```
4. Run the GEOtop Docker image:
   ```$ docker run --rm  -v $(pwd):/work omslab/geotop```


# Feedback

If you have any problems with or questions about this image, please contact us through the [GitHub GEOtop Docker issue][]. If the issue is related to the model, please contact the GEOtop community through the [GitHub GEOtop issue][] or the [GEOtopUsers mailing list][].

# Known Issues

* The Docker GEOtop image runs as the ```root``` user, thus the output files have root ownership. However, you can always open and read them without any problem;
* To stop GEOtop mid-run, use the ```docker stop``` or ```docker kill``` command.
* GEOtop runs from within the container. This is the reason why the screen output shows ```/work/<file or folder>``` instead of your current path.
* On certain Linux distributions (e.g. Ubuntu) you have to either run docker via ```sudo docker run ...``` or you configure the ```sudoers``` file for Docker. 

## Bibliography

Endrizzi S., Gruber S., Dall’Amico M., Rigon R., [GEOtop 2.0: Simulating the combined energy and water balance at and below the land surface accounting for soil freezing, snow cover and terrain effects][], Geosci. Model Dev., 2014

Rigon, R., Bertoldi, G., & Over, T. M. (2006), [GEOtop: A Distributed Hydrological Model with Coupled Water and Energy Budgets][], Journal of Hydrometeorology, 7, 371–388.

[```2.1```, (2.1/Dockerfile)]: https://github.com/geotopmodel/docker/blob/master/2.1/Dockerfile
[www.geotop.org]: http://geotopmodel.github.io/geotop/
[GNU/Linux]: https://docs.docker.com/engine/installation/
[Mac OS X]: https://docs.docker.com/docker-for-mac/
[Windows]: https://docs.docker.com/docker-for-windows/
[small_example]: https://github.com/geotopmodel/docker/blob/master/small_example.tar.gz?raw=true
[geotop_examples]: https://github.com/geotopmodel/geotop_examples
[tests folder]: https://github.com/geotopmodel/geotop/tree/master/tests
[Docker]: https://www.docker.com/
[the Docker installation documentation]: https://docs.docker.com/engine/installation/
[GitHub GEOtop Docker issue]: https://github.com/geotopmodel/docker/issues
[GitHub GEOtop issue]: https://github.com/geotopmodel/geotop/issues
[GEOtopUsers mailing list]: https://groups.google.com/forum/#!forum/geotopusers
[GEOtop 2.0: Simulating the combined energy and water balance at and below the land surface accounting for soil freezing, snow cover and terrain effects]: http://www.geosci-model-dev.net/7/2831/2014/gmd-7-2831-2014.html
[GEOtop: A Distributed Hydrological Model with Coupled Water and Energy Budgets]: https://dl.dropboxusercontent.com/u/4762277/000-me/J24-GEOtop.pdf
