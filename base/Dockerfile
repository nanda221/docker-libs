# 使用固定版本；使用较新的版本可以获取较新版本的apt软件包，比如16.04只有python3.5，17.04可以下载到python3.6了
FROM ubuntu:17.04

LABEL maintainer=nandaman221@gmail.com

# RUN echo "deb \
#         http://mirrors.163.com/ubuntu/ trusty main restricted universe multiversedeb \
#         http://mirrors.163.com/ubuntu/ trusty-security main restricted universe multiversedeb \
#         http://mirrors.163.com/ubuntu/ trusty-updates main restricted universe multiversedeb \
#         http://mirrors.163.com/ubuntu/ trusty-proposed main restricted universe multiversedeb \
#         http://mirrors.163.com/ubuntu/ trusty-backports main restricted universe multiversedeb-src \
#         http://mirrors.163.com/ubuntu/ trusty main restricted universe multiversedeb-src \
#         http://mirrors.163.com/ubuntu/ trusty-security main restricted universe multiversedeb-src \
#         http://mirrors.163.com/ubuntu/ trusty-updates main restricted universe multiversedeb-src \
#         http://mirrors.163.com/ubuntu/ trusty-proposed main restricted universe multiversedeb-src \
#         http://mirrors.163.com/ubuntu/ trusty-backports main restricted universe multiverse"\
#         > /etc/apt/sources.list

# 因更新滞后，取消了国内apt源加速(python3.6等包国内源没有)
RUN apt-get update

# 调试工具
RUN apt-get install -y net-tools vim-tiny

# 安装gcc make等编译、打包工具
RUN apt-get install -y build-essential


RUN apt-get install -y openssh-server
RUN mkdir /var/run/sshd
RUN echo 'root:hello1234' | chpasswd
RUN sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config

RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd

RUN echo '#!/bin/bash\n/usr/sbin/sshd -D' >> /root/bootstrap.sh && chmod 755 /root/bootstrap.sh

ENTRYPOINT ["/root/bootstrap.sh"]

EXPOSE 22

# For test below:
#   Build: "docker build -t base:1.0 ."
#   Run And Listen: "docker run -d -p 10012:22 base:1.0"
#   Connect: "ssh root@0.0.0.0 -p 10012"
#   Check port listened in container: "netstat -tunlp"