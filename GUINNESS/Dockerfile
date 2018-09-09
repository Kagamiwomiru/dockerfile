# ベースイメージ
FROM nvidia/cuda:8.0-cudnn6-devel
# 作成したユーザ情報
MAINTAINER kagamiwomiru <soromonneo@gmail.com>

# アップデート
RUN apt update && apt upgrade -y

# 日本語化
RUN apt install -y language-pack-ja-base language-pack-ja && \
    echo 'export LANG=ja_JP.UTF-8' >> ~/.profile && \
    echo 'cd' >> ~/.profile

# 必要なライブラリ/ソフトウェアをインストール
## apt-get(apt)
RUN apt install -y python3 python3-pip python3-pyqt4 git libgtk2.0-0 libsm6 libxrender1 libfontconfig1

## pip3
RUN pip3 install -U pip && \
    pip install chainer==1.24.0  opencv-python matplotlib pillow scipy

## GUINNESS本体ファイル
RUN cd ~/ && git clone https://github.com/HirokiNakahara/GUINNESS.git