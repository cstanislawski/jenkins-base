FROM jenkins/jenkins:2.426.2-lts

# `ARG` is only available during build time
# `ENV` is available during run time

ENV JAVA_OPTS -Djenkins.install.runSetupWizard=false
ENV JENKINS_HOME /var/jenkins_home
ENV CASC_JENKINS_CONFIG /usr/share/jenkins/ref/casc.yml

# install casc
COPY ./casc.yml ${CASC_JENKINS_CONFIG}

# install plugins
COPY ./plugins.txt /usr/share/jenkins/ref/plugins.txt

RUN jenkins-plugin-cli \
  -f /usr/share/jenkins/ref/plugins.txt \
  --view-security-warnings \
  --clean-download-directory \
  --list
