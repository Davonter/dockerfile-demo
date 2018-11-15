FROM 1and1internet/ubuntu-16-sshd

# 下面是一些创建者的基本信息
MAINTAINER wynter (wangtdada@gmail.com)

# 安装升级gcc,git
RUN apt-get update \
    && apt-get -y install --assume-yes apt-utils \
    && apt-get -y install git wget \
    && apt-get -y install build-essential libpcre3 libpcre3-dev libssl-dev zlib1g-dev spawn-fcgi fcgiwrap

RUN mkdir -p /home/uniubi/software/temp \
    && cd /home/uniubi/software/ \
    && wget http://nginx.org/download/nginx-1.14.0.tar.gz \
    && tar -zxvf nginx-1.14.0.tar.gz -C /home/uniubi/software/temp \
    && cd /home/uniubi/software/temp/ \
    && git clone https://github.com/fdintino/nginx-upload-module.git \
    && git clone https://github.com/arut/nginx-rtmp-module.git \
    && cd /home/uniubi/software/temp/nginx-1.14.0 \
    && ./configure --add-module=/home/uniubi/software/temp/nginx-upload-module --add-module=/home/uniubi/software/temp/nginx-rtmp-module \
    && make \
    && make install
    
# 在/tmp目录创建临时hash阵列
RUN mkdir -p /tmp/0 /tmp/1 /tmp/2 /tmp/3 /tmp/4 /tmp/5 /tmp/6 /tmp/7 /tmp/8 /tmp/9

# 将nginx文件覆盖
COPY nginx.conf /usr/local/nginx/conf/

# 将cgi.cgi赋值到html目录
COPY cgi-bin/ /usr/local/nginx/

# 定义可以挂载的目录，分别为虚拟主机的挂在目录，证书目录，配置目录
VOLUME ["/usr/local/nginx/html", "/opt"]

# 定义工作目录

CMD /usr/local/nginx/sbin/nginx -g "daemon off;" && /usr/bin/spawn-fcgi -f /usr/sbin/fcgiwrap -p 8081
