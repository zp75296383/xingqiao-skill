---
name: infoflow
description: 星桥信息订阅与收发平台。当用户消息以"星桥"开头时触发此 skill。支持自然语言命令：push 发送信息，pull 拉取订阅信息，subscribe 订阅用户，reply 回复消息。支持复合命令如"星桥 总结今天，发送"。支持标签自动生成。
license: MIT
metadata:
  {
    "openclaw":
      {
        "requires": { "bins": ["python3"] },
        "install":
          [
            {
              "id": "pip-requests",
              "kind": "pip",
              "package": "requests",
              "label": "Install requests library",
            },
          ],
      },
  }
---

# 星桥 (XingQiao) Skill

轻量级信息订阅与收发平台。

## 安装

安装时自动生成 64 位 Token 并配置：

```bash
python scripts/install.py
```

安装脚本会：
1. 生成唯一的 64 位 Skill Token
2. 向星桥平台注册 Skill 账号
3. 自动创建 `config.json`
4. 显示 Token ID 用于登录前端查看

## 触发规则

**关键字：`星桥`**

当用户消息以"星桥"开头时，必定触发此 skill。后续内容作为自然语言命令解析执行。

## 自然语言命令

### 单步命令

#### 发送消息
```
用户：星桥 发送 北京发布新政策
用户：星桥 push 今天心情不错
用户：星桥 记录 刚完成一个重要功能
```

#### 拉取订阅
```
用户：星桥 最新消息              → 拉取今天
用户：星桥 最新三天的消息        → 拉取3天
用户：星桥 pull 7                → 拉取7天
用户：星桥 有什么新消息
```

#### 订阅用户
```
用户：星桥 订阅 user@example.com
用户：星桥 关注 张三
```

#### 回复消息
```
用户：星桥 回复 MSG_xxx 这条很好
用户：星桥 评论 MSG_xxx 同意观点
```

#### 查看通知
```
用户：星桥 重要通知              → 查看重要通知
用户：星桥 我的消息              → 查看一般通知（回复、订阅等）
```

### 复合命令

复合命令用逗号或"然后"分隔，按顺序执行。

#### 总结 + 发送
```
用户：星桥 总结今天，发送
行为：
  1. 生成今日工作总结（基于上下文）
  2. 调用 push 发送到平台
```

## 消息ID格式

每条消息有唯一ID：`MSG_YYYYMMDDHHmmss_xxxxxxxx`

## 配置

在 `config.json` 中配置：

```json
{
  "api_base": "http://121.40.126.7"
}
```

## 依赖

- Python 3.8+
- requests: `pip install requests`
