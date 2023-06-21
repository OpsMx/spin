FROM opsmx11/java:ubuntu16_java8
RUN apt-get update && apt-get install -y \
    curl 
USER root
RUN curl -LO https://storage.googleapis.com/spinnaker-artifacts/spin/$(curl -s https://storage.googleapis.com/spinnaker-artifacts/spin/latest)/linux/amd64/spin
RUN chmod +x spin
RUN mv spin /usr/local/bin/spin
