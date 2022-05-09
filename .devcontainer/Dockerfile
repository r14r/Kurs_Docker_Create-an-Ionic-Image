#------------------------------------------------------------------------------
# STAGE 1:
#------------------------------------------------------------------------------
FROM ubuntu:latest

ENV DEBIAN_FRONTEND noninteractive

# Configure Timezone
ENV TZ 'Europe/Berlin'

RUN echo $TZ > /etc/timezone 

RUN apt-get update                                     && \
    apt-get install -y tzdata                          && \
    rm /etc/localtime                                  && \
    ln -snf /usr/share/zoneinfo/$TZ /etc/localtime     && \
    dpkg-reconfigure -f noninteractive tzdata          && \
    apt-get clean

#
RUN apt-get install --yes build-essential curl sudo git vim

# Create user
RUN groupadd work           --gid 1000                                                     && \
    adduser user --uid 1000 --gid 1000 --home /workspace --disabled-password --gecos User

# Setup sudo
RUN echo '%work        ALL=(ALL)       NOPASSWD: ALL' >/etc/sudoers.d/work

# Install NodeJS
RUN curl -fsSL https://deb.nodesource.com/setup_16.x | bash -
RUN apt-get install --yes nodejs

RUN npm -g update npm
RUN npm -g install yarn npm-check-updates @angular/cli @ionic/cli

EXPOSE 4200

#
USER user

VOLUME [ "/workspace" ]
WORKDIR /workspace

RUN echo "\nalias ll='ls -al'"            >>/workspace/.bashrc

CMD ["/bin/bash"]
