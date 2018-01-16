FROM base:1.0

LABEL maintainer=nandaman221@gmail.com

RUN apt-get update
RUN apt-get install -y ruby-dev

# CMD method should added here
# RUN echo 'ruby -v' >> /root/bootstrap.sh

# 安装gcc make等build和打包工具，jekyll需要(https://jekyllrb.com/docs/installation/)
# 已在base主镜像中安装
# RUN apt-get install -y build-essential

ENTRYPOINT ["/root/bootstrap.sh"]

# manipulation below:
#   Build: "docker build -t ruby:2.3 ."
#   Run And Listen: "docker run -d -P ruby:2.3"