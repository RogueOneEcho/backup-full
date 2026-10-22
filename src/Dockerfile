ARG ALPINE_VERSION=3.24.3
FROM alpine:${ALPINE_VERSION}
RUN apk add --no-cache bash restic
WORKDIR /app
COPY logging /app/logging
COPY file-env /app/file-env
COPY backup /app/backup
RUN chmod a+x /app/logging && chmod a+x /app/file-env && chmod a+x /app/backup
ENTRYPOINT ["/app/backup"]
