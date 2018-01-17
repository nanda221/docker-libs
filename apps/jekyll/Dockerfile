FROM ruby:2.3

LABEL maintainer=nandaman221@gmail.com

RUN gem sources --add https://gems.ruby-china.org/ --remove https://rubygems.org/
RUN gem install jekyll


# CMD method should added here
RUN echo "#!/bin/bash\nsh sshd.sh\nsh nginx.sh" >> /root/bootstrap.sh && chmod 755 /root/bootstrap.sh

ENTRYPOINT ["/root/bootstrap.sh"]

EXPOSE 80

# manipulation below:
#   Build: "docker build -t jekyll:0.3 ."
#   Run And Listen: "docker run -d -P jekyll:0.3"