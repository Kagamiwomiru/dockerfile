# ベースイメージ
FROM nvidia/cuda:9.0-cudnn7-devel
# 作成したユーザ情報
MAINTAINER kagamiwomiru <soromonneo@gmail.com>

RUN apt update && apt upgrade -y && apt install -y language-pack-ja-base language-pack-ja python3-pip

RUN pip3 install  jupyter 


# 環境設定
RUN echo 'export LANG=ja_JP.UTF-8'>> ~/.bashrc
RUN jupyter notebook --generate-config && \
    echo "c = get_config()" >>  /root/.jupyter/jupyter_notebook_config.py && \
    echo "c.NotebookApp.ip = '0.0.0.0'" >>  /root/.jupyter/jupyter_notebook_config.py && \
    echo "c.NotebookApp.open_browser = False" >>  /root/.jupyter/jupyter_notebook_config.py && \
    echo "c.NotebookApp.port = 8080" >>  /root/.jupyter/jupyter_notebook_config.py && \
    echo "c.NotebookApp.token = ''" >>  /root/.jupyter/jupyter_notebook_config.py 
    
CMD echo "コンテナの中に入るには\\n$ docker run --runtime=nvidia -it イメージ名 bash \\nと入力してください。" && \
    jupyter notebook
