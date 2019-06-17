FROM lambci/lambda-base:build

WORKDIR /tmp
RUN curl -s https://ftp.postgresql.org/pub/source/v11.3/postgresql-11.3.tar.gz > postgresql-11.3.tar.gz
RUN tar xf postgresql-11.3.tar.gz

WORKDIR /tmp/postgresql-11.3
RUN ./configure
RUN gmake
RUN gmake install
