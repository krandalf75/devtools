
FROM oraclelinux:9

RUN yum -y groupinstall 'Development Tools'
RUN yum -y install wget sudo cmake

RUN useradd -ms /bin/bash conan \
    && printf "conan:conan" | chpasswd \
    && printf "conan ALL= NOPASSWD: ALL\\n" >> /etc/sudoers \
    && usermod -aG wheel conan


USER conan
WORKDIR /home/conan

RUN mkdir -p /home/conan/.conan \
    && printf 'eval "$(pyvenv init -)"\n' >> ~/.bashrc \
    && printf 'eval "$(pyvenv virtualenv-init -)"\n' >> ~/.bashrc

