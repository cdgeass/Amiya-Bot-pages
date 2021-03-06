---
title: 如何维护
---

::: tip <br>
推荐使用 [Amiya-Bot-console](https://github.com/AmiyaBot/Amiya-Bot-console) 获得更好的可视化维护界面，否则部分数据维护需要手动编辑数据库<br>
使用方法请阅读 [说明文档](/docs/amiyaConsole/)
:::

- Amiya 带有 `自动维护` 功能，会在每天凌晨4点执行以下操作：
    - 重置所有用户的签到状态和心情值
    - 清空一定时间前的历史消息及图片 ID 记录
    - 清除本地缓存<br>
      ::: warning <br>
      如果你的 Amiya 因为某些原因错过了维护时间，你可能需要进行手动维护。<br>
      方法是：私聊 Amiya 发送 `手动维护`
      :::
- Amiya 在每次启动时都会执行 `更新检查`。如需更新则会下载新数据和图片资源，请保持良好的网络环境下启动。<br>
  ::: warning <br>
  Amiya 会在更新时对下载失败但不影响运行的资源作忽略处理，在第二次启动时跳过下载。如果重要的资源被忽略，请私聊 Amiya 发送`强制更新` 重新检查资源。
  :::
- 自然语言处理方法和公招图像识别需要调用 [百度智能云](https://cloud.baidu.com/)的接口，如需使用请自行申请并配置

```yaml
baiduCloud:
    enable: true
    appId: 21*****7
    apiKey: MM************GnL5
    secretKey: XR*********************U7UM
```

- 为了防止某个指令会导致 Amiya 与其他机器人互相触发关键词导致恶性死循环，造成不可控的刷屏局面，**请务必设置消息限制**，在与其他机器人触发循环时及时制止

```yaml
# 10 秒内最多响应 3 次指令
message:
    limit:
        seconds: 10
        maxCount: 3
```

- 部分配置改动后需重启 Amiya 生效
