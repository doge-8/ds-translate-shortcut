# ds-translate-shortcut

iOS 快捷指令：双击手机背面，用 DeepSeek 翻译选中的文字。中文译成英文，其他语言译成简体中文。

## 安装

**[点这里添加快捷指令](https://www.icloud.com/shortcuts/6bf7f6aa8d77431abcb7b3ba9c579d76)**

也可以下载本仓库的 [`ds-translate.shortcut`](ds-translate.shortcut) 导入。这个文件的 Apple 签名在 2027-11-30 到期。

## 设置

1. 到 [DeepSeek 开放平台](https://platform.deepseek.com/) 创建 API Key。
2. 在「快捷指令」App 里编辑这个捷径，找到「获取 URL 内容」的请求头，把 `Authorization` 的值改成你自己的 Key，保留前面的 `Bearer `：

   ```
   Bearer sk-你的api
   ```

3. 打开 iPhone 的「设置 → 辅助功能 → 触控 → 轻点背面 → 轻点两下」，选择这个捷径。

> 填入 Key 后不要再分享这个捷径，否则别人能直接用你的额度。

## 使用

选中文字，双击手机背面。如果没有选中文字，就翻译剪贴板里的内容。

结果会同时显示原文和译文，译文会自动复制到剪贴板。

## 翻译规则

| 原文 | 译成 |
|---|---|
| 简体或繁体中文 | 英文 |
| 其他语言（包括日文、韩文） | 简体中文 |
| 中英混合 | 按中文占比判断 |
| 含平假名或片假名 | 视为日文 |

只输出译文，不带解释、引号或原文。

## 工作原理

向 `https://api.deepseek.com/chat/completions` 发送请求，模型为 `deepseek-flash`，并关闭思考模式以加快响应。系统提示词和完整动作可以在 [`ds-translate.plist`](ds-translate.plist) 里查看。

被翻译的文字会发送给 DeepSeek，敏感内容请自行判断。
