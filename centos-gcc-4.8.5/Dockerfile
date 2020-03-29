FROM centos:7

RUN yum -y groupinstall 'Development Tools'
RUN yum -y install wget nasm python3

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
    && printf "conan ALL= NOPASSWD: ALL\\n" >> /etc/sudoers 
	

USER conan
WORKDIR /home/conan

RUN mkdir -p /home/conan/.conan \
    && printf 'eval "$(pyenv init -)"\n' >> ~/.bashrc \
    && printf 'eval "$(pyenv virtualenv-init -)"\n' >> ~/.bashrc
