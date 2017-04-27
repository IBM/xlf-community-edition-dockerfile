# XL Fortran for Linux, Community Edition

## Overview

This image contains the XL Fortran for Linux, Community Edition compiler, it's installation dependencies, and some common development tools (vim-tiny, make, autoconf, automake).

For the details how this image was built, see [xlf-community-edition-dockerfile](https://github.com/IBM/xlf-community-edition-dockerfile).
This image does not use docker hub automated builds because they are currently not available for the ppc64le architecture.

*Note:* Before installing additional packages using apt-get, update the package lists using 'apt-get update'. This image is currently based on the experimental [ppc64le/ubuntu](https://hub.docker.com/r/ppc64le/ubuntu/) images:
  
	FROM ppc64le/ubuntu:16.04


## Usage

To run this image interactively:  

	docker run -ti ppc64le/xlf-ce

The entrypoint is a script that will interactively display the license text and then configure the compiler.  
To automatically accept the license, add "-e LICENSE=accept" to your run command:  

	docker run -ti -e LICENSE=accept ppc64le/xlf-ce

You may also want to mount a directory that contains your source using -v. If your source is in /home/user/source, run:  

	docker run -ti -e LICENSE=accept -v /home/user/source:/source ppc64le/xlf-ce

Here is an example of compiling and running hello world in non-interactive mode:  

	docker run -e LICENSE=accept -v /home/user/source:/source --workdir /source ppc64le/xlf-ce bash -cx 'xlf -O3 hello.f -o hello && ./hello'  
    + xlf -O3 hello.f -o hello
    ** main   === End of Compilation 1 ===
    1501-510  Compilation successful for file hello.f.
    + ./hello
    Hello Fortran World!


## Documentation

Documentation can be found in the [XL Fortran for Linux documentation library](http://www.ibm.com/support/docview.wss?uid=swg27036672), product information can be found at [XL Fortran for Linux](http://www.ibm.com/software/products/en/xlfortran-linux/).


## Providing feedback

XL Fortran Community Edition is a no-charge product (unlimited license for production use) and does not include official IBM support.  
You can provide feedback at the [XL on POWER Community Edition forum](http://ibm.biz/xlfortran-linux-ce).


## Contributions

All contributions to [xlf-community-edition-dockerfile](https://github.com/IBM/xlf-community-edition-dockerfile) require a comment in the pull request to indicate you accept the terms in [DCO.1.1.txt](https://github.com/IBM/xlf-community-edition-dockerfile/blob/master/DCO.1.1.txt) (example below):  
DCO 1.1 Signed-off-by: Ray Kivisto rkivisto at ca.ibm.com


## License

The Dockerfile is licensed under [Apache License, Version 2.0](https://github.com/IBM/xlf-community-edition-dockerfile/blob/master/LICENSE).  
XL Fortran Community Edition is licensed under the [International License Agreement for Non-Warranted Programs](http://www14.software.ibm.com/cgi-bin/weblap/lap.pl?li_formnum=L-JYIP-AEMRZJ).