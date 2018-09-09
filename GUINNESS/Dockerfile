# ベースイメージ
FROM nvidia/cuda:8.0-cudnn6-devel
# 作成したユーザ情報
MAINTAINER kagamiwomiru <soromonneo@gmail.com>

# アップデート
RUN apt update && apt upgrade -y

# 日本語化
RUN apt install -y language-pack-ja-base language-pack-ja && \
    echo 'export LANG=ja_JP.UTF-8' >> ~/.bashrc && \
    echo 'cd' >> ~/.bashrc

# 必要なライブラリ/ソフトウェアをインストール
## apt-get(apt)
RUN apt install -y wget unzip less vim python3 python3-pip python3-tk python3-pyqt4 git libgtk2.0-0 libsm6 libxrender1 libfontconfig1

## pip3
RUN pip3 install -U pip && \
    pip install chainer==1.24.0  opencv-python matplotlib pillow scipy

## GUINNESS本体ファイル
RUN cd ~/ && git clone https://github.com/HirokiNakahara/GUINNESS.git

## サンプルデータセットのダウンロード
##ここで失敗する場合は下の行をコメントにして、手動でダウンロードしてください。（その場合、コンテナとホストをマウントする必要があります。

RUN wget  -O ~/class3_images.zip "https://www.dropbox.com/s/59fx0r5fuqmuo3j/class3_images.zip?dl=1" && \
    unzip ~/class3_images.zip
    
###データセットの場所の設定
RUN echo "../class3_images/airplane800 airplane" > ~/GUINNESS/list.txt && \
    echo "../class3_images/pets800 pets" >> ~/GUINNESS/list.txt && \
    echo "../class3_images/car800 car" >> ~/GUINNESS/list.txt

# データセットのピクル化(データセットをGUINNESSで読める形にします)
RUN  python3 ~/GUINESS/gen_training_data.py --pathfile ~/GUINESS/list.txt --dataset  class3  --size  48  --keepaspect  yes