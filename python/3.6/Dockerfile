FROM base:1.0

LABEL maintainer=nandaman221@gmail.com

# 删除ubuntu17.04自带的python3.5
# @todo 删除后，后面install3.5版本的过程中还是会安装3.5
# RUN apt-get purge -y python3.5 python3.5-minimal


# reference: https://askubuntu.com/questions/865554/how-do-i-install-python-3-6-using-apt-get
# ubuntu17.07 apt源已包含python3.5
RUN apt-get update
RUN apt-get install -y python3.6 \
python3-pip

RUN ln -s /usr/bin/python3.6 /usr/bin/python && \
ln -s -f /usr/bin/python3.6 /usr/bin/python3 && \
ln -s /usr/bin/pip3 /usr/bin/pip

ENTRYPOINT ["/root/bootstrap.sh"]

# manipulation below:
#   Build: "docker build -t python:3.6 ."
#   Run And Listen: "docker run -d -P python:3.6"