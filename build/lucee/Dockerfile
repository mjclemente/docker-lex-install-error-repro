FROM ortussolutions/commandbox:4.6.0
# Not using latest tag. https://hub.docker.com/r/ortussolutions/commandbox/

## Lucee Envs
ENV REDIS_LICENSE_HOME=/root/serverHome/WEB-INF/lucee-server/context/context/ortus/redis

# Copy application in.
COPY ./app/wwwroot/ ${APP_DIR}/

# Copy our extensions in
COPY ./build/lucee/config/ /config/
# Overwrite redis license with production
COPY ./build/lucee/config/license/redis/production/license.properties ${REDIS_LICENSE_HOME}/

# Install our box.json and package.json dependencies and run webpack
WORKDIR $APP_DIR
RUN box install  && \
  box install commandbox-fusionreactor


# Warm up
RUN ${BUILD_DIR}/util/warmup-server.sh