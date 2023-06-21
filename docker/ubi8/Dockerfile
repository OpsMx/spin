FROM registry.access.redhat.com/ubi8/go-toolset as build
ARG VERSION=dev
WORKDIR /app
COPY ./ ./
ENV LD_VERSION="-X github.com/spinnaker/spin/version.Version=${VERSION}"
RUN GOARCH=amd64 GOOS=linux CGO_ENABLED=0 go build \
    -ldflags "${LD_VERSION}" .

FROM registry.access.redhat.com/ubi8/ubi:8.8 
RUN microdnf update && microdnf install ca-certificates && microdnf clean all
COPY --from=build /app/spin /usr/local/bin
RUN addgroup -S -g 10111 spinnaker
RUN adduser -S -G spinnaker -u 10111 spinnaker
USER spinnaker
ENTRYPOINT ["spin"]
