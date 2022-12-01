===============
Getting Started
===============

Implementation Notes
====================

This work graciously builds on a benchmark developed by Arbel-Raviv and Brown's
work (https://bitbucket.org/trbot86/implementations/src/master/cpp/range_queries/)
to provide linearizable range queries in linked data structures. We use their
codebase as a starting point and implement our technique on top of the existing
framework. The core of our bundling implementation is contained in the 'bundle'
directory, which implements the global structures as well as necessary functions
of bundling. The three data structures we implement are found in 'bundled_*'
directories. The scripts necessary to produce the plots found in our paper are
included under the 'microbench' directory.

Getting Started Guide
=====================

Requirements
------------

The experiments from the paper were executed on a 4-socket machine with Intel Xeon Platinum 8160 processors running Ubuntu 20.04. However, we also verified our results on a dual-socket machine with Intel Xeon E5-2630 v3 processors running Ubuntu 18.04. The C++11 libraries are requried to build and run the experiments, while the Python libraries are used for plotting results.

Unix Utilities::

  make (e.g., sudo apt install make)
  dos2unix (e.g., sudo apt install dos2unix)
  bc (e.g., sudo apt install bc)

C++ Libraries:::

  libnuma (e.g., sudo apt install libnuma-dev)
  libjemalloc (e.g., sudo apt install libjemalloc-dev)
  libpapi (e.g., sudo apt install libpapi-dev)

Python libraries:::

  python (v3.10)
  plotly (v5.1.0)
  psutil (v5.8.0)
  requests (v2.26.0)
  pandas (v1.3.4)
  absl-py (v0.13.0)

The above libraries can be installed with Miniconda, whose installation instructions can be found here (https://docs.conda.io/en/latest/miniconda.html). Generally speaking, you will download the appropriate installer for your machine, run the install script, and follow the prompts. After it is installed, use the following commands to prepare the environment needed for plotting output.::

  conda create -n paper63 python=3
  conda activate paper63
  conda install plotly psutil requests pandas absl-py

In order to reproduce our results, it is necessary to link against jemalloc. For convenience, our scripts assume that a symbolic link is available in the lib subdirectory. If you already have it installed on your system you can create a link to the shared library in lib so that the scripts can locate it. Otherwise, you can use the following command to install it in the previously configured conda environment and link it. Note that we assume the commands are run from the project's root directory.::

  conda install -c conda-forge jemalloc
  ln -s $(conda info --base)/envs/paper63/lib/libjemalloc.so ./lib/libjemalloc.so

Docker. As a convenience, we also include a Dockerfile that will handle all of the setup steps outlined above. Note that running in a Docker container may inhibit performance, so we advise running on bare metal if you wish to reproduce our results. The Dockerfile can be used as a guide when doing so. Please see the comments in the Dockerfile for more detailed information. Once Docker is installed on your machine following the instructions here (https://docs.docker.com/engine/install/), you can build and run the container in the background by running the following commands from the root directory, where the Dockerfile is located.::

  docker build -t bundledrefs .
  docker run -d -p 8022:22 bundledrefs

After, you can ssh into the container using::

  ssh -p 8022 bundledrefs@localhost

and provide the password bundledrefs. From there, you will be able to follow the rest of this README as usual.
