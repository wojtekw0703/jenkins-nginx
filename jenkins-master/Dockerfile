FROM jenkins/jenkins:latest
LABEL maintainer="Adam Wieczorek"

# Prep Jenkins Directories
USER root
RUN mkdir /var/log/jenkins
RUN mkdir /var/cache/jenkins
RUN chown -R jenkins:jenkins /var/log/jenkins
RUN chown -R jenkins:jenkins /var/cache/jenkins
USER jenkins

# Set Defaults
ENV JAVA_OPTS="-Xmx1024m"
ENV JENKINS_OPTS="--logfile=/var/log/jenkins/jenkins.log  --webroot=/var/cache/jenkins/war"