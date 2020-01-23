FROM lambci/lambda:build-nodejs12.x

# Copied from the Dockerfile for lambci/lambda:build-nodejs12.x
# https://github.com/lambci/docker-lambda/blob/master/nodejs12.x/build/Dockerfile
# We re-run so we can get the latest node, which the published build image doesn't have for some reason
RUN rm -rf /var/runtime /var/lang /var/rapid && \
    curl https://lambci.s3.amazonaws.com/fs/nodejs12.x.tgz | tar -zx -C /

# Setup to use "app" user, do everything in /opt/app
ENV APPUSER=app
ENV APPDIR=/opt/app

# Install yarn
RUN curl --silent --location https://rpm.nodesource.com/setup_12.x | bash -
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

# Make sure ~/.aws dir is owend by app user
RUN mkdir -p /home/app/.aws && chown app:app /home/app/.aws

USER $APPUSER
WORKDIR $APPDIR
