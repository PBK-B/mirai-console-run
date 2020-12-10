# mirai-console-run Project

> 基于目前 Github 最火的机器人 mirai 搭建相关服务，提供 Linux 基础集成库

### 环境 🚕

> JDK 8.0 或以上

> PHP 7.0 或以上

> Linux Screen 4.0.0 或以上

### 部署 🐻

- 拉取仓库代码

```
git clone https://github.com/PBK-B/mirai-console-run.git
```

- 初次运行生成 config 文件夹和 yml 配置文件，执行 login 测试 QQ 是否能够正常登陆

```
# 赋予可执行权限
sudo chmod +x ./run.sh

# 执行脚本
sh ./run.sh

# 在窗口中测试 QQ 登陆
login QQ账号 QQ密码

```

- 登陆成功后，结束程序运行。配置 `config/Console/AutoLogin.yml` 自动登陆配置文件

```
plainPasswords:
  QQ账号: QQ密码
```

> 想要安全点的话可以配置 MD5 密码，md5Passwords 字段格式相同

- 修改 `config/MiraiApiHttp/setting.yml` 文件中 `port` 端口为 `9923`，`enableWebsocket` 字段配置为 `true`。

- 修改 `scripts/index.php` 中 `$bot_qq` 为 QQ 账号，`$bot_authKey` 为 `config/MiraiApiHttp/setting.yml` 文件中 `authKey` 字段

- 使用 screen 开启一个后台任务

```
# 启动 screen 任务
screen -R qq_bot_server

# 进入仓库目录
cd mirai-console-run

# 运行 QQ Bot Server 服务
sh ./run.sh

```

- 新开一个 screen 后台任务，执行 `scripts/index.php` 脚本。

```
# 启动 screen 任务
screen -R bot_movie

# 进入仓库目录
cd mirai-console-run

# 运行脚本
php scripts/index.php
```

### 开发 🍅

- `config` mirai 插件配置文件夹
- `data` mirai 文件缓存文件夹
- `http_api` php 脚本程序或提供 api 的代码（主要开发目录）
- `libs` mirai 程序目录
- `logs` mirai 运行 log 文件夹
- `plugins` mirai 插件安装文件夹
- `run.sh` mirai 启动脚本

### 相关链接 🏈

- 高效率 QQ 机器人框架 <https://github.com/mamoe/mirai>

- Mirai HTTP API (console) plugin <https://github.com/project-mirai/mirai-api-http>

- mirai 的高效率 QQ 机器人控制台 <https://github.com/mamoe/mirai-console>
