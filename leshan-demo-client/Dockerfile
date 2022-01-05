### 1. Get Linux
FROM alpine:latest

### 2. Get Java via the package manager
RUN apk update \
    && apk upgrade \
    && apk add --no-cache bash \
    && apk add --no-cache --virtual=build-dependencies unzip \
    && apk add --no-cache curl \
    && apk add --no-cache  openjdk11

ADD https://ci.eclipse.org/leshan/job/leshan-1.x/lastSuccessfulBuild/artifact/leshan-client-demo.jar /

### 3. Requiered args:
ARG URI
ENV URI ${URI}
ARG ENDPOINT
ENV ENDPOINT ${ENDPOINT}
ARG INIT_POS
ENV INIT_POS ${INIT_POS}

### 4. RUN client
ARG DEMO_CLIENT=/leshan-client-demo.jar
ENV DEMO_CLIENT=${DEMO_CLIENT}

CMD /usr/bin/java -jar ${DEMO_CLIENT} -u ${URI} -n ${ENDPOINT} -b -pos ${INIT_POS}