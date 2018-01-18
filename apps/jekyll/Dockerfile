FROM ruby:2.3

LABEL maintainer=nandaman221@gmail.com

RUN gem sources --add https://gems.ruby-china.org/ --remove https://rubygems.org/
RUN gem install jekyll

# 配置nginx
COPY nginx.conf /etc/nginx/nginx.conf

# 切换到root下
WORKDIR /root
RUN echo 'cd /webapp\nbundle install\nbundle exec jekyll serve' > app.sh && chmod 755 app.sh
# 生成自定义启动文件
RUN cat sshd.sh nginx-daemon.sh app.sh > bootstrap.sh

ENTRYPOINT ["/bin/bash", "/root/bootstrap.sh"]

# manipulation below:
#   Build: "docker build -t jekyll:0.3 ."
#   Run And Listen: "docker run -d -P jekyll:0.3"