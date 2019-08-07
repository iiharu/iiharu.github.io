---
title: GitHub Pagesのローカル開発環境
---

# GitHub Pagesのローカル開発環境

最近使い始めたのですが,
GitHubページは便利です.
しかし, ローカルで編集を確認しようとすると環境設定が少し面倒です. (特にWindows)
今回はDockerを使って楽にローカルで編集を確認できるようにしたいと思います.

## 前提
- Dockerはインストール済み
- `docker-compose`を使用(無くても`docker`コマンドからオプションを指定すれば可能)

## ローカル環境
レポジトリのトップディレクトリに`docker-compose.yml`を配置する. (これだけ)

以下が `docker-compose.yml` です.

```docker-compose.yml
version: "3"
services:
  jekyll:
    image: jekyll/jekyll:pages
    command: jekyll serve --watch --force_polling
    volumes:
      - .:/var/www
    working_dir: /var/www
    ports:
      - 4000:4000
```

## 実行
レポジトリのトップディレクトリに移動して,
```
$ docker-compose up
```
を実行して, ブラウザで`localhost:4000`にアクセスすると確認することができます.

## まとめ

jekyllがGitHub Pages用のDockerイメージを用意しているので簡単にできました.
