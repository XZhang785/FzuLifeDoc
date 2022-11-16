#   服务器环境搭建
## JDK配置
版本：java"1.8.0_352"
搭建过程
1.命令行安装
2.修改名称
3.配置jdk对应的环境变量

安装jdk
```
apt-get install openjdk-8-jdk
```
配置环境变量
在命令行运行sudo vim ~/.bashrc文件末尾
export JAVA_HOME="/usr/lib/jvm/java-1.8.0-openjdk-amd64"
export PATH=$JAVA_HOME/bin
想要如下：

![在这里插入图片描述](https://img-blog.csdnimg.cn/02981dfa42044abaaac9e9594c6f7455.png)

## Mysql配置
1.更新软件源
sudo apt-get update
2.安装mysql-server
sudo apt-get install mysql-server
3.监听mysq是否启动
sudo netstat -tap | grep mysql
4.启动和关闭mysql服务
service mysql start
service mysql stop
5.进入mysql
sudo mysql

## SSh配置
1.进入到.ssh文件夹下
cd ~/.ssh
2.ssh服务器端的安装
sudo apt-get  install openssh-server
3.ssh登录本机

ssh localhost
4.退出登录
exit
5.ssh免密登录配置
在~/.ssh文件夹下,生成密匙
ssh-keygen -t rsa，直接回车
6.将生成的公匙追加到 authorized_keys中
cat id_rsa.pub >> authorized_keys
7.ssh localhost直接登录，不需要密码
## Window本地下，SSh远程登录linux云服务器
1.在C:\Users\29848\.ssh\known_hosts中添加对于的linux云服务器密匙
2.ssh  用户名@ip地址，即可远程登录

## Node.js的配置 
1：下载
wget https://nodejs.org/dist/v14.17.4/node-v14.17.4-linux-x64.tar.xz
2：解压
tar xf node-v14.17.4-linux-x64.tar.xz3
3.解压成功后可以选择删除压缩包：
rm -rf node-v14.17.4-linux-x64.tar.xz
4.创建目录
mkdir /usr/local/lib/node
5.移动目录并重命名
mv node-v14.17.4-linux-x64 /usr/local/lib/node/nodejs
6.设置环境变量
执行;
sudo vim ~/.bashrc

在文件底部添加环境变量：
export NODEJS_HOME=/usr/local/lib/node/nodejs
export PATH=$NODEJS_HOME/bin: $PATH
![在这里插入图片描述](https://img-blog.csdnimg.cn/dadb853c96424e198b24c4afdfad3fe8.png)
7.刷新修改
source ~/.bashrc
8.安装完成，查看版本号
node版本号：
node -v
npm -v
![在这里插入图片描述](https://img-blog.csdnimg.cn/20aba8ef5eef47099a585eb5c0f244ff.png)
8.过程可能会遇到如下情况：
![在这里插入图片描述](https://img-blog.csdnimg.cn/ffb14a416a1949ddbbca5c8c6e30037d.png)
Ubuntu18.04
问题：Command 'ls' is available in '/bin/ls'
解决办法：export PATH=/usr/bin:/bin

## Vue安装
