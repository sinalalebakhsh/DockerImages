FROM golang:1.21.3
WORKDIR /app
COPY . /app

RUN go build -o bin .

ENTRYPOINT [ "/app/bin" ]

 

