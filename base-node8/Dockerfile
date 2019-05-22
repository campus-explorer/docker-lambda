FROM lambci/lambda:build-nodejs8.10

# Setup to use "app" user, do everything in /opt/app
ENV APPUSER=app
ENV APPDIR=/opt/app

# Install yarn
RUN curl --silent --location https://dl.yarnpkg.com/rpm/yarn.repo | \
    tee /etc/yum.repos.d/yarn.repo \
    && yum -y install yarn

# Setup app user
RUN useradd --system -U $APPUSER \
    && mkdir $APPDIR \
    && mkdir $APPDIR/node_modules \
    && chown -R $APPUSER:$APPUSER $APPDIR \
    && mkdir -p /home/app \
    && chown -R $APPUSER:$APPUSER /home/app
USER $APPUSER
WORKDIR $APPDIR
