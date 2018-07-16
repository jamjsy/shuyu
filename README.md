# shuyu


## 建立库

使用 hugo new site mysite 就可以建一个库

## 创建README.md

注册一个GitHub账号，建立一个新的仓库，建立时勾选README.md 

## 创建一个hugo博客

在hugo上挑选一个喜欢的主题，将其克隆到本地themes中

## 创建dockerfile

在本地的仓库里创建一个dockerfile文件

FROM registry.saas.hand-china.com/tools/debian:jessie 

COPY mysite/ /myblog/

ADD hugo_0.44_Linux-64bit.deb /tmp/hugo.deb

RUN dpkg -i /tmp/hugo.deb \ 
	&& rm /tmp/hugo.deb

WORKDIR myblog/

CMD hugo

CMD  hugo server --baseUrl=192.168.99.100 --bind=0.0.0.0

EXPOSE 1313

## build.sh

创建一个build.sh 文件

docker build -t mysite:v1.0 .

## run.sh

创建一个run.sh 文件

docker run -d -p 1313:1313 --name=mysite mysite:v1.0 

然后将本地的仓库push到远程的GitHub上