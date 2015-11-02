FROM ubuntu:14.04
MAINTAINER Hans Christian v. Stockhausen <hc@vst.io>

RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

RUN apt-get install -y wget git
RUN wget https://packages.erlang-solutions.com/erlang-solutions_1.0_all.deb && \
    dpkg -i erlang-solutions_1.0_all.deb && \
    rm erlang-solutions_1.0_all.deb && \
    apt-get update && \
    apt-get -y install elixir
RUN groupadd elixir && useradd -g elixir -G sudo elixir
USER elixir
WORKDIR /home/elixir
CMD ["iex"]
