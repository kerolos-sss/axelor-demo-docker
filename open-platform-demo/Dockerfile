FROM axelor/aio-builder as builder
# https://github.com/axelor/abs-webapp.git
RUN mkdir -p /app/src
WORKDIR /app/src

RUN \
  set -ex && \
  git clone https://github.com/axelor/open-platform-demo.git axelor-erp && \
#   sed -e 's|git@github.com:|https://github.com/|' -i axelor-erp/.gitmodules && \
   cd axelor-erp && \
#   git checkout master && \
#   git submodule sync && \
#   git submodule init && \
#   git submodule update && \
#   git submodule foreach git checkout master && \
#   git submodule foreach git pull origin master && \
  sed -e 's|^application.theme.*|application.theme = modern|g' -i src/main/resources/application.properties && \
  ./gradlew --no-daemon -x test npm-build build
  
# CMD ls /app/src/axelor-erp/build/libs/
FROM axelor/aio-base
LABEL maintainer="Axelor <support@axelor.com>"

# COPY --from=builder /app/src/axelor-erp/build/libs/axelor-erp-*.war $CATALINA_BASE/webapps/ROOT.war
COPY --from=builder /app/src/axelor-erp/build/libs/open-platform-demo-*.war $CATALINA_BASE/webapps/ROOT.war
# COPY ./test /usr/local/bin/
COPY ./docker-entrypoint.sh /usr/local/bin/
RUN chmod +x /usr/local/bin/docker-entrypoint.sh 

CMD ["start"]