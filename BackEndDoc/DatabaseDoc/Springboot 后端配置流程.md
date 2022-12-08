# 概述：分三步
# 一、从github克隆项目master分支来
## git操作步骤：
### 目录
1.配置用户名和邮箱
2.初始化
3.设置仓库地址
4.拉取代码
5.设置保存账号密码时间
6.查看状态
sudo git config --global user.name 'zhouchaoke'
sudo git config --global user.email'2984972695@qq.com'
sudo git init
sudo git remote add origin https://github.com/zhouchaoke/remake.exe.git
sudo git pull origin master
sudo git config --global credential.helper store
sudo git  status
# 二、在含有pom.xml的项目目录下运行以下命令
mvn clean
mvn compile
mvn package

# 三、最后打包后端，上线命令：
nohup java -jar springboot-0.0.1-SNAPSHOT.jar > logname.log 2>&1 &
## 查看输出日志
Cat logname.log


# 问题：可能出现的错误
注意点：
#  问题一：会出现springboot-resources-plugins插件报错
# Answer：
注意的问题是：target输出的文件路径必须要由权限，就是从github克隆下来的项目如
项目名是remake.exe需要赋予权限例如 
sudo chown ubuntu:ubuntu remake.exe
sudo chmod 777 remake.exe



# 问题二： 【ubuntu】fatal: detected dubious ownership in repository at ...

# answer：
文件的所有者不对，切换一下就行 

# 问题三：解决git error: could not lock config file C:/Program Files/Git/mingw64/etc/gitconfig: Permission deny
# answer：github要用https连接
# 问题四：Cloning into 'remake.exe'...error: RPC failed; curl 16 Error in the HTTP2 framing layerfatal: expected flush after ref listing

# answer:
git config --global http.postBuffer 5242880000

# 问题五 :可能会出现maven下载包相关的错误
# answer ：
建议直接apt install maven 下载 默认地址，尽量不要包下载


