# linux_clash

[here](https://github.com/yangzijia/linux_clash/wiki/ubuntu-server-%E5%9C%A8terminal%E4%B8%8B%E9%85%8D%E7%BD%AE%E7%A7%91%E5%AD%A6%E4%B8%8A%E7%BD%91)

# Linux 翻墙教程 2026-0425

来源：fanqiang.gitbook.io/fanqiang/linux

## 一、创建并进入程序目录

```bash
mkdir ~/.config/

mkdir ~/.config/mihomo/

cd ~/.config/mihomo/
```

## 二、下载最新版本 Clash (mihomo)

wget -O clash-linux.gz https://github.com/MetaCubeX/mihomo/releases/download/v1.17.0/mihomo-linux-amd64-v1.17.0.gz

根据你的 Linux 版本选择相应的下载，一般下载 linux-amd64 版本即可。如果 wget 下载不了，就用浏览器手工下载。
如果用浏览器下载，下载后移动文件到 ~/.config/mihomo/ 并改名为 clash-linux.gz。

## 三、初始化并生成配置文件

```shell
gzip -f clash-linux.gz -d

chmod +x clash-linux

./clash-linux
```

等几分钟，然后按 Ctrl+C 退出 clash 程序。

初始化执行 clash 会默认在 ~/.config/mihomo/ 目录下生成配置文件和全球 IP 地址库：

```shell
config.yaml
Country.mmdb
GeoSite.dat
```

## 四、手工下载缺失文件（如需要）

```shell
Country.mmdb
https://github.com/Dreamacro/maxmind-geoip/releases/latest/download/Country.mmdb
```

GeoSite.dat

手工下载 GeoSite.dat 后放到 ~/.config/mihomo/ 目录。

## 五、下载 Clash 配置文件（更新订阅更新节点）

```shell
wget -U "Mozilla/6.0" -O ~/.config/mihomo/config.yaml "你的Clash订阅链接网址"
```

重复执行就是更新订阅更新节点

`说明`

- 下面的 wget 命令后面的 你的Clash订阅链接网址，用你的机场的实际的 clash 订阅链接替换。
- 当然，你也可以用浏览器打开订阅链接，下载后拷贝或移动到 ~/.config/mihomo/ 目录替换覆盖 config.yaml 文件。
- 机场节点信息可能会不定时更新，若出现大面积节点不可用现象，或者从免费用户升级为 VIP 用户，请手工更新订阅更新节点。

## 六、配置 Linux / 浏览器使用 Clash 代理（以 Ubuntu 为例）

同时启用 HTTP 代理和 Socks5 代理。

Clash 默认 HTTP 和 Socks5 端口都默认监听 7890。

配置 HTTP 代理和 Socket 代理分别为上面的端口号。

⚠️ 注意：Linux 命令行的程序或 shell 脚本不一定遵循此处代理设置，设置命令行的代理请看后文。

## 七、Linux 命令行设置代理

```shell
export http_proxy="http://127.0.0.1:7890"
export https_proxy="http://127.0.0.1:7890"
```

验证代理是否设置成功：

```shell
echo $http_proxy
echo $https_proxy
```

⚠️ 注意：ping 不支持代理，命令行测试外网网址请使用 curl 测试。
取消代理

```shell
unset http_proxy
unset https_proxy
```

## 八、常用命令

```shell
# 解压
gzip -f clash-linux.gz -d

# 添加执行权限
chmod +x clash-linux

# 查看目录文件
ls -rtl ~/.config/mihomo/

# 更新订阅
wget -U "Mozilla/6.0" -O ~/.config/mihomo/config.yaml "你的Clash订阅链接网址"
```
