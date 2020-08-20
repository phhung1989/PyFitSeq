#Bootstrap: shub
#From: phhung1989/PyFitSeq

Bootstrap: docker
From: ubuntu:20.04
#Bootstrap: localimage
#From: ../ubuntu-2004/ubuntu.simg

%labels
MAINTAINER darachm

%help

    This should give you an environment to run FITseq.
    The runscript is just bash.
    Scripts are going to be in /usr/bin, and that's:

        - evo_simulator.py
        - pyfitseq.py

    Should be accessible immediately from the exec line, so something like this
    should do it:

        singularity exec fitseq_container.simg pyfitseq.py -h

%runscript

    bash

%environment

    export LANG="C.UTF-8"
    export LANG_ALL="C.UTF-8"
    export PATH=${PATH}:/PyFitSeq

%post

    export LANG="C.UTF-8"
    export LANG_ALL="C.UTF-8"
    export DEBIAN_FRONTEND="noninteractive"

    apt -y update
    apt -y install apt-utils git
    apt -y install python3 python3-pip
    #apt -y install gzip xz-utils bzip2 parallel gawk perl 
    
    git clone https://github.com/phhung1989/PyFitSeq.git /PyFitSeq

    python3 -m pip install -r /PyFitSeq/requirements.txt
    chmod a+x /PyFitSeq/evo_simulator.py /PyFitSeq/pyfitseq.py 

%test

    export PATH=${PATH}:/PyFitSeq
