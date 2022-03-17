ARG TAIGA_VERSION=6.4.2
ARG RELEASE=master

FROM taigaio/taiga-front:${TAIGA_VERSION}
RUN apk --update add git && \
    rm -rf /var/lib/apt/lists/* && \
    rm /var/cache/apk/*
    
RUN git clone https://github.com/OuFinx/taiga-contrib-openid-auth && cd taiga-contrib-openid-auth && git checkout ${RELEASE}
RUN mkdir -p /usr/share/nginx/html/plugins/openid-auth && cp -r taiga-contrib-openid-auth/front/dist/* /usr/share/nginx/html/plugins/openid-auth

COPY conf.json.template /usr/share/nginx/html/conf.json.template
COPY 30_config_env_subst.sh /docker-entrypoint.d/30_config_env_subst.sh

ENV OPENID_SCOPE="openid email"