# syntax=docker/dockerfile:1
FROM alpine:latest AS builder
RUN apk add --no-cache git go
RUN git clone https://github.com/deusdat/arangomigo \
  && cd arangomigo \
  && go build ./cmd/arangomigo/main.go

FROM alpine:latest
MAINTAINER Adolfo Silva "code@adolfosilva.org"
WORKDIR /app
RUN adduser -D arangomigo && chown -R arangomigo /app
COPY --from=builder /arangomigo/main ./
USER arangomigo
ENTRYPOINT ["./main"]
