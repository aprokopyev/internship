LABEL maintainer="aprokopyev@somewhere.com"

FROM node:14.16.0-buster-slim as stage1

RUN apt-get update && \
    apt-get install -y openssh-server supervisor

WORKDIR /usr/src/app

COPY example .

RUN npm install

FROM stage1

WORKDIR /usr/src/app/node_modules

COPY /usr/src/app/node_modules .

WORKDIR /usr/src/app

COPY /usr/src/app/app.js .

COPY "autorun.sh" "autorun.sh"

RUN chmod +x /usr/src/app/autorun.sh

EXPOSE 3000

ENTRYPOINT ["/bin/bash"]

CMD ["/usr/src/app/autorun.sh"]

#FROM node
#WORKDIR /usr/src/app
#COPY example/package*.json example/app.js ./
#RUN npm install
#RUN apt-get update && apt-get install -y openssh-server apache2 supervisor
#RUN mkdir -p /var/run/sshd /var/log/supervisor
#COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf
#EXPOSE 3000
#CMD ["/usr/bin/supervisord"]