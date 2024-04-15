# Node.jsの公式イメージをベースにする
FROM node:16

# 作業ディレクトリを設定
WORKDIR /app

# 依存関係のファイルをコピー
COPY react-ts/package.json react-ts/package-lock.json ./

# 依存関係をインストール
RUN npm install

# ソースコードをコピー
COPY react-ts/ ./

# アプリケーションをビルド
RUN npm run build

# serveをインストールしてReactアプリを提供
RUN npm install -g serve
CMD ["serve", "-s", "build", "-l", "3000"]

EXPOSE 3000