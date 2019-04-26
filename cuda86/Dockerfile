# ベースイメージ
FROM nvidia/cuda:8.0-cudnn6-devel
# 作成したユーザ情報
MAINTAINER kagamiwomiru <soromonneo@gmail.com>

# 必要なプログラムのインストール

RUN apt update && apt upgrade -y;apt install -y vim wget git language-pack-ja-base language-pack-ja 

# 環境設定
RUN echo 'export LANG=ja_JP.UTF-8' >> ~/.bashrc && \
    echo 'cd' >> ~/.bashrc

