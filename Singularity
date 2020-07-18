BootStrap: shub
From: willgpaik/fmriprep_aci:fmriprep

%setup

%files

%environment 
    PATH="$PATH:/opt/sw/dsistudio/build/:/opt/sw/mrtrix3/bin/"
    export PATH
    export EIGEN_CFLAGS=/usr/include/eigen3

%runscript

%post
    # Ubuntu DSI Studio installation guide: http://www.nemotos.net/?p=1878

    apt-get update
    apt-get install -y --no-install-recommends \
        wget \
        zip \
        unzip \
        libboost-all-dev \
        qt5-qmake \
        qt5-default \
        libqt5opengl5-dev \
        libqt5svg5* \
        zlib1g \
        zlib1g-dev \
        libeigen3-dev \
        vim \
        nano \
        subversion
    apt-get clean
    
    # Install DSI Studio and MRtrix3
    mkdir -p /opt/sw/
    cd /opt/
    wget https://raw.githubusercontent.com/willgpaik/qt5_aci/master/dsistudio_mrtrix3_install.sh
    chmod +x dsistudio_mrtrix3_install.sh
    ./dsistudio_mrtrix3_install.sh
    
    rm dsistudio_mrtrix3_install.sh
    
    # Link directories
    mkdir -p /storage/home
    mkdir -p /storage/work
    mkdir -p /gpfs/scratch
    mkdir -p /gpfs/group
    mkdir -p /var/spool/torque



