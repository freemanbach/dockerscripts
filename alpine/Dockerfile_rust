FROM alpine:latest

ENV PATH /usr/local/bin:$PATH

ENV LANG C.UTF-8

MAINTAINER Freeman Lo (aschenbach@gmail.com)

RUN set -eux; \
    apk update   ; \
    apk add wget ; \
    apk add curl ; \
    apk add bash ; \
    apk add vim
    
RUN set -eux; \
    cd /root ; \
    curl https://gist.githubusercontent.com/nelsonJM/10401892/raw/0f5651affda3712c27f3350f0ab2b29107188cff/.profile -o .profile ;\
    curl https://gist.githubusercontent.com/marioBonales/1637696/raw/93a33aa5f1893f46773483250214f8b8b496a270/.bashrc -o .bashrc ; \
    curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y
    
ENTRYPOINT ["/bin/bash"]
