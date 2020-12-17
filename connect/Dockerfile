# -----------------------------------------------------------------------------
# docker-lilypadmc Connect
#
# Builds a basic docker image that can run Lilypadmc
# (http://lilypadmc.org/).
#
# Authors: Pieter Maes
# -----------------------------------------------------------------------------

# Base system is alpine linux
FROM alpine:latest

RUN apk -U add bash

# Build and install lilypad connect
COPY assets/install /app/install
RUN chmod 755 /app/install
RUN /app/install
# Cleanup
RUN rm /app/install

# Add initscript
ADD assets/init /app/init
# Fix permissions
RUN chmod 755 /app/init


# /start runs it.
EXPOSE 5091
VOLUME ["/data"]
WORKDIR /data

ENTRYPOINT ["/app/init"]
CMD ["app:start"]

