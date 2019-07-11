FROM lambci/lambda-base:build

ENV JQ_VERSION='1.5'

RUN curl -sL https://raw.githubusercontent.com/stedolan/jq/master/sig/jq-release.key > /tmp/jq-release.key
RUN curl -sL https://raw.githubusercontent.com/stedolan/jq/master/sig/v${JQ_VERSION}/jq-linux64.asc > /tmp/jq-linux64.asc
RUN curl -sL https://github.com/stedolan/jq/releases/download/jq-${JQ_VERSION}/jq-linux64 > /tmp/jq-linux64
RUN gpg --import /tmp/jq-release.key
RUN gpg --verify /tmp/jq-linux64.asc /tmp/jq-linux64
RUN cp /tmp/jq-linux64 /usr/bin/jq
RUN chmod +x /usr/bin/jq
RUN rm -f /tmp/jq-release.key /tmp/jq-linux64.asc /tmp/jq-linux64
