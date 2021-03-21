FROM node:14.16.0-buster-slim as stage1

LABEL maintainer="aprokopyev@somewhere.com"

RUN apt-get update && \
    apt-get install -y openssh-server supervisor

WORKDIR /usr/src/app

COPY example .

RUN npm install

FROM stage1

COPY "autorun.sh" "autorun.sh"

COPY ["supervisord.conf", "/etc/supervisor/conf.d/supervisord.conf"]

RUN chmod +x /usr/src/app/autorun.sh

EXPOSE 3000

ENTRYPOINT ["/bin/bash"]

CMD ["/usr/src/app/autorun.sh"]
