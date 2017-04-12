FROM openjdk:8-jdk-alpine
# Set versions
ARG DRILL_LINK=http://www-us.apache.org/dist/drill/drill-1.10.0/apache-drill-1.10.0.tar.gz
ENV DRILL_HOME /opt/drill/

# Download and extract, set home folder and permissions
RUN useradd -ms /bin/bash drill --home $DRILL_HOME &&  wget -qO- $DRILL_LINK | tar xvz --strip 1 -C $DRILL_HOME && chown drill -R $DRILL_HOME

ADD drill-override.conf $DRILL_HOME/conf/
ADD entrypoint.sh $DRILL_HOME/

ENV DRILL_LOG_DIR $DRILL_HOME/logs

USER drill
WORKDIR $DRILL_HOME
ENTRYPOINT ["bash", "entrypoint.sh"]
