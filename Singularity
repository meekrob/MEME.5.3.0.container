BootStrap: docker
From: ubuntu:16.04

%post

    # install some system deps
    apt-get -y update
    apt-get -y install locales curl bzip2 less unzip git wget vim ant default-jdk
    # this is a X11 dep
    apt-get -y install libxext6
    # tools to open PDF and HTML files
    apt-get -y install firefox xpdf
    # some extra devel libs
    apt-get -y install zlib1g-dev libssl-dev libpng-dev uuid-dev
    # other
    locale-gen en_US.UTF-8
    apt-get clean

    # download and install miniconda3.7, 3.8 is the latest and seems to cause a conflict
    curl -sSL -O https://repo.anaconda.com/miniconda/Miniconda3-py37_4.8.3-Linux-x86_64.sh
    bash Miniconda3-py37_4.8.3-Linux-x86_64.sh -p /opt/miniconda3 -b
    rm -fr Miniconda3-py37_4.8.3-Linux-x86_64.sh
    export PATH=/opt/miniconda3/bin:$PATH
    conda update -n base conda
    conda config --add channels conda-forge
    conda config --add channels bioconda

    # install some dependencies to build R packages
    apt-get -y install build-essential gfortran

    conda install meme=5.3.0

%environment
    export LANG=en_US.UTF-8
    export LANGUAGE=en_US:en
    export LC_ALL=en_US.UTF-8
    export PATH=/opt/miniconda3/bin:$PATH
    export OMPI_MCA_opal_cuda_support=true
