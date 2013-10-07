---
layout: post
title: Installing PyCUDA on Ubuntu via pip
categories:
- python
- cuda
- gpu
- articles
- sysadmin
---

I'm currently configuring an Ubuntu server with an [NVidia Tesla](http://www.nvidia.com/object/tesla-supercomputing-solutions.html) GPU unit.

In the interest of actually getting things done with it, we are going to try out the [PyCUDA][1] library.

The [PyCUDA Installation Docs][3] for Linux don't refer to installation via pip, but I wanted to give it a try. It mostly went without a hitch, except for a couple of things.

You'll need to make sure that the cuda `bin` directory is on the system path.

    export PATH=/usr/local/cuda/bin:$PATH

Then you'll need to install numpy, which also requires having Python's dev package installed.

    sudo apt-get install python-dev
    pip install numpy

At this point, if you run

    pip install pycuda

You will get an error:

    In file included from src/cpp/cuda.cpp:1:0:
    
    src/cpp/cuda.hpp:12:18: fatal error: cuda.h: No such file or directory
    
    compilation terminated.

This had me confounded, partially due to pycuda's frequent exhortations in the install logging to run the configure script and Ctrl-C if certain things weren't what I wanted, etc. But most of the warnings were moot, since pip removes the build directory if you cancel the install (I'm sure there's some way around this), blocking manual access to the configure script, and there did not seem to be a way to pass configure flags through pip (would also love to learn if you can do this). But then I found this little gem at the beginning of the [Ubuntu-flavored install docs][4]:

> You'll need $CUDA_ROOT set to the root of the CUDA install directory

Set CUDA_ROOT and you should be good to go!

    export CUDA_ROOT=/usr/local/cuda

[1]: http://mathema.tician.de/software/pycuda
[3]: http://wiki.tiker.net/PyCuda/Installation/Linux 
[4]: http://wiki.tiker.net/PyCuda/Installation/Linux/Ubuntu

