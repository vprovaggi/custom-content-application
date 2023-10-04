# Dockerfile v 0.3
# default Node version
ARG NODE_VERSION=14-bullseye

FROM node:${NODE_VERSION}
# default values
ARG ANGULAR_VERSION=14.1.3
ARG NX_VERSION=14.2.1

# needed to update to a version of git >2.34 for SSH sign commits
RUN echo "deb http://deb.debian.org/debian bullseye-backports main" >> /etc/apt/sources.list.d/bullseye-backports.list \
&& apt-get update \
&& apt-get -t bullseye-backports install git -y
RUN apt-get install gnupg2 -y

USER node

# resolve the npm EACCESS problem : https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally
ENV NPM_CONFIG_PREFIX=~/.npm-global

RUN mkdir ~/.npm-global \
    && npm config set prefix '~/.npm-global'

RUN npm i -g @angular/cli@${ANGULAR_VERSION} \
    && npm install -g nx@${NX_VERSION}
