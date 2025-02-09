## 操作场景
Ghost 是使用 Node.js 语言编写的开源博客平台，您可使用 Ghost 快速搭建博客，简化在线出版过程。本文档以 Ubuntu 18.04 的 Linux 操作系统的腾讯云云服务器（CVM）为例，手动搭建 Ghost 个人网站。

## 技能要求
进行 Ghost 网站搭建，您需要熟悉 Liunx 操作系统及命令，例如 [CentOS 环境下通过 YUM 安装软件](https://cloud.tencent.com/document/product/213/2046) 等常用命令。


## 前提条件
- 已购买 Linux 云服务器。如果您还未购买云服务器，请参考 [创建实例](https://cloud.tencent.com/document/product/213/4855)。
- 已登录 Linux 云服务器。如果您还未登录，请准备好云服务器的登录密码及公网 IP，参考 [使用标准方式登录 Linux 实例](https://cloud.tencent.com/document/product/213/5436) 完成登录。
- 请通过腾讯域名注册购买域名，并通过 [云解析](https://cloud.tencent.com/product/cns) 服务解析域名。


## 操作步骤
当您登录 Ubuntu 操作系统的云服务器后，需切换 root 用户身份，详情请参考 [Ubuntu 系统使用 root 用户登录](https://cloud.tencent.com/document/product/213/17278#ubuntu-.E7.B3.BB.E7.BB.9F.E5.A6.82.E4.BD.95.E4.BD.BF.E7.94.A8-root-.E7.94.A8.E6.88.B7.E7.99.BB.E5.BD.95.E5.AE.9E.E4.BE.8B.EF.BC.9F)。
### 创建新用户
1. 执行以下命令，创建新用户。本文以 `user` 为例。
>!请勿使用 `ghost` 作为用户名，会导致与 Ghost-CLI 发生冲突。 
>
```
adduser user
```
 1. 请按照提示输入并确认用户密码，密码默认不显示，输入完成后按 “**Enter**” 进入下一步。
 2. 根据您的实际情况填写用户相关信息，可默认不填写，按 “**Enter**” 进行下一步。
 3. 输入 “**Y**” 确认信息，并按 “**Enter**” 完成设置。如下图所示：
 ![](https://main.qcloudimg.com/raw/66ca399607b89f2653668eb4b0cb71f5.png)
2. 执行以下命令，增加用户权限。
```
usermod -aG sudo user
```
3. 执行以下命令，切换 `user` 登录。
```
su user
```

### 更新安装包
依次执行以下命令，更新安装包。
>?请按照界面上的提示输入 `user` 的密码，并按 “**Enter**” 开始更新。
>
```
sudo apt-get update
sudo apt-get upgrade -y
```

### 环境搭建
#### 安装配置 Nginx
执行以下命令，安装 Nginx。
```
sudo apt-get install -y nginx 
```

#### 安装配置 MySQL
1. 执行以下命令，安装 MySQL。
```
sudo apt-get install -y mysql-server 
```
2. 执行以下命令，连接 MySQL。
```
sudo mysql
```
3. <span id="database"></span>执行以下命令，创建 Ghost 使用的数据库。本文以 `ghost_data` 为例。
```
CREATE DATABASE ghost_data;
```
4. <span id="sercet"></span>执行以下命令，设置 root 帐户密码。
```
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '输入root帐户密码';
```
5. 执行以下命令，退出 MySQL。
```
\q
```

#### 安装配置 Node.js
1. 执行以下命令，添加 Node.js 支持的安装版本。
```
curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash
```
2. 执行以下命令，安装 Node.js。
```
sudo apt-get install -y nodejs
```

#### 安装 Ghost-CLI
执行以下命令，安装 Ghost 命令行工具，以便快速配置 Ghost。
```
sudo npm install ghost-cli@latest -g
```

### 安装配置 Ghost
1. 依次执行以下命令，设置 Ghost 安装目录。
```
sudo mkdir -p /var/www/ghost
sudo chown user:user /var/www/ghost
sudo chmod 775 /var/www/ghost
cd /var/www/ghost
```
2. 执行以下命令，运行安装程序。
```
ghost install
```
3. 安装过程中需要进行相关配置，请参考界面及以下提示完成配置。如下图所示：
![](https://main.qcloudimg.com/raw/6c3a3b9d083dfb253285f47d81e928b5.png)
 1. **Enter your blog URL**：输入已解析的域名。
 2. **Enter your MySQL  hostname**：输入数据库连接地址，请输入 `localhost` 后按 “Enter”。
 3. **Enter your MySQL username**：输入数据库用户名，请输入 `root` 后按 “Enter”。
 4. **Enter your MySQL password**：输入数据库密码，请输入在 [设置 root 帐户密码](#sercet) 中已设置的密码后按 “Enter”。
 5. **Enter your database name**：输入 Ghost 使用的数据库，请输入在 [创建数据库](#database) 中已创建的 `ghost_data` 后按 “Enter” 。
 后续设置请结合实际情况输入 “Y” 确认或 “n” 否认来完成配置。完成设置后，界面下方会输出 Ghost 的管理员访问地址。
4. 使用浏览器访问 Ghost 的管理员访问地址，开始个人博客配置。如下图所示：
单击【Create your account】开始创建管理员账户。
![](https://main.qcloudimg.com/raw/8cd0a5b93a299e8d3b9faa5f813e23a6.png)
5. 输入相关信息，并单击【Last setp】。如下图所示：
![](https://main.qcloudimg.com/raw/b74067914e25a8d60592aee9a2abf158.png)
6. 可邀请他人一起参与博客创建，也可跳过此步骤。
7. 进入管理界面后，即可开始管理博客。如下图所示：
![](https://main.qcloudimg.com/raw/d69feb2f695922773616578b0eb887a4.png)
配置完成后，访问 `www.xxxxxxxx.xx` 域名即可看到个人博客主页。如下图所示：
![](https://main.qcloudimg.com/raw/cfdd18b0ab2fa07e46658d0b502d4ea3.png)

 
 
