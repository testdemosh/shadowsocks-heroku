# shadowsocks-heroku
[Heroku](https://www.heroku.com/) 是一个支持多种编程语言的云平台即服务，shadowsocks-heroku 则是可部署在 Heroku 平台的ss服务。
和 [shadowsocks](https://github.com/clowwindy/shadowsocks) 不同的是 shadowsocks-heroku 使用的 WebSocket 代替原本的 sockets。

### 准备
#### 1.注册 Heroku 帐号
Heroku 提供免费账号，具体限制如下：
- Run apps for free using your monthly pool of free dyno hours
- Unverified accounts: receive a pool of 550 free dyno hours
- Verified accounts: receive an additional 450 free dyno hours
- Dyno hours can be shared across any of your free apps
- 1 web dyno/1 worker dyno/1 one-off dyno maximum per app
- 512 MB RAM per dyno
- Free apps sleep automatically after 30 mins of inactivity to conserve your dyno hours
- Free apps wake automatically when a web request is received
- Access to the Heroku Dashboard and Heroku CLI for app management
- Custom domains for every free app (with verified account)
- Up to 5 free apps (unverified) or 100 (verified)

用作 VPS 是够了，注册地址：https://signup.heroku.com/

#### 2.Fork本项目
Fork 本项目到个人账号下
![](https://github.com/521xueweihan/shadowsocks-heroku/blob/master/img/4-min.png)

### 部署
heroku 在创建项目的时候可以，通过关联 GitHub 账号，直接部署 GitHub 账号下的项目。具体步骤如下：

1. 登陆 Heroku 帐号，后进入 Dashboard ——> Create New App ——> 输入 App Name
2. 完成上一步后，会跳转到 Deploy 页面，找到 Deployment method 选择 GitHub 关联上自己的 GitHub 帐号。
3. 关联上 shadowsocks-heroku 项目，如下图所示：
    ![](https://github.com/521xueweihan/shadowsocks-heroku/blob/master/img/1-min.png)
4. 点击 Deploy Branch，部署成功如下图：
    ![](https://github.com/521xueweihan/shadowsocks-heroku/blob/master/img/2-min.png)

### 设置加密算法和密码
Setting 页面 ——> Reveal Config Vars，设置参数如下图：
![](https://github.com/521xueweihan/shadowsocks-heroku/blob/master/img/3-min.png)

### 启动本地 client：
1. **进到本项目目录**，执行`npm install` 命令，安装依赖的库
2. 启动本地 client，`node local.js -s 你的app名称.herokuapp.com -l 1080 -m 设置的加密算法 -k 设置的密码 -r 80`

### 最后
设置浏览器代理：
```
SOCKS5 127.0.0.1:1080
```
推荐 Chrome 插件——SwitchyOmega，[教程](https://github.com/XX-net/XX-Net/wiki/%E4%BD%BF%E7%94%A8Chrome%E6%B5%8F%E8%A7%88%E5%99%A8#%E6%96%B9%E6%A1%88%E4%BA%8C%E5%AE%89%E8%A3%85%E5%92%8C%E4%BD%BF%E7%94%A8%E4%BB%A3%E7%90%86%E5%88%87%E6%8D%A2%E6%8F%92%E4%BB%B6)

### 支持的加密算法
- rc4
- rc4-md5
- table
- bf-cfb
- des-cfb
- rc2-cfb
- idea-cfb
- seed-cfb
- cast5-cfb
- aes-128-cfb
- aes-192-cfb
- aes-256-cfb
- camellia-256-cfb
- camellia-192-cfb
- camellia-128-cfb
