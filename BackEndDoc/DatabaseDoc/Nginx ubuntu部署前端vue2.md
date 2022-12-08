# 步骤：一共四步
## 查看ubuntu版本：lsb_release -a
## 第 1 步：安装 Nginx
由于 Nginx 可以从 ubuntu 软件源中获得，因此我们可以使用 apt 来安装 Nginx。
我们可以使用以下命令安装 Nginx 到 Ubuntu 中。
sudo apt update
sudo apt install nginx

## 第 2 步：启动和关闭Nginx指令
sudo systemctl start nginx
sudo systemctl stop nginx
sudo systemctl restart nginx

## 第3步：查看Nginx是否启动，
1-- ps查看进程，利用nginx关键字过滤

    ps -aux | grep nginx

2--直接查看进程pid

ps -C nginx -o pid


停止nginx:

    1:ps -ef | grep nginx 查出进程id， 
    kill -9 进程id 杀死进程

 2:kill -9 进程id  杀死进程

## nginx默认端口是80的，访问服务器网址如;43.139.155.223，如果出现Nginx界面，则Nginx成功启动
## Nginx默认配置路径：/etc/nginx/conf.d/
## 第四步配置前端Vue2的配置文件
 因为，由nginx.conf文件调用conf.d路径下的配置文件，使用在conf.d目录下，
 建立一个文件，文件名任意取，但一定要以.conf结尾如nginx.conf
### 如nginx.con配置内容如下：
```
server {
        listen  8080;
        server_name localhost;

        location  /{
                root /home/ubuntu/app/dist1;
                index index.html;
        }
}
```
#### 解释：
listen：监听端口，一般情况下监听端口是8080
server_name:服务器主机名 如;43.139.155.223
root: 定位dist1即vue2打包在linux下的路径
index：即加载初始页面，dist1下一定要有index.html才可以加载出来
### 重新加载修改后的配置
sudo nginx -s reload

## 问题：
### 问题一：nginx：403 forbidden 二种原因 - ZengGW - 博客园 (cnblogs.com)
### Answer:
因为权限不够，在访问的dist1目录下，给予 777 权限，以及在nginx.conf配置文件中，第一行 修改为user root，然后重新加载修改后的配置
