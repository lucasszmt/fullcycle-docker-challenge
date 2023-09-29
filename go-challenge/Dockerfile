FROM golang:1.21 AS builder

WORKDIR /usr/src/app

COPY . .

# the -ldflags "-s -w" flag is used to reduce the size of the binary, -s removes the symbol table and -w removes the DWARF debugging information
RUN go build -ldflags "-s -w" -o app main.go

FROM scratch

WORKDIR /usr/src/app

COPY --from=builder /usr/src/app/app .

ENTRYPOINT ["./app"]