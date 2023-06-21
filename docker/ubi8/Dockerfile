FROM registry.access.redhat.com/ubi8/go-toolset:1.17 as build
ARG VERSION=dev
WORKDIR /app
COPY ./ ./
ENV LD_VERSION="-X github.com/spinnaker/spin/version.Version=${VERSION}"
RUN GOARCH=amd64 GOOS=linux CGO_ENABLED=0 go build \
    -ldflags "${LD_VERSION}" .

FROM registry.access.redhat.com/ubi8/ubi:8.8 

COPY --from=build /app/spin /usr/local/bin
RUN adduser spinnaker
USER spinnaker
ENTRYPOINT ["spin"]
