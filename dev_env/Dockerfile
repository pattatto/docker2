FROM centos:centos7.3.1611

#必要なgroupinstallをインストール
RUN yum -y groupinstall "Development Tools"
#各種パッケージインストール。
RUN yum -y install \ 
    wget \
    git \
    zlib-devel

WORKDIR /opt
# Pythonをダウンロード
RUN wget https://www.python.org/ftp/python/3.6.7/Python-3.6.7.tgz && \
    #ファイルと解凍
    tar xzvf Python-3.6.7.tgz && \
    rm -f Python-3.6.7.tgz

# makeでインストール
WORKDIR ./Python-3.6.7
RUN ./configure --with-threads && \
    make install

# pipインストール
WORKDIR /opt
RUN wget https://bootstrap.pypa.io/get-pip.py && \
    python get-pip.py && \
    rm -f get-pip.py

RUN pip install jupyterlab

WORKDIR /
CMD ["/bin/bash"]