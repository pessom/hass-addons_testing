ARG BUILD_FROM
FROM $BUILD_FROM

ENV LANG C.UTF-8

# Install required packages
RUN apk add --no-cache nfs-utils bash jq coreutils util-linux

# Copy rootfs and scripts
COPY rootfs /

# s6-overlay is already handled by base image