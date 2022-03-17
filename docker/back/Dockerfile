ARG TAIGA_VERSION=6.4.2
ARG RELEASE=master
FROM taigaio/taiga-back:${TAIGA_VERSION}
RUN apt-get update && apt-get install git -y
RUN git clone https://github.com/OuFinx/taiga-contrib-openid-auth && cd taiga-contrib-openid-auth && git checkout ${RELEASE}
RUN cd taiga-contrib-openid-auth/back; pip install -e .
COPY config.py /taiga-back/settings/config.py
ENV OPENID_SCOPE="openid email"