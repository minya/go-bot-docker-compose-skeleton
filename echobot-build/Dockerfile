FROM golang:1.19-alpine AS builder

LABEL maintainer="Mikhail Brel <m@brel.me>" 
LABEL version="0.1"
LABEL description="Runs the bot"

ARG sources_url
ARG botname
ARG bottoken


WORKDIR /app

#downlad and build go project
RUN apk add --no-cache git

RUN git clone ${sources_url} sources

WORKDIR /app/sources/
RUN go mod download
RUN CGO_ENABLED=0 go build -o ${botname}

#copy the bot to the final container
FROM alpine:latest

WORKDIR /app
VOLUME /app

COPY --from=builder /app/sources/${botname} .
# copy settings.json from the current folder to the container
RUN apk add --no-cache ca-certificates

CMD [ "./${botname}" ]