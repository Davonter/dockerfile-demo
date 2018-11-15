FROM 1and1internet/ubuntu-16-sshd

MAINTAINER  wangtun (wangtun@uni-ubi.com)

# 安装软件
#RUN apt-get update \
#    && apt-get -y install build-essential
    
# 安装第三方模块
RUN pip install HTMLParser python-magic tornado

# 在/tmp目录下增加临时文件夹
RUN mkdir -p /tmp/0 /tmp/1 /tmp/2 /tmp/3 /tmp/4 /tmp/5 /tmp/6 /tmp/7 /tmp/8 /tmp/9

ADD main.py /root/main.py
RUN chmod 777 /root/main.py

# 定义可以挂载的目录
VOLUME ["/opt"]
