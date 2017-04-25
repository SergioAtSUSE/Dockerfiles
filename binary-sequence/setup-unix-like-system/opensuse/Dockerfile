FROM opensuse:42.2
LABEL version="0.5"
LABEL maintainer "sergiolindo.empresa@gmail.com"

RUN zypper ref
RUN zypper in -y git
RUN mkdir /home/github/
WORKDIR /home/github
# RUN git clone https://github.com/binary-sequence/setup-unix-like-system.git
RUN git clone https://github.com/SergioAtSUSE/setup-unix-like-system.git
WORKDIR /home/github/setup-unix-like-system/
RUN git fetch --all --tags --prune
RUN git checkout -b v0.5 tags/v0.5
RUN ["bash", "src/opensuse/install_packages.sh"]
RUN mkdir -p /home/root/.config
RUN ["bash", "src/opensuse/install_config.sh"]
RUN source /home/root/.alias

WORKDIR /
CMD ["bash"]
