## 待初始化

这是一个刚从模板创建的字幕仓库，尚未完成信息初始化。请按照以下步骤完成自动化配置。

### 下一步

1. **确认仓库名**：建议对照下方 [仓库命名规范](#仓库命名规范) 检查仓库名格式，如不符合，可前往 **[Settings](../../settings)** 修改。
2. **检查可见性**：检查页面顶部仓库名右侧的标签
   - 已显示 **Public** --> 进行第 3 步
   - 显示 **Private** --> 点击 [此链接](../../settings#danger-zone) 进入 Danger Zone（或手动前往 **Settings --> General --> Danger Zone**），选择 **Change repository visibility** 更改为 **Public**
3. **触发初始化**：进入 **[Actions](../../actions/workflows/init.yml)** 页面 --> 选择 **"初始化 (Initialize)"** 工作流 --> 点击 **Run workflow**，按下方[选项说明](#触发初始化时的选项说明)填写后运行。

### 仓库命名规范

仓库名必须为 **`英文片名_年份`** 格式（片名 + 分隔符 + 四位年份）。**缺失年份将无法解析，直接判定命名不合法。**

片名部分的大小写与分隔符写法，建议对齐 TMDB 官方英文标题惯例，但不达标不会失败，工作流会自动改名修正。

**推荐写法：**
- `Cosmos_Laundromat_2015`：下划线分隔，逐词大小写对齐 TMDB 官方标题，一次通过、无需改名。
- 也可以直接粘贴自然写法，如 `Cosmos Laundromat (2015)`：GitHub 创建仓库时会自动把空格、括号转换为短横线，工作流能正确识别短横线/下划线混用的仓库名，随后自动改名为标准写法。

**属于命名错误的情况：**
- 缺失年份（如仅 `Cosmos_Laundromat`），无法解析。
- 片名与 TMDB 收录内容差异过大，或年份相差超过 1 年，视为未找到匹配作品。

遇到以上情况，工作流会中止并将本 README 替换为错误说明，按提示操作即可。

### 触发初始化时的选项说明

点击 **Run workflow** 后会展开以下参数。**WEB / BluRay / 自定义来源标识三者互斥，必须选定其中一项**；其余参数保持默认（留空/不勾选）即可。

| 选项 | 含义 | 何时选择 |
|---|---|---|
| **WEB** | 本次资源来源为网络流媒体版本 | 来源是 WEB 时勾选此项（与 BluRay 互斥） |
| **BluRay** | 本次资源来源为蓝光版本 | 来源是蓝光时勾选此项（与 WEB 互斥） |
| **自定义来源标识** | 来源既非 WEB 也非 BluRay 时手动填写（如 `AMZN`、`Directors-Cut`），命名规则见 `docs/guides/EDITION_GUIDE.md` | 仅在 WEB / BluRay 均不适用时填写 |
| **手动指定 TMDB/IMDb ID** | 跳过按仓库名自动搜索，直接用提供的 ID 或 URL 拉取信息 | 默认留空（按仓库名自动搜索）；仅当自动搜索匹配错误、或片名生僻难以被 TMDB 检索到时才填写 |
| **强制初始化** | 忽略已初始化标记，清空现有文件并重新生成；若仍未匹配到作品则生成空白模板 | 首次初始化保持不勾选；仅在需要重新拉取信息或修复初始化异常时勾选 |
| **跳过剧情摘要生成** | 跳过 Wikipedia/LLM 剧情摘要环节 | 默认不勾选；仅在摘要接口异常导致流程受阻时临时勾选，先完成基础初始化 |

### 工作流说明

工作流会自动根据仓库名在 TMDB 检索影视信息，并将本 README 重写为正式的项目主页。

> [!NOTE]
> - 自动化流程需要仓库为公开状态才能正常读写仓库信息。

---

## Awaiting Initialization

This is a subtitle repository created from a template and is awaiting initialization. Please follow the steps below to complete the automated setup.

### Next Steps

1. **Confirm Repository Name**: Check the repository name against the [Naming Conventions](#naming-conventions) below. If it doesn't match, you can update it in **[Settings](../../settings)**.
2. **Check Visibility**: Check the label next to the repository name at the top of the page.
   - **Public** --> Proceed to Step 3.
   - **Private** --> Click [this link](../../settings#danger-zone) to enter the Danger Zone (or manually navigate to **Settings --> General --> Danger Zone**) and set **Change repository visibility** to **Public**.
3. **Trigger Initialization**: Navigate to the **[Actions](../../actions/workflows/init.yml)** page --> select the **"Initialize"** workflow --> click **Run workflow**, filling in the fields per the [option guide](#workflow-options-explained) below.

### Naming Conventions

The repository name must follow **`EnglishTitle_Year`** (title + separator + four-digit year). **A missing year cannot be parsed and is immediately flagged as invalid.**

For the title segment's casing and separators, matching TMDB's official English-title convention is recommended, but falling short doesn't fail the run; the workflow auto-renames to fix it.

**Recommended forms:**
- `Cosmos_Laundromat_2015`: underscore-separated, casing matched word-for-word to TMDB's official title; passes on the first try with no rename needed.
- Pasting the natural form directly also works, e.g. `Cosmos Laundromat (2015)`: GitHub converts spaces and parentheses to hyphens on repo creation, and the workflow correctly parses names mixing hyphens and underscores, then auto-renames to the canonical form.

**What counts as an invalid name:**
- Missing year (e.g. just `Cosmos_Laundromat`), cannot be parsed.
- Title too different from what TMDB has on record, or year off by more than 1, treated as no matching title found.

In these cases the workflow aborts and replaces this README with an error message; just follow the instructions in it.

### Workflow Options Explained

Clicking **Run workflow** expands the following parameters. **WEB / BluRay / custom source label are mutually exclusive; exactly one must be selected.** All other parameters can stay at their defaults (blank/unchecked).

| Option | Meaning | When to choose |
|---|---|---|
| **WEB** | This release's source is a web/streaming version | Check when the source is WEB (mutually exclusive with BluRay) |
| **BluRay** | This release's source is a Blu-ray version | Check when the source is Blu-ray (mutually exclusive with WEB) |
| **Custom source label** | Fill in manually when the source is neither WEB nor BluRay (e.g. `AMZN`, `Directors-Cut`); naming rules in `docs/guides/EDITION_GUIDE.md` | Fill only when neither WEB nor BluRay applies |
| **Manual TMDB/IMDb ID** | Skips auto-search by repo name, fetching metadata directly from the given ID or URL | Leave blank by default (auto-search by repo name); fill in only if auto-search matches the wrong title, or the title is too obscure for TMDB search |
| **Force init** | Ignores the initialization marker, wipes existing files and regenerates; produces a blank template if still no match | Leave unchecked on first run; check only to re-fetch metadata or recover from a broken init |
| **Skip synopsis generation** | Skips the Wikipedia/LLM synopsis step | Leave unchecked by default; check temporarily only if the synopsis service is failing and you need to complete basic init first |

### Workflow Details

The workflow automatically retrieves metadata for movies and series from TMDB based on the repository name and rewrites this README as the official project homepage.

> [!NOTE]
> - The repository must be public for the automation to read and write metadata.

---

<div align="center">

**蒙太奇字幕社区 (MontageSubs)**  
"用爱发电 ❤️ Powered by Love"

</div>
