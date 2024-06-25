VERSION --global-cache --try 0.7
IMPORT ../../earthly/go AS go

deps:
    FROM golang:1.22.2-alpine3.19
    WORKDIR /libs/pg-replicate-sql

    DO go+DEPS --ginkgo="false"

src:
    FROM +deps

    COPY . .
    SAVE ARTIFACT /libs/pg-replicate-sql
    
# check:
#     FROM +src

#     DO go+FMT
#     DO go+LINT

test:
    FROM +src

    RUN go test -v ./...
