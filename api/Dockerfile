# 使用するGoのバージョン
FROM golang:1.18 as builder

# 作業ディレクトリを設定
WORKDIR /app

# Goの依存関係を管理
COPY go.mod go.sum ./
RUN go mod download

# ソースコードをコピー
COPY . .

# アプリケーションをビルド
RUN CGO_ENABLED=0 GOOS=linux go build -o main .

# 実行用の軽量なイメージ
FROM alpine:latest  
RUN apk --no-cache add ca-certificates

WORKDIR /root/
COPY --from=builder /app/main .

EXPOSE 8080
CMD ["./main"]
