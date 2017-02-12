FROM alpine:3.4

LABEL \
    maintainer="Morgan Auchede <morgan.auchede@gmail.com>"

ENV \
    DAVMAIL_VERSION=4.7.2 \
    S6_BEHAVIOUR_IF_STAGE2_FAILS=2 \
    S6_OVERLAY_VERSION=1.19.1.1

RUN set -x \

    # Install packages

    && apk add --no-cache --no-progress --virtual build_deps \
           curl \

    && apk add --no-cache --no-progress \
           ca-certificates \
           openjdk8-jre \

    # Install davmail

    && curl -sL "http://downloads.sourceforge.net/project/davmail/davmail/${DAVMAIL_VERSION}/davmail-linux-x86_64-${DAVMAIL_VERSION}-2427.tgz" | tar fxz - -C /tmp \
    && mv /tmp/davmail-linux-x86_64-4.7.2-2427 /usr/lib/davmail \
    && ln -s /usr/lib/davmail/davmail.sh /usr/bin/davmail \

    # Install s6-overlay

    && curl -ksL "https://github.com/just-containers/s6-overlay/releases/download/v${S6_OVERLAY_VERSION}/s6-overlay-amd64.tar.gz" | tar fxz - -C / \

    # Clean

    && apk del --no-progress \
           build_deps \

    && rm -rf \
           /tmp/*

COPY ./rootfs /

ENTRYPOINT [ "/init" ]
