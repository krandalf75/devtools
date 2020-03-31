FROM centos:7

RUN yum -y groupinstall 'Development Tools'
RUN yum -y install wget nasm python3 java-1.8.0-openjdk java-1.8.0-openjdk-devel sudo 

RUN wget -q --no-check-certificate https://cmake.org/files/v3.16/cmake-3.16.1-Linux-x86_64.tar.gz \
    && tar -xzf cmake-3.16.1-Linux-x86_64.tar.gz \
       --exclude=bin/cmake-gui \
       --exclude=doc/cmake \
       --exclude=share/cmake-3.12/Help \
    && cp -fR cmake-3.16.1-Linux-x86_64/* /usr \
    && rm -rf cmake-3.16.1-Linux-x86_64 \
    && rm cmake-3.16.1-Linux-x86_64.tar.gz
	

RUN useradd -ms /bin/bash conan \
    && printf "conan:conan" | chpasswd \
    && printf "conan ALL= NOPASSWD: ALL\\n" >> /etc/sudoers \
    && usermod -aG wheel conan
	

USER conan
WORKDIR /home/conan

RUN mkdir -p /home/conan/.conan \
    && printf 'eval "$(pyvenv init -)"\n' >> ~/.bashrc \
    && printf 'eval "$(pyvenv virtualenv-init -)"\n' >> ~/.bashrc
