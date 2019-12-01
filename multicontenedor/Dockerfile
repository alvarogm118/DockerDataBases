FROM ubuntu:16.04
RUN apt-get update
RUN apt-get install \
        apt-transport-https \
        ca-certificates \
        curl \
        gnupg-agent \
        software-properties-common -y
RUN curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
RUN apt-key fingerprint 0EBFCD88
RUN add-apt-repository \
       "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
       $(lsb_release -cs) \
       stable"
RUN apt-get update
RUN apt-get install docker-ce docker-ce-cli containerd.io -y
RUN apt-get install docker-ce=5:19.03.5~3-0~ubuntu-xenial docker-ce-cli=5:19.03.5~3-0~ubuntu-xenial
RUN curl -L "https://github.com/docker/compose/releases/download/1.24.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
RUN chmod +x /usr/local/bin/docker-compose
RUN curl -sL https://deb.nodesource.com/setup_8.x | bash -
RUN apt-get install nodejs -y
RUN apt install git -y
RUN git clone https://github.com/CORE-UPM/CRM_2017
RUN export CLOUDINARY_URL=cloudinary://457429635615339:kk4m51ylXGlcIqeRpPSpMt9OaJI@alvaroana
WORKDIR /CRM_2017
RUN npm install
EXPOSE 3000
CMD npm run-script migrate_local
CMD npm run-script seed_local
CMD npm run-script supervisor

