# 制作工作区 / Work

本目录是当前版次全部字幕文件的存放位置，下方会看到三个子目录，脚本按固定顺序解析：

1. 若 [`authored/`](./authored/) 中存在对应语言的人工稿，优先采用
2. 否则若该语言是 [`authored/main.ass`](./authored/main.ass) 的主语言，从中提取
3. 否则采用 [`source/`](./source/) 中的官方原始底本
4. 否则按既定转换关系（如简繁转换）自动生成，结果落入 [`generated/`](./generated/)

## 我要做什么

- **下载 / 查看原始字幕** → [`source/`](./source/)
- **翻译、校对、制作特效** → [`authored/`](./authored/)
- **查看自动化生成的最终结果** → [`generated/`](./generated/)，请勿在此目录直接编辑，修改会在下次自动化运行时被覆盖

---

<div align="center">

**蒙太奇字幕社区 (MontageSubs)**  
"用爱发电 ❤️ Powered by Love"

</div>
