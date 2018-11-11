FROM 1and1internet/ubuntu-16-sshd

MAINTAINER  wangtun (wangtun@uni-ubi.com)

# 安装软件
#RUN apt-get update \
#    && apt-get -y install build-essential
    
# 安装第三方模块
RUN pip install HTMLParser python-magic tornado

ADD main.py /root/main.py
RUN chmod 777 /root/main.py

# 定义可以挂载的目录
VOLUME ["/opt" "/tmp"]
