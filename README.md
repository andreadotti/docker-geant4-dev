Create docker image with Geant4 SDK
=================================================

Author: Andrea Dotti (adotti@slac.stanford.edu)  
Copyright: Andrea Dotti (adotti@slac.stanford.edu) and   
           the Geant4 Collaboration <http://www.geant4.org>  
License: Geant4 License <http://www.geant4.org/geant4/license/LICENSE.html>  

The following repository contains scripts to 
create a docker image with the Geant4 libraries and development 
environment. The image can then be used to create containers
that can compile and run a Geant4 application.

Usage:
------
Assuming Geant4 source code and Geant4 DB are installed on the host
respectively under */geant4-src* and */geant4-data*

```
$ git clone https://github.com/andreadotti/docker-geant4-dev
$ cd docker-geant4-dev
$ ./build-binaries.sh /geant4-src /geant4-data
$ docker build -t geant4-env .
```

The Geant4 binaries can be found in the tarball under binaries.
You may want to adapt the *buildme.sh* script to your particular
configuration.

To test the new image:
```
$ docker run --rm -t -i -v "/geant4-data:/usr/local/geant4/data:ro" \
	geant4-env geant4-config --version
```  


