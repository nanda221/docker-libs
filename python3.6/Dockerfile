FROM base:1.0

LABEL maintainer=nandaman221@gmail.com

# ubuntu17.04不自带python2.7，在安装python3前无需删除老版本
# RUN apt purge -y python python-minimal


# reference: https://askubuntu.com/questions/865554/how-do-i-install-python-3-6-using-apt-get
# ubuntu17.07 apt源已包含python3.6
RUN apt-get update
RUN apt-get install -y python3.6 \
python3-pip

RUN ln -s /usr/bin/python3.6 /usr/bin/python && \
ln -s /usr/bin/pip3 /usr/bin/pip

ENTRYPOINT ["/root/bootstrap.sh"]

# manipulation below:
#   Build: "docker build -t python:3.6 ."
#   Run And Listen: "docker run -d -P python:3.6"