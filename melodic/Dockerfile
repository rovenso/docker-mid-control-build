FROM ros:melodic-robot-bionic

RUN apt-get update && apt-get install -y \
    ccache \
    curl \
    unzip \
    udev \
    ros-melodic-serial \
    libsdl2-dev \
 && rm -rf /var/lib/apt/lists/* \
 && ccache --max-size=4G \
 && curl -o EPOSlib.zip https://www.maxongroup.com/medias/sys_master/root/8834320007198/EPOS-Linux-Library-En.zip \
 && unzip EPOSlib.zip \
 && rm EPOSlib.zip \
 && cd EPOS_Linux_Library \
 && chmod +x install.sh \
 && ./install.sh \
 && cd .. \ 
 && rm -r EPOS_Linux_Library \
 && . /opt/ros/melodic/setup.sh \
 && mkdir -p /workspace/src \
 && catkin_init_workspace /workspace/src \
 && cd /workspace \
 && catkin_make \
 && . /workspace/devel/setup.sh \
 && echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc \
 && echo "source /workspace/devel/setup.bash" >> ~/.bashrc

ENV PATH /usr/lib/ccache:$PATH
VOLUME /workspace/src
WORKDIR /workspace
