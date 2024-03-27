# -------- stage 1 --------
FROM golang:alpine AS builder

WORKDIR /go/src/app
COPY main.go .

RUN go mod init
RUN go build -o webserver .

CMD ["./webserver"]

# -------- stage 2 --------
FROM scratch

WORKDIR /app
COPY --from=builder /go/src/app /app/

# EXAMPLE
# RUN apt update
# RUN apt install -y nginx
# RUN apt install -y pkg2
# 위 내용을 한 줄로 줄이면 레이어가 줄어들어 전체 용량이 줄어든다
# RUN apt update  && app install -y nginx pkg2


CMD ["./webserver"]
