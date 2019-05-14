# fmriprep_aci
Singularity recipe for fMRIPrep on Ubuntu 16.04 for ICS ACI clusters

This version contains:  
fMRIPrep, ANTs, DSI Studio, and MRtrix3  
(If you are looking for DSI Studio and MRtrix3 only version, please go to willgpaik/qt5_aci for more information)  
(If you are looking for fMRIPrep only version, please check https://github.com/ics-i-ask-center/fmriprep_icsaci)

2019/5/11  
Updated to Ubuntu 18.04 (Due to Qt5 dependencies issue -> look for Charts in link: http://www.nemotos.net/?p=1878)  
Separated **fMRIPrep build** and **DSI Studio + MRtrix3 build** (Due to build time limit of 2 hours)

2019/5/14  
Moved back to Ubuntu 16.04 (Kernel version issue on ACI clusters)  
Qt 5.12.3 is added to **fMRIPrep build**
