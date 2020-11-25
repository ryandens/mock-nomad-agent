FROM golang:1.14.7 as builder
RUN git clone --depth 1 --branch v0.12.3 https://github.com/hashicorp/nomad.git
RUN cd nomad/ && GOOS=linux GOARCH=amd64 go build -o /go/bin/nomad -tags nomad_test github.com/hashicorp/nomad

FROM debian:stable
COPY --from=builder /go/bin/nomad /go/bin/nomad
COPY nomad.hcl /etc/nomad/
ENTRYPOINT [ "/go/bin/nomad" ]
CMD [ "agent", "-dev", "-config=/etc/nomad/" ]
