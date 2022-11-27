<a id="running-frpc"></a>使用 frpc 前，请先 [查看您的访问密钥](#get-token)。您可以通过下列方式启动 frpc：

| 启动方式 | 说明 |
| --- | --- |
| [TUI](#tui-usage) | 易于上手，适合不熟悉命令行的新手用户 |
| [命令行](#cli-usage) | 支持更复杂的配置，适合高级用户 |

### 查看访问密钥 :id=get-token

本文档所提到的 **访问密钥**（有时也叫 **Token**）是专门用于客户端（启动器、frpc）登录的一个 **专用密码**，与您的账户登录密码 **不同**。

!> 请妥善保管您的访问密钥，截图时注意打码。若访问密钥不慎泄露，请尽快到 [用户信息](https://www.natfrp.com/user/profile) 界面进行重置

您可以在 [管理面板](https://www.natfrp.com/user/) 点击 **查看访问密钥** 按钮查看并复制访问密钥：

![](_images/get-token.png)

本文档通常使用 `wdnmdtoken6666666` 作为示例密钥，实际操作时请将其替换为您自己的访问密钥。

### 通过 TUI 启动隧道 :id=tui-usage

在 `frpc.ini` 不存在的情况下，不带参数直接运行 frpc 会打开 TUI（文本图形界面）。

在 **Token** 后面的文本框内输入访问密钥，然后使用 `Tab` 键切换到 **Login** 按钮并按 `回车` 键登录 (若终端支持也可使用鼠标进行操作)：

![](_images/tui-0.png)

登录成功后 TUI 会显示当前账户下的隧道列表，使用方向键选中想要启动的隧道，按空格标为绿色 (或使用鼠标直接点击隧道)：

?> 可以一次性启用多个隧道，您也可以直接选中节点来启用该节点下的所有隧道

![](_images/tui-1.png)

选择完毕后，按 `Ctrl-C` 即可启动隧道，相关启动参数会被保存到配置文件 `frpc.ini` 中，下次不带参数直接运行 frpc 时不再显示 TUI 而是直接启动隧道：

?> 自 `v0.42.0-sakura-3` 版本起，启动时若不带参数 且 `frpc.ini` 存在，您会看到 `正在使用配置文件运行，在 3 秒内按任意键进入配置模式` 的提示。按下任意按键即可进入配置界面，否则 frpc 会自动加载 `frpc.ini` 并启动里面保存的隧道

![](_images/tui-2.png)

### 通过命令行启动隧道 :id=cli-usage

#### 从面板获取启动参数 :id=view-startup-parameter

要获取启动参数，最简单的方法就是在管理面板中直接查看了。点击隧道操作中的 **配置文件** 选项即可进行查看：

![](_images/view-startup-parameter-1.png)

如果要同时启动多条隧道，先勾选要启动的隧道再点击 **批量操作** 中的 **配置文件** 选项：

![](_images/view-startup-parameter-2.png)

弹出对话框后，如图所示复制启动参数并粘贴到 `frpc ` 命令后面即可，注意中间要用空格分开。

![](_images/view-startup-parameter-3.png)

在上面这个例子中，我们启动隧道的命令就是：

```bash
frpc -f wdnmdtoken6666666:114514,114516
#   ^
# 注意这里有一个空格
```

#### 启动参数格式 :id=startup-parameter

!> 如果您没有按照 **基本使用指南** 安装 frpc，或您使用的是 Windows 系统，启动时要把 "frpc" 换成下载到的的文件名，例如 `frpc_windows_386.exe`、`./frpc_linux_amd64`

frpc 支持通过 ID 启动单条或多条隧道，也可以直接开启位于某个节点的所有隧道。旧版 frpc 同时启动多条隧道时，这些隧道必须位于同一节点，新版 frpc 无此限制，详见 [常见问题-一个 frpc 可以连接多条隧道吗](/faq/frpc#frpc-connect-to-multiple-tunnels)。

启动参数的格式如下：

```bash
frpc -f <访问密钥>:<启动目标1>[,启动目标2[,启动目标3...]]
```

多个 **启动目标** 使用半角逗号 "," 分开，中间不能有空格或其他字符。每个 **启动目标** 可以是一个隧道 ID（如 `123456`）或是 `n` 前缀加上节点 ID（如 `n233`）。

#### 使用举例 :id=cli-example

假设您使用的是 Linux 系统，且已跟随文档正确安装了 frpc，您的隧道列表如下图所示：

![](_images/tunnel-list.png)

- 启动第一条 **隧道 ID** 为 `114514` 的隧道：
  ```bash
  frpc -f wdnmdtoken666666:114514
  ```

- 启动 **#29 圣何塞CUVIP** 节点下的所有隧道，则有两种方法：
  ```bash
  # 直接使用节点 ID
  frpc -f wdnmdtoken666666:n29

  # 一个个输隧道 ID
  frpc -f wdnmdtoken666666:114514,114515
  ```

- 启动图中的所有隧道
  ```bash
  # 使用节点 ID
  frpc -f wdnmdtoken666666:n20,n29

  # 一个个输隧道 ID
  frpc -f wdnmdtoken666666:114514,114515,114516

  # 混着用也可以
  frpc -f wdnmdtoken666666:n29,114516
  ```

### 进阶使用 :id=advanced

这是一篇适合绝大多数用户的简明使用教程，因此文中省略了很多特性和配置说明。

如果您是高级用户，您还可以在 [用户手册](/frpc/manual) 获取更多关于 frpc 的信息，例如命令行开关和配置文件细则。