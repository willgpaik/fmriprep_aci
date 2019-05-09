BootStrap: docker
From: poldracklab/fmriprep:latest

%setup

%files

%environment 
    PATH="$PATH:/opt/sw/dsistudio/build/:/opt/sw/mrtrix3/bin/"
    export PATH
    LD_PRELOAD="/opt/eod/lib/libopentextdlfaker.so.3:/opt/eod/lib/libopentextglfaker.so.3 \
        :/opt/eod/lib64/libopentextdlfaker.so.3:/opt/eod/lib64/libopentextglfaker.so.3"
    export LD_PRELOAD

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
        libqt5svg5* \
        zlib1g \
        zlib1g-dev \
        libqt5opengl5-dev \
        libeigen3-dev \
        vim \
        nano
    apt-get clean
    
    # Install DSI Studio and MRtrix3
    mkdir -p /opt/sw/
    cd /opt/
    wget https://raw.githubusercontent.com/willgpaik/qt5_aci/master/dsistudio_mrtrix3_install.sh
    chmod +x dsistudio_mrtrix3_install.sh
    ./dsistudio_mrtrix3_install.sh
    
    rm dsistudio_mrtrix3_install.sh
    
    # Download requires libraries for EoD:
    cd /opt/
    svn export https://github.com/willgpaik/MorphoGraphX_aci.git/trunk/eod_graphics_libraries
    mv eod_graphics_libraries eod
    
    # Link directories
    mkdir -p /storage/home
    mkdir -p /storage/work
    mkdir -p /gpfs/scratch
    mkdir -p /gpfs/group
    mkdir -p /var/spool/torque



