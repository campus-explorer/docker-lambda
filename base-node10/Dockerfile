FROM lambci/lambda:build-nodejs10.x

# Setup to use "app" user, do everything in /opt/app
ENV APPUSER=app
ENV APPDIR=/opt/app

# Install yarn
RUN curl --silent --location https://rpm.nodesource.com/setup_8.x | bash -
RUN curl --silent --location https://dl.yarnpkg.com/rpm/yarn.repo | \
    tee /etc/yum.repos.d/yarn.repo \
    && yum -y install yarn

# Install jq
COPY --from=campusexplorer/jq:latest /usr/bin/jq /usr/bin/jq

# Setup app user
RUN useradd --system --uid 370 -U $APPUSER \
    && mkdir $APPDIR \
    && mkdir $APPDIR/node_modules \
    && chown -R $APPUSER:$APPUSER $APPDIR \
    && mkdir -p /home/app \
    && chown -R $APPUSER:$APPUSER /home/app
USER $APPUSER
WORKDIR $APPDIR
