---
title: 在Mac上设置密钥(SSH KEY)登录Linux
date: 2019-03-09 19:30:00
tags: Mac使用优化
---

Linux服务器，输入以下命令：
``` bash
lastb | less
```
你会看到非常多的类似以下的记录：

{% asset_img hacking.png "blogs image" %}

这些都是在不停尝试登陆你服务器的记录；

### 生成秘钥
使用ssh-keygen生成，输入以下命令：
``` bash
ssh-keygen -t rsa
```
运行结果：
```
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/bstardev/.ssh/id_rsa): 
/Users/bstardev/.ssh/id_rsa already exists.
Overwrite (y/n)? y
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in ~/.ssh/id_rsa.
Your public key has been saved in ~/.ssh/id_rsa.pub.
```
其中id_rsa是私钥，id_rsa.pub是公钥，分别保存以备用。

### 上传生成的公钥

登陆需要配置密钥登陆的服务器，将公钥内容填入~/.ssh/authorized_keys文件中：

``` bash
cd ~/.ssh/
vi authorized_keys
```
保存后，对.ssh目录和其中的authorized_keys公钥文件设置相应的权限：

``` bash
chown -R 0700  ~/.ssh
chown -R 0644  ~/.ssh/authorized_keys
```

### 配置ssh服务以使用密钥登陆

接着修改ssh配置文件：
``` bash
vi /etc/ssh/sshd_config
```
对以下内容去掉注释：

``` bash
StrictModes no
RSAAuthentication yes 
PubkeyAuthentication yes 
AuthorizedKeysFile    .ssh/authorized_keys
PasswordAuthentication no
```
保存后重启sshd服务：

``` bash
systemctl restart sshd
```
退出重新登陆服务器，这次使用密钥登陆，测试是否成功。

这样就完成了密钥登陆的配置。

