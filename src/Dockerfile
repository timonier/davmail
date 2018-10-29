FROM openjdk:jre-alpine

LABEL \
    maintainer="Morgan Auchede <morgan.auchede@gmail.com>"

ENV \
    S6_BEHAVIOUR_IF_STAGE2_FAILS=2 \
    S6_KEEP_ENV=1 \
    S6_READ_ONLY_ROOT=1

RUN set -e -u -x \
\
    # Install packages
\
    && apk add --no-cache --no-progress --virtual BUILD_DEPS curl \
\
    # Install davmail
\
    && export $(curl --location "https://github.com/timonier/version-lister/raw/generated/_/davmail/latest" | xargs) \
    && curl --location "${DAVMAIL_RELEASE}" | tar --directory /tmp --extract --gzip \
    && mkdir -p /opt \
    && mv /tmp/davmail-linux-x86_64-"${DAVMAIL_VERSION}"-"${DAVMAIL_BUILD}" /opt/davmail \
\
    # Install dockerize
\
    && export $(curl --location "https://github.com/timonier/version-lister/raw/generated/jwilder/dockerize/latest" | xargs) \
    && curl --location "${DOCKERIZE_RELEASE}" | tar --directory /tmp --extract --gzip \
    && mv /tmp/dockerize /usr/bin/dockerize \
\
    # Install s6-overlay
\
    && curl --location "https://github.com/timonier/dumb-entrypoint/raw/master/src/s6-overlay/installer" | sh -s -- install \
\
    # Clean
\
    && apk del --no-progress BUILD_DEPS \
    && rm -f -r /tmp/*

COPY rootfs/. /

ENTRYPOINT [ "/init" ]

VOLUME [ "/etc/davmail" ]
