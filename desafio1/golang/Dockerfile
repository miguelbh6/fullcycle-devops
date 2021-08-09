FROM golang:rc-alpine3.14 as Builder
ENV GO111MODULE=off
WORKDIR /app
COPY ./src ./
RUN CGO_ENABLED=0 GOOS=linux go build -ldflags '-w' -o servicex

FROM scratch
WORKDIR /app
COPY --from=builder /app/servicex .
CMD ["/app/servicex"] 