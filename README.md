# loment-site

Loment 的官网。静态站，手写 HTML/CSS，没有构建步骤、没有依赖。

站点本身是**英文**的 —— Loment 的对外材料（README、QUICKSTART、语言指南、
仓库描述与 topics）都是英文，官网跟着走。这份 README 是给维护者的，所以是中文。

## 文件

| | |
|---|---|
| `index.html` | 落地页：一句话定义、一段可跑的代码、三件资产、Download |
| `start.html` | 安装与第一个程序（`QUICKSTART.md` 的短版） |
| `examples.html` | 四个短程序，各带真跑出来的输出 |
| `style.css` | 全部样式。一个强调色、一套字体族，都在文件头的注释里说明了理由 |
| `examples/*.lomt` | `examples.html` 上那四个程序的**源**，可重跑 |
| `mark.svg` | 站点图标与顶栏的 mark |

## 硬约定

**1. 不放会过期的事实。** 这是这个站最容易烂掉的地方 —— 它上一版
（`fujojtop.github.io/FujoOSwebsite/loment/`）在 0.1.4 发布后仍在说"预编译工具链尚未发布"，
还挂着一个"立刻使用"的弹窗。

所以：

- 所有下载链接写 `releases/latest`，**不写版本号**，也不写归档文件名
  （文件名带版本号）；
- **不写**模块数、示例数、内置命令数、语言数这类会随仓库变的计数；
- 版本号只在必须的地方出现，且以仓库为权威。

**2. 代码示例必须真跑过。** 不要凭语法印象写。跑法：

```bash
# 用发布版（用户实际会拿到的那个）
#   https://github.com/FujoJTOP/loment/releases/latest → linux-x64.tar.gz
loment run examples/hello.lomt
```

`examples/*.lomt` 是站上代码的源。改了 `examples.html` 里的代码就要同步改源文件并重跑 ——
两处不一致的话，源文件就是错的，因为它声称自己对应站上那段。

**3. 已知跑不了的东西，要么不放，要么如实标注。** `examples.html` 末尾那段注记是范例：
capability 不在那四个示例里，因为它在本版**链接不过去**（自举链接器的缺陷，参考实现没事）。
站上不假装它能跑。

## 改与发

改完直接 push 到 `main`，GitHub Pages 从分支直接服务（`build_type: legacy`），
没有 CI、没有生成步骤。本地预览：

```bash
python -m http.server 8000
```

## 这个仓是只读的吗

不是。站点内容以这个仓为准，在别处改不会生效。
