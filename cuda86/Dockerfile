# ベースイメージ
FROM kagamiwomiru/cuda:8.0-cudnn6-devel
# 作成したユーザ情報
MAINTAINER kagamiwomiru <soromonneo@gmail.com>

ENV PATH /opt/conda/bin:$PATH

# condaパッケージをインストール

RUN conda install -y jupyter


# 環境設定
RUN jupyter notebook --generate-config && \
    echo "c = get_config()" >>  /root/.jupyter/jupyter_notebook_config.py && \
    echo "c.NotebookApp.ip = '0.0.0.0'" >>  /root/.jupyter/jupyter_notebook_config.py && \
    echo "c.NotebookApp.open_browser = False" >>  /root/.jupyter/jupyter_notebook_config.py && \
    echo "c.NotebookApp.port = 8080" >>  /root/.jupyter/jupyter_notebook_config.py && \
    echo "c.NotebookApp.token = ''" >>  /root/.jupyter/jupyter_notebook_config.py 
    
CMD echo "コンテナの中に入るには\\n$ docker run --runtime=nvidia -it イメージ名 bash \\nと入力してください。" && \
    jupyter
