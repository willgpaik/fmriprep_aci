BootStrap: shub
From: willgpaik/fmriprep_aci:fmriprep

%setup

%files

%environment 
    export QT_BASE_DIR="/opt/qt512"
    export QTDIR=$QT_BASE_DIR
    export PATH=$QT_BASE_DIR/bin:$PATH:
    export LD_LIBRARY_PATH=$QT_BASE_DIR/lib/x86_64-linux-gnu:$QT_BASE_DIR/lib:$LD_LIBRARY_PATH
    export PKG_CONFIG_PATH=$QT_BASE_DIR/lib/pkgconfig:$PKG_CONFIG_PATH
    
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
        subversion \
        
    apt-get clean
    
    export QT_BASE_DIR="/opt/qt512"
    export QTDIR=$QT_BASE_DIR
    export PATH=$QT_BASE_DIR/bin:$PATH:
    export LD_LIBRARY_PATH=$QT_BASE_DIR/lib/x86_64-linux-gnu:$QT_BASE_DIR/lib:$LD_LIBRARY_PATH
    export PKG_CONFIG_PATH=$QT_BASE_DIR/lib/pkgconfig:$PKG_CONFIG_PATH
    
    # Install DSI Studio and MRtrix3
    mkdir -p /opt/sw/
    cd /opt/
    wget https://raw.githubusercontent.com/willgpaik/qt5_aci/master/dsistudio_mrtrix3_install.sh
    chmod +x dsistudio_mrtrix3_install.sh
    ./dsistudio_mrtrix3_install.sh
    
    rm dsistudio_mrtrix3_install.sh
    
    # Install VirtualGL
    cd /opt
    wget https://sourceforge.net/projects/virtualgl/files/2.6.4/virtualgl_2.6.4_amd64.deb
    wget https://sourceforge.net/projects/virtualgl/files/2.6.4/virtualgl32_2.6.4_amd64.deb
    dpkg -i virtualgl*.deb
    rm virtualgl*.deb


