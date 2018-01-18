FROM base:1.0

LABEL maintainer=nandaman221@gmail.com

# 切换到root下
WORKDIR /root

# RUN wget -qO- "https://nodejs.org/dist/v8.9.4/node-v$NODE_VERSION-linux-x64.tar.xz" \
COPY node-v8.9.4-linux-x64.tar.xz node-v8.9.4-linux-x64.tar.xz
RUN tar -xJf "node-v8.9.4-linux-x64.tar.xz" -C /usr/local --strip-components=1 --no-same-owner \
  && rm "node-v8.9.4-linux-x64.tar.xz" \
  && ln -s /usr/local/bin/node /usr/local/bin/nodejs


# 使用默认启动文件

ENTRYPOINT ["/bin/bash", "/root/bootstrap.sh"]

# manipulation below:
#   Build: "docker build -t nodejs:8.9.4 ."
#   Run And Listen: "docker run -d -P nodejs:8.9.4"