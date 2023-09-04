ARG BUILDER_IMAGE=fission/builder
ARG PY_BASE_IMG=3.8

FROM ${BUILDER_IMAGE}
FROM python:${PY_BASE_IMG}

COPY --from=0 /builder /builder
# RUN apk add --update --no-cache python3-dev build-base gcc bash
ENV DEBIAN_FRONTEND=noninteractive
RUN sed -i 's|http://\(.*\).debian.org/debian|http://mirrors.tuna.tsinghua.edu.cn/debian|g' /etc/apt/sources.list.d/debian.sources
RUN apt-get update && apt-get install -y python3-dev build-essential

ADD defaultBuildCmd /usr/local/bin/build

EXPOSE 8001
