FROM openjdk:jre-alpine

LABEL \
    maintainer="Morgan Auchede <morgan.auchede@gmail.com>"

ENV \
    DAVMAIL_VERSION=latest \
    S6_BEHAVIOUR_IF_STAGE2_FAILS=2 \
    S6_KEEP_ENV=1

RUN set -ex \

    # Install packages

    && apk add --no-cache --no-progress --virtual BUILD_DEPS \
           curl \

    && apk add --no-cache --no-progress \
           ca-certificates \

    # Install davmail

    && export $(curl "https://raw.githubusercontent.com/timonier/version-lister/release/generated/davmail/${DAVMAIL_VERSION}" | xargs) \

    && curl --location "http://downloads.sourceforge.net/project/davmail/davmail/${DAVMAIL_VERSION}/davmail-linux-x86_64-${DAVMAIL_VERSION}-${DAVMAIL_BUILD}.tgz" | tar --directory /tmp --extract --gzip \
    && mv "/tmp/davmail-linux-x86_64-${DAVMAIL_VERSION}-${DAVMAIL_BUILD}" /usr/share/davmail \

    # Install timonier/dumb-entrypoint

    && curl --location "https://github.com/timonier/dumb-entrypoint/raw/master/src/s6-overlay/installer" | INSTALL_DIRECTORY="/usr/sbin" sh -s -- install \

    # Clean

    && apk del --no-progress \
           BUILD_DEPS \

    && rm -f -r \
           /tmp/*

COPY ./rootfs /

ENTRYPOINT [ "/init" ]
