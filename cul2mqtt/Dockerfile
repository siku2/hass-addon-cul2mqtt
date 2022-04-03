# https://developers.home-assistant.io/docs/add-ons/configuration#add-on-dockerfile
ARG BUILD_FROM
FROM $BUILD_FROM

RUN apk add --no-cache git
RUN pip install paho.mqtt

# Execute during the build of the image
ARG TEMPIO_VERSION BUILD_ARCH
RUN \
    curl -sSLf -o /usr/bin/tempio \
    "https://github.com/home-assistant/tempio/releases/download/${TEMPIO_VERSION}/tempio_${BUILD_ARCH}"


WORKDIR /opt/cul-mqtt
RUN \
    git clone "https://github.com/siku2/hass-cul2mqtt.git" /opt/cul-mqtt && \
    python setup.py install

# Copy root filesystem
COPY rootfs /
