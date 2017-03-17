FROM ruby:2.4
LABEL maintainer Sergio Lindo Mansilla <slindomansilla@suse.com>
LABEL version=0.1

# install necessary packages
RUN apt-get update
RUN apt-get -y install build-essential
RUN apt-get -y install gcc
RUN apt-get -y install less
RUN apt-get -y install make
RUN apt-get -y install tcl
RUN apt-get -y install tree
RUN apt-get -y install vim
RUN apt-get -y install zip

# install redis
WORKDIR /tmp
ENV DOCKER_REDIS_VERSION redis-3.2.8
RUN curl -O http://download.redis.io/releases/${DOCKER_REDIS_VERSION}.tar.gz
RUN tar xzvf ${DOCKER_REDIS_VERSION}.tar.gz
WORKDIR /tmp/${DOCKER_REDIS_VERSION}
RUN make
RUN make test
RUN make install
RUN utils/install_server.sh
RUN service redis_6379 start

# install HiGecko
WORKDIR /tmp
ENV DOCKER_HIGECKO_VERSION HiGecko-dockerfile_0.1
ADD ${DOCKER_HIGECKO_VERSION}.zip /tmp/${DOCKER_HIGECKO_VERSION}.zip
RUN unzip ${DOCKER_HIGECKO_VERSION}.zip
RUN mv ${DOCKER_HIGECKO_VERSION} HiGecko
WORKDIR /tmp/HiGecko
RUN bundle env
RUN bundle install
RUN rake db:setup

EXPOSE 3000
CMD rails s -b 0.0.0.0 > /tmp/higecko_rails_s.log 2> /tmp/higecko_rails_s.error
