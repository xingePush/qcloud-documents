## 操作场景

若您的 DNS 服务器不正确，需将域名 DNS 修改为提示的 DNS 地址，解析方可生效。

## 操作步骤

### 查看 DNS 服务器
您可以通过以下步骤查看 DNS 服务器是否正确：
1. 登录 [腾讯云控制台](https://console.cloud.tencent.com/)，选择 “云产品 > 域名与网站 > 云解析”，进入 “域名解析列表” 页面。
2. 选择需要查看的域名，进入该域名的管理页面。
3. 选择 “记录管理” 页签。若存在如下提示，说明 DNS 服务器不正确。如下图所示：
![1](https://main.qcloudimg.com/raw/1334ffff245ca5ecebea8521d6df5d65.png)
>!不同解析套餐对应的 DNS 地址不同，请根据提示来修改。

### 腾讯云注册域名修改 DNS
如果域名在腾讯云注册，或者已转入腾讯云，可以通过以下步骤修改 DNS 服务器：
1. 登录 [腾讯云控制台](https://console.cloud.tencent.com/)，选择 “云产品 > 域名与网站 > 域名管理”，进入 “域名管理” 页面。
2. 选择待修改 DNS 的域名，单击【管理】。如下图所示：
![2](https://main.qcloudimg.com/raw/b13507067276aca1db2f7ba81394e1c6.png)
3. 在 “基本信息” 栏中，单击 “DNS 服务器” 的【修改】。如下图所示：
![3](https://main.qcloudimg.com/raw/88639b803510ea036620b6ed7f58b0d8.png)
4. 在弹出的 “修改 DNS 服务器” 窗口中，填写指定的 DNS 服务器地址，单击【提交】，完成修改。
![4](https://main.qcloudimg.com/raw/7660182fc679028ed428d0564e1d8d89.png)

>?如果域名在其他注册商处管理，您需要前往域名注册商提供的域名管理页面，修改为指定的域名 DNS。
下面以阿里云（万网）、GoDaddy 为例说明修改方法。

### 阿里云（万网）注册商域名修改 DNS
1. 选择需要在腾讯云进行解析的域名，进入域名管理页的【DNS 修改/创建】，单击【修改域名 DNS】；
![](https://main.qcloudimg.com/raw/139975c769f43867a53c70b3ae2fc6ad.png)
2. 分别填写 f1g1ns1.dnspod.net，f1g1ns2.dnspod.net，保存后最长等待 72 小时可以全球生效。
![](https://main.qcloudimg.com/raw/1694dd7391aa85140f654ee7db90ebe0.png)

### GoDaddy 注册商域名修改 DNS
1. 登录 [GoDaddy](http://www.godaddy.com) 后单击【DOMAINS】的【Manage】。
![gd1](https://main.qcloudimg.com/raw/2ca1a9c4c5a5f4513c7b2ff419582f5f.png)
2. 在域名列表中找到要修改要修改 DNS 的域名，然后单击该域名下拉列表中的 【Set NameServers】。
![gd2](https://main.qcloudimg.com/raw/c2bba72ee7f8afc445d84327229518e8.png)
3. 选择【Custom】，再单击左下角的【Add Nameserver】。
![gd3](https://main.qcloudimg.com/raw/66cdd937d1e94d0e87f5adbd413dd221.png)
4. 分别输入 f1g1ns1.dnspod.net、f1g1ns2.dnspod.net，然后单击【Add Nameserver】，再单击【Save】，等待全球递归 DNS 服务器刷新（最多72小时）。
![gd4](https://main.qcloudimg.com/raw/ec7b82d7b0080932246a65480680c1b8.png)
![gd5](https://main.qcloudimg.com/raw/c2473a10face5bbd1524283bde65b08c.png)

