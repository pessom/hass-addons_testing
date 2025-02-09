ARG BUILD_FROM
FROM $BUILD_FROM

ARG RABBITMQ_VERSION="3.13.7-r0"
ARG RABBITMQ_HOME="/data/config"
ARG RABBITMQ_DATA_DIR="/data/rabbitmq"

ENV LANG=C.UTF-8 \
    LANGUAGE=C.UTF-8 \
    LC_ALL=C.UTF-8 \
    RABBITMQ_CONFIG_FILE="/data/config" \
    RABBITMQ_MNESIA_BASE="/data/rabbitmq"
#    RABBITMQ_LOG_BASE="/var/log/rabbitmq"

RUN apk add --no-cache rabbitmq-server=${RABBITMQ_VERSION} procps tzdata
RUN addgroup -g 101 -S rabbitmq; \
	adduser -u 100 -S -h "${RABBITMQ_DATA_DIR}" -G rabbitmq rabbitmq; \
	mkdir -p "${RABBITMQ_DATA_DIR}" "${RABBITMQ_HOME}" "${RABBITMQ_HOME}/conf.d" /tmp/rabbitmq-ssl /var/log/rabbitmq; \
	chown -fR rabbitmq:rabbitmq "${RABBITMQ_DATA_DIR}" "${RABBITMQ_HOME}" /tmp/rabbitmq-ssl /var/log/rabbitmq; \
	chmod 1777 "${RABBITMQ_DATA_DIR}" "${RABBITMQ_HOME}" "${RABBITMQ_HOME}/conf.d" /tmp/rabbitmq-ssl /var/log/rabbitmq

EXPOSE 4369 5671 5672 15691 15692 25672

COPY rootfs /
