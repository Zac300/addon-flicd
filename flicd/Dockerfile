ARG BUILD_FROM=hassioaddons/ubuntu-base:3.1.0

FROM ${BUILD_FROM}

# Set shell
SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# Setup base system
RUN apt-get update \
    \
    && rm -fr \
        /tmp/* \
        /var/{cache,log}/* \
        /var/lib/apt/lists/*

# Copy root filesystem
COPY rootfs /

# Add flicd binary
ARG BUILD_ARCH
COPY bin/flicd-${BUILD_ARCH} /usr/bin/flicd

# Build arguments
ARG BUILD_DATE
ARG BUILD_REF
ARG BUILD_VERSION

# Labels
LABEL \
    io.hass.name="flicd" \
    io.hass.description="Flicd service for intercepting commands from flic buttons." \
    io.hass.arch="${BUILD_ARCH}" \
    io.hass.type="addon" \
    io.hass.version=${BUILD_VERSION} \
    maintainer="Zac Krebbekx <zkrebbekx@addons.community>" \
    org.label-schema.description="Flicd service for intercepting commands from flic buttons." \
    org.label-schema.build-date=${BUILD_DATE} \
    org.label-schema.name="flicd" \
    org.label-schema.schema-version="1.0" \
    org.label-schema.usage="https://github.com/Zac300/addon-flicd/tree/master/README.md" \
    org.label-schema.vcs-ref=${BUILD_REF} \
    org.label-schema.vcs-url="https://github.com/Zac300/addon-flicd" \
    org.label-schema.vendor="Zac Krebbekx Hass.io Add-ons"
