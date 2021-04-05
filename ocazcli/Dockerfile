FROM registry.redhat.io/ubi8:latest
ENV HOME=/tmp/

# install wget
RUN yum install wget -y

# Install python3 dependency for AZ CLI
RUN yum install -y python3 python3-virtualenv python3-pip

# Install AZ CLI
ADD ./azure-cli.repo /etc/yum.repos.d/
RUN rpm --import https://packages.microsoft.com/keys/microsoft.asc
RUN yum install azure-cli -y
RUN az --version
RUN chmod -R 777 /tmp/.azure

# Install OC CLI
RUN wget -q https://mirror.openshift.com/pub/openshift-v4/clients/oc/4.6/linux/oc.tar.gz
RUN tar -xzf ./oc.tar.gz -C /usr/local/bin/
RUN chmod 755 /usr/local/bin/oc
RUN oc version

USER 1001