# ベースイメージ
FROM nvidia/cuda:9.0-cudnn7-devel
# 作成したユーザ情報
MAINTAINER kagamiwomiru <soromonneo@gmail.com>

# 必要なプログラムのインストール
RUN apt-get update && apt-get install -y vim wget bzip2 ca-certificates \
    libglib2.0-0 libxext6 libsm6 libxrender1 git language-pack-ja-base language-pack-ja 

RUN echo 'export PATH=/opt/conda/bin:$PATH' > /etc/profile.d/conda.sh && \
    wget --quiet https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda.sh && \
    /bin/bash ~/miniconda.sh -b -p /opt/conda && \
    rm ~/miniconda.sh

RUN apt-get install -y curl grep sed dpkg && \
    TINI_VERSION=`curl https://github.com/krallin/tini/releases/latest | grep -o "/v.*\"" | sed 's:^..\(.*\).$:\1:'` && \
    curl -L "https://github.com/krallin/tini/releases/download/v${TINI_VERSION}/tini_${TINI_VERSION}.deb" > tini.deb && \
    dpkg -i tini.deb && \
    rm tini.deb && \
    apt-get clean


ENV PATH /opt/conda/bin:$PATH

#CKFaceCoreのダウンロード
RUN git clone https://github.com/Kagamiwomiru/CKFaceCore.git 


# condaパッケージをインストール

RUN conda install -y keras-gpu opencv pillow 


# 環境設定
RUN echo 'export LANG=ja_JP.UTF-8' >> ~/.bashrc && \
    echo 'cd CKFaceCore' >> ~/.bashrc


CMD echo "コンテナの中に入るには\\n$ docker run --runtime=nvidia -it イメージ名 bash \\nと入力してください。"
