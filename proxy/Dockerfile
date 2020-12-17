# -----------------------------------------------------------------------------
# docker-lilypadmc Proxy
#
# Builds a basic docker image that can run Lilypadmc Proxy
# (http://lilypadmc.org/).
#
# Authors: Pieter Maes
# -----------------------------------------------------------------------------

# Base system is alpine linux.
FROM alpine:latest

RUN apk -U add bash

# Installer
COPY assets/install /app/install
RUN chmod 755 /app/install
RUN /app/install
#Cleanup
RUN rm /app/install

# Load in all of our config files.
ADD assets/proxy.yml /opt/lilypad-proxy/proxy.yml

# Copy init script
COPY assets/init /app/init
RUN chmod 755 /app/init

# /app/init runs it.
EXPOSE 25565
VOLUME ["/data"]

WORKDIR /data

ENTRYPOINT ["/app/init"]
CMD ["app:start"]

