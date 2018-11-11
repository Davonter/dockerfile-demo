## 创建镜像

`docker build -t tornado:v1 .`

## 启动容器

`docker run -d -p 8080:8080 --network host -v /opt:/opt -v /tmp:/tmp tornado:v1 python /root/main.py`