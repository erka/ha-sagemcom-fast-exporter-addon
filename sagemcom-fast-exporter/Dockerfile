# https://developers.home-assistant.io/docs/add-ons/configuration#add-on-dockerfile
ARG BUILD_FROM=ghcr.io/home-assistant/aarch64-base:latest
ARG BUILD_VERSION=v0.3.1

#FROM ghcr.io/hairyhenderson/sagemcom_fast_exporter:${BUILD_VERSION} AS base

FROM $BUILD_FROM

ENV USER=nobody
ENV OTEL_TRACES_EXPORTER=none
ENV OTEL_SDK_DISABLED=true
# Execute during the build of the image
#COPY --from=base /sagemcom_fast_exporter /sagemcom_fast_exporter

# hack until the changes merged back 
COPY sagemcom_fast_exporter_linux-arm64 /sagemcom_fast_exporter

COPY start-exporter /start-exporter
RUN chmod a+x /start-exporter

CMD [ "/start-exporter" ]
