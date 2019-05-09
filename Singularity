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
        libqt5opengl5-dev \
        libeigen3-dev \
        vim \
        nano
    apt-get clean
    
    # Qt5 Charts required:
    # Installation help found: https://forum.qt.io/topic/71581/problem-installing-qt-charts/8
    cd /tmp
    wget http://download.qt.io/official_releases/qt/5.12/5.12.3/single/qt-everywhere-src-5.12.3.tar.xz
    tar -xf qt-everywhere-src-5.12.3.tar.xz
    cd qt-everywhere-src-5.12.3
    ./configure -opensource -nomake tests -confirm-license -c++std c++11 -sqlite
    make && make install
    cd qt-everywhere-src-5.12.3/qtcharts
    make && make install
    cd /tmp
    rm qt-everywhere-src-5.12.3.tar.xz
    #rm -rf qt-everywhere-src-5.12.3
    
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



