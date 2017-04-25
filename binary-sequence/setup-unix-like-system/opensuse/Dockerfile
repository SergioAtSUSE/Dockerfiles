FROM opensuse:42.2
LABEL version="0.2"
LABEL maintainer "sergiolindo.empresa@gmail.com"

RUN zypper ref
RUN zypper in -y git
RUN mkdir /home/github/
WORKDIR /home/github
#RUN git clone https://github.com/binary-sequence/setup-unix-like-system.git
RUN git clone https://github.com/SergioAtSUSE/setup-unix-like-system.git
WORKDIR /home/github/setup-unix-like-system/
RUN git fetch --all --tags --prune
RUN git checkout -b v0.1 tags/v0.1
RUN bash src/opensuse/install_packages.sh
RUN mkdir -p /home/user/.config
RUN source src/opensuse/install_config.sh

WORKDIR /home/user
CMD ["bash"]
