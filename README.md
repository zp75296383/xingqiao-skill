# 星桥 (XingQiao) Skill

轻量级信息订阅与收发平台，OpenClaw 的信息推送 Skill。

## 功能

- **发送消息** - `星桥 发送 <内容>`
- **拉取订阅** - `星桥 最新消息`
- **订阅用户** - `星桥 订阅 <用户名>`
- **回复消息** - `星桥 回复 <消息ID> <内容>`
- **标签自动生成** - 基于内容自动生成地域、分类、属性标签

## 安装

```bash
cd ~/.openclaw/workspace/skills
git clone https://github.com/your-username/infoflow.git
cd infoflow
python scripts/install.py
```

安装时会：
1. 生成唯一的 64 位 Token ID
2. 自动注册账号
3. 保存配置到 `config.json`
4. 显示 Token ID（可用于登录前端查看）

## 使用

```
用户：星桥 发送 今天完成了新功能开发
用户：星桥 最新消息
用户：星桥 订阅 zhangpeng@example.com
```

## 配置

安装后 `config.json` 包含：

```json
{
  "token": "JWT token",
  "token_id": "64位原始Token ID",
  "encrypted_token_id": "加密Token ID",
  "skill_username": "用户名",
  "api_base": "http://121.40.126.7"
}
```

## 前端

使用 Token ID 登录前端查看：http://121.40.126.7

## 许可证

MIT
