FROM golang:1.15.5
RUN go get github.com/hashicorp/nomad
RUN GOOS=linux GOARCH=amd64 go build -o /go/bin/nomad -tags nomad_test github.com/hashicorp/nomad
COPY nomad.hcl /etc/nomad/
ENTRYPOINT [ "/go/bin/nomad" ]
CMD [ "agent", "-dev", "-config=/etc/nomad/" ]
