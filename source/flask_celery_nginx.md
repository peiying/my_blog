# flask + celery + nginx 接口测试环境部署


---

次文档是针对用户流失预测平台，机器学习工具后端接口服务部署的一个记录和说明。

## nginx

### 安装 nginx
需要 root 权限
``` shell
sudo yum install nginx
```
### 配置 nginx

``` shell
vim etc/nginx/nginx.conf
```
#### 修改如下：

```
server {
        listen       80;
        server_name  10.160.165.135; #公网地址
        location / {
                proxy_pass http://127.0.0.1:5000; #转发端口
        }
```

### Nginx简单指令

启动 nginx：
命令行输入nginx或者nginx -c nginx配置文件

关闭 nginx：
ps -ef|grep nginx查看nginx 线程ID
kill -QUIT 线程ID

重启 nginx：
```
nginx -s reload
```

这样 nginx 就部署完成了, 如此的简单。因为只需要部署flask接口用来测试，暂时不需要部署 uwsgi 。
