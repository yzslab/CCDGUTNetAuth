# CCDGUTNetAuth
![#f03c15](https://placehold.it/15/f03c15/000000?text=+) **★ 声明：本项目的创建者与一切销售或推广网络设备的人员无任何合作关系，且不销售或推广任何相关设备，以前没有，目前没有，未来也不会有。**

本Shell Script可用于东莞城院校园网账号的自动认证（注意非天翼认证）

需要自动进行天翼认证的，可以参考此项目：[zte-client](https://github.com/yzslab/zte-client)

# 0. 另一个可参考的方案：SmartCCDGUTPHPClient
```
./SmartCCDGUT ccdgutAutoAuth USERNAME # e.g.: ./SmartCCDGUT ccdgutAutoAuth 201535000000
# or manually specific IP address
./SmartCCDGUT ccdgutAuth USERNAME IP # e.g.: ./SmartCCDGUT ccdgutAuth 201535000000 10.20.0.0
```
以上命令可以调用智慧城院APP的API进行认证，通过“ccdgutAuth”似乎可以无需任何身份认证登录任意账号，具体的API调用方式，见：[SmartCCDGUTPHPClient](https://github.com/yzslab/SmartCCDGUTPHPClient)

# 1. 使用
## 1.1. 环境准备
Shell Script是在bash下测试的，不保证busybox ash可以运行，建议安装bash。

此外，还用到curl；如果需要后台运行，请安装nohup。
#### 1.1.1. OpenWRT可执行以下命令安装所需程序
```
opkg update
opkg install bash coreutils-nohup curl
```
## 1.2. 获取Shell Script
```
curl -k https://raw.githubusercontent.com/yzslab/CCDGUTNetAuth/master/ccdgut-auth > /usr/bin/ccdgut-auth
chmod +x /usr/bin/ccdgut-auth
```
## 1.3. 运行
参数一为学号，参数二为密码：
```
ccdgut-auth 学号 密码
```
后台运行：
```
nohup ccdgut-auth 学号 密码 > /dev/null 2>&1 &
```
## 1.4 自定义认证URL前缀
```
url_prefix="http://YOUR_HTTP_HOST" ccdgut-auth 学号 密码
```
