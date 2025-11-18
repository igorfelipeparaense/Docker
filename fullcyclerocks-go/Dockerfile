FROM golang:alpine AS builder

RUN apk add --no-cache upx

WORKDIR /app

COPY . .

RUN go build -ldflags="-s -w" -o fullcycle

RUN upx --best fullcycle

FROM scratch

COPY --from=builder /app/fullcycle /fullcycle

ENTRYPOINT ["/fullcycle"]
