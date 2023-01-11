---
home: true
tagline:
---

::: warning
使用前必看：[内网穿透基础知识](/basics)
:::

## 字形注意

所有命令建议复制使用，如果要自行输入，请注意区分 `0` (数字) 和 `O` (大写字母) 和 `o` (小写字母)。

## 关于首页到处乱飞的文档链接有四个关闭按钮这件事

只有右下角那个是永久关闭，您也可以设置 `localStorage.close_rtfm_alert = '20220119'` 手动关闭。

@include(./faq.md)

## 文档快速索引 {#quick-index}

::: tip
本文档内容丰富，此处索引只列出了一小部分内容，请善用搜索功能
:::

- [frpc Linux/macOS/Docker 基本使用指南](/frpc/usage) | [Linux 开机自启](/frpc/service/systemd)

- [Windows 使用](/launcher/usage) | [Windows XP/Vista/Server 2003](/geek#compatibility)

- NAS 相关教程: [群晖 DSM](/app/synology) | [威联通 QNAP](/app/qnap)

- 其他常见应用: [映射网页应用](/app/http) | [远程桌面](/app/rdp) | [远程开机](/app/wol)

## 文档使用指南 {#how-to-use}

- 在左侧列表中根据目录查看对应内容
- 在顶部搜索框中输入关键字、报错信息等内容查询

![](./_images/index-1.png)

## 重要提示 {#important-note}

本文档中所有 **必须参数** 使用 `<>` 标出，所有 **可选参数** 使用 `[]` 标出，多个可选项使用 `|` 分开。

在实际操作时 **不需要** 输入 `<>` 和 `[]`，当碰到 `|` 分开的选项时只能选择其中 **任意一个** 输入。

1. 例如文档中写道:

   ```ini
   force_https = <Int>
   ```

   您准备将 `force_https` 选项设置为 `302`，则 **应该** 输入:

   ```ini
   force_https = 302
   ```

   而 **不应该** 输入:

   ```ini
   force_https = <302>
   ```

2. 例如文档中写道:

   ```bash
   # 执行
   service frpc <restart|start>
   ```

   您准备执行该命令，则 **应该** 使用:

   ```bash
   service frpc restart
   # 或
   service frpc start
   ```

   而 **不应该** 使用:

   ```bash
   service frpc restart|start
   ```

---

本文档使用 Github Pages 服务托管，[点我前往托管仓库](https://github.com/natfrp/wiki)。

---

## 交流群 {#community}

### QQ 水群 {#community-qq}

- 群号: 1036050697 ( 已满员 ), 766865191, 1011690081
- 入群问题不是摆设, 你不好好填是不会让你进的
- 非官方群, 群内没有网站管理员

### 社区论坛 {#community-forum}

- [点击访问 SakuraFrp BBS](https://www.natfrpbbs.com)
- **非官方论坛**，由社区人员管理

### 其他 IM 水群 {#community-other-im}

- [Telegram](https://t.me/natfrp_unofficial)
- [Matrix](https://matrix.to/#/!GFWDTqltQmjaSCDGij:atunemic.cn?via=atunemic.cn&via=t2bot.io)
- 非官方群, 群内没有网站管理员

### VIP 反馈群 {#community-vip}

请前往 [用户信息](https://www.natfrp.com/user/profile) 页面查看详情。