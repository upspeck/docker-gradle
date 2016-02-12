FROM upspeck/groovy:2.4.5
MAINTAINER Jeyson Maia <jeyson@upspeck.io>

# Gradle
ENV GRADLE_VERSION 2.11
ENV GRADLE_HASH 8d7437082356c9fd6309a4479c8db307673965546daea445c6c72759cd6b1ed6
WORKDIR /usr/lib
RUN wget https://downloads.gradle.org/distributions/gradle-${GRADLE_VERSION}-bin.zip
RUN echo "${GRADLE_HASH} gradle-${GRADLE_VERSION}-bin.zip" > gradle-${GRADLE_VERSION}-bin.zip.md5
RUN md5sum -c gradle-${GRADLE_VERSION}-bin.zip.md5
RUN unzip "gradle-${GRADLE_VERSION}-bin.zip"
RUN ln -s "/usr/lib/gradle-${GRADLE_VERSION}/bin/gradle" /usr/bin/gradle
RUN rm "gradle-${GRADLE_VERSION}-bin.zip"
RUN mkdir -p /usr/src/app

# Set Appropriate Environmental Variables
ENV GRADLE_HOME /usr/src/gradle
ENV PATH $PATH:$GRADLE_HOME/bin

# Caches
VOLUME /root/.gradle/caches
VOLUME /root/.m2/repository

USER $USER
# Default command is "/usr/bin/gradle -version" on /usr/bin/app dir
# (ie. Mount project at /usr/bin/app "docker --rm -v /path/to/app:/usr/bin/app gradle <command>")
#VOLUME /usr/bin/app
WORKDIR /usr/bin/app
