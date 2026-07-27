# openResume-data

[ranpin/openResume](https://github.com/ranpin/openResume)（简历中心 SPA）的**数据仓库**——与代码仓库隔离，简历与经历库内容持久化在这里，应用运行时从本仓库拉取。

## 结构

```
index.json          # 清单：列出各集合包含的 YAML 路径，应用入口
resumes/*.yaml      # 简历（文件名去扩展名 = 稳定 id）
projects/*.yaml     # 经历库 · 项目
internships/*.yaml  # 经历库 · 实习
honors.yaml         # 经历库 · 荣誉（单文件数组）
```

## 读写链路

- **读**：应用从 `https://raw.githubusercontent.com/ranpin/openResume-data/main/index.json` 取清单，再并行拉取各 YAML。
- **写**：在应用编辑器内「发布到线上」——浏览器直连 GitHub Contents API 提交 YAML（BYO Token，令牌只存发布者本地浏览器），约 1 分钟后生效。新建简历的发布会同步更新 `index.json`。

## 复用自己的数据

fork [ranpin/openResume](https://github.com/ranpin/openResume) 后，修改代码仓库 `src/data/source.ts` 指向你自己的数据仓库（或置空进入纯本地模式，数据只存浏览器 IndexedDB）。
