FROM jenkins/jenkins

USER root

# RUN yum -y install epel-release
# RUN yum -y install python3 python3-pip

# RUN curl -O https://bootstrap.pypa.io/get-pip.py && \
# 	python get-pip.py && \
# 	pip install ansible --upgrade

# RUN apt-get update
# RUN apt-get install -y ansible

RUN apt-get update && apt-get install python3-pip -y && \
    pip3 install ansible --upgrade &&\
    apt-get upgrade -y && apt-get update
    
# back to the original user

# Install Docker

RUN apt-get update &&\
apt-get install apt-transport-https\
    ca-certificates \
    curl \
    gnupg \
    lsb-release \
    software-properties-common && \
curl -fsSL https://download.docker.com/linux/$(. /etc/os-release; echo "$ID")/gpg > /tmp/dkey; apt-key add /tmp/dkey && \
add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/$(. /etc/os-release; echo "$ID") \
   $(lsb_release -cs) \
   stable" && \
apt-get update && \
apt-get -y install docker-ce

# COmpose

RUN curl -L "https://github.com/docker/compose/releases/download/1.22.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose && chmod +x /usr/local/bin/docker-compose

RUN usermod -aG docker jenkins

USER jenkins