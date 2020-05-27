FROM ubuntu:18.04

RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt install -y git cmake libboost-all-dev build-essential cmake unzip pkg-config
RUN DEBIAN_FRONTEND=noninteractive apt install -y libtbb-dev libgdal-dev qtbase5-dev doxygen texlive
RUN DEBIAN_FRONTEND=noninteractive apt install -y libjpeg-dev libpng-dev libtiff-dev software-properties-common wget
RUN add-apt-repository "deb http://security.ubuntu.com/ubuntu xenial-security main"
RUN apt update
RUN apt install -y libjasper1 libjasper-dev
RUN apt install -y libavcodec-dev libavformat-dev libswscale-dev libv4l-dev
RUN apt install -y libxvidcore-dev libx264-dev
RUN apt install -y python3-pip
RUN wget -O /tmp/opencv.zip https://github.com/opencv/opencv/archive/4.3.0.zip
RUN wget -O /tmp/opencv_contrib.zip https://github.com/opencv/opencv_contrib/archive/4.3.0.zip
RUN cd /tmp && unzip opencv.zip && unzip opencv_contrib.zip
RUN pip3 install numpy
RUN  cd /tmp/opencv-4.3.0/ && mkdir build && cd build && cmake -D OPENCV_EXTRA_MODULES_PATH=/tmp/opencv_contrib-4.3.0/modules -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr -D WITH_CUDA=OFF -D INSTALL_PYTHON_EXAMPLES=ON -D OPENCV_ENABLE_NONFREE=ON  -D BUILD_EXAMPLES=ON ..
RUN cd /tmp/opencv-4.3.0/build && make -j4
RUN cd /tmp/opencv-4.3.0/build && make install
RUN cd /tmp && git clone https://github.com/gerbilvis/gerbil.git && cd gerbil && ./configure.sh /usr && make