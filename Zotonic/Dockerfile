FROM hcvst/erlang

MAINTAINER Hans Christian v. Stockhausen, hc@vst.io

# http://zotonic.com/docs/0.9/tutorials

# Install Dependencies
RUN apt-get update
RUN apt-get install -y build-essential
RUN apt-get install -y imagemagick
RUN apt-get install -y postgresql

# Enable trust-authentication in PostgreSQL
RUN echo "                                    " >>/etc/postgresql/9.1/main/pg_hba.conf
RUN echo "# Zotonic settings                  " >>/etc/postgresql/9.1/main/pg_hba.conf
RUN echo "local all zotonic              ident" >>/etc/postgresql/9.1/main/pg_hba.conf
RUN echo "host  all zotonic 127.0.0.1/32 md5  " >>/etc/postgresql/9.1/main/pg_hba.conf
RUN echo "host  all zotonic ::1/128      md5  " >>/etc/postgresql/9.1/main/pg_hba.conf
RUN service postgresql restart

# Install Zotonic 
RUN apt-get install -y python-software-properties
RUN add-apt-repository -y ppa:arjan-scherpenisse/zotonic
RUN apt-get update
RUN apt-get install -y zotonic
