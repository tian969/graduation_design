# 项目上下文文件 (AGENTS.md)

## 项目概述

这是一个基于 LaTeX 的学位论文项目,使用北京大学研究生论文模板(pkuthss)编写。论文主题为"面向多模态理解的对话安全模型构建与应用",属于软件工程专业信息安全方向的硕士学位论文。

### 项目类型
- **类型**: 学术论文/文档项目
- **主要技术**: LaTeX (XeLaTeX/LuaLaTeX), BibLaTeX
- **模板**: pkuthss (北京大学研究生论文模板)
- **字体配置**: ctex 中文支持,使用 pkuthss 字体集

### 项目结构

```
/Users/tianzujie.1/DevRepo/graduation_design/doc/example/
├── thesis.tex              # 论文主文件(根文档)
├── thesis.bib              # 参考文献数据库
├── Make.bat                # Windows 编译脚本
├── ctex-fontset-pkuthss.def # 中文字体配置
├── ctexopts.cfg            # ctex 选项配置
├── spine.tex               # 书脊文件
├── chap/                   # 论文章节目录
│   ├── abs.tex             # 中英文摘要
│   ├── ack.tex             # 致谢
│   ├── chap1.tex           # 第一章:绪论
│   ├── chap2.tex           # 第二章:相关工作
│   ├── chap3.tex           # 第三章:方法设计
│   ├── chap4.tex           # 第四章:实验与分析
│   ├── chap5.tex           # 第五章:总结与展望
│   ├── copy.tex            # 版权声明
│   ├── origin.tex          # 原创性声明
│   └── encl1.tex           # 附录
└── figures/                # 图片资源目录
    ├── VLM输出不当内容.png
    ├── Openai_policy.txt
    └── 越狱评估集评估模版.txt
```

## 编译与构建

### 编译命令

**Windows 用户:**
```batch
# 完整编译(生成 PDF)
Make.bat doc

# 清理临时文件
Make.bat clean
```

**macOS/Linux 用户 (需要 latexmk):**
```bash
# 完整编译
latexmk

# 清理临时文件
latexmk -c

# 指定编译器(XeLaTeX 推荐)
latexmk -xelatex
```

### 编译流程
1. **XeLaTeX** - 编译主文档
2. **Biber** - 处理参考文献
3. **XeLaTeX** - 重新编译(解析引用)
4. **XeLaTeX** - 最终编译(生成完整 PDF)

### 注意事项
- 推荐使用 **XeLaTeX** 或 **LuaLaTeX** 编译器(支持中文)
- 必须先运行 `latexmk` 或 `Make.bat doc` 完整编译
- 参考文献使用 BibLaTeX + Biber 处理
- 编译后生成的文件:
  - `thesis.pdf` - 最终论文
  - `thesis.synctex.gz` - 同步信息(用于 PDF 源跳转)
  - `thesis.bbl` - 处理后的参考文献
  - `thesis.blg` - Biber 日志

## 写作规范与约定

### 文档结构
- **封面信息**: 在 `thesis.tex` 的 `\pkuthssinfo` 中配置
- **双盲模式**: 将 `\blindfalse` 改为 `\blindtrue` 启用
- **章节组织**: 按照标准学术论文章节结构
  - 绪论(chap1)
  - 相关工作(chap2)
  - 方法设计(chap3)
  - 实验分析(chap4)
  - 总结展望(chap5)

### 参考文献规范
- **数据库**: `thesis.bib`
- **格式**: BibLaTeX with `caspervector` style
- **排序**: 西文文献在前,中文文献在后 (`sorting = ecnyt`)
- **引用命令**:
  - `\cite{key}` - 普通引用
  - `\parencite{key}` - 带方括号引用
  - `\supercite{key}` - 上标引用

### 字体使用
- **宋体**: `\songti` 或 `\CJKfamily{zhsong}`
- **黑体**: `\heiti` 或 `\CJKfamily{zhhei}`
- **仿宋**: `\fangsong` 或 `\CJKfamily{zhfs}`
- **楷体**: `\kaishu` 或 `\CJKfamily{zhkai}`

### 图片插入
- 图片存放在 `figures/` 目录
- 使用 `\includegraphics` 命令
- 示例:
  ```latex
  \begin{figure}[htbp]
      \centering
      \includegraphics[width=0.8\textwidth]{figures/图片名.png}
      \caption{图片说明}
      \label{fig:引用标签}
  \end{figure}
  ```

### 缩写词
- 使用 `acronym` 包
- 定义: `\ac{缩写}` - 首次展开,后续仅显示缩写
- 示例: `\ac{LLM}` - 大语言模型

### 数学公式
- 行内公式: `$...$`
- 行间公式: `\[...\]` 或 `$$...$$`
- 带编号: `\begin{equation}...\end{equation}`

## 常见问题解决

### 格式审查问题
- 如果提示字号不符合标准,在 `\documentclass` 中添加 `ugly` 选项
- 脚注按页编号: 取消 `footmisc` 包的注释
- 去除彩色框: 在导言区添加 `\hypersetup{hidelinks}`

### 参考文献不显示
1. 确认 `.bib` 文件存在
2. 运行完整编译流程
3. 参考 `texdoc pkuthss` 中关于 biber 的说明

### 编译错误
- 确保使用 XeLaTeX/LuaLaTeX 编译器
- 检查是否安装了所有依赖的 TeX 包
- 查看 `.log` 文件获取详细错误信息

## 工作流程建议

1. **章节写作**: 在 `chap/` 目录下的相应文件中编辑
2. **本地编译**: 使用 `latexmk` 或 `Make.bat doc` 进行完整编译
3. **引用管理**: 在 `thesis.bib` 中添加参考文献,使用 `\cite{key}` 引用
4. **图表插入**: 将图片放入 `figures/`,使用标准 LaTeX 语法插入
5. **格式调整**: 修改 `thesis.tex` 中的文档信息和配置

## 相关文档

- 查看模板文档: `texdoc pkuthss`
- 查看参考文献格式: `texdoc biblatex-caspervector`
- 编译工具文档: `texdoc latexmk`

## Git 注意事项

- 当前分支: `main`
- 未跟踪文件: `AGENTS.md`, `figures/Openai_policy.txt`, `figures/越狱评估集评估模版.txt`
- 已修改文件: `chap/chap2.tex`, `chap/chap3.tex`, `chap/chap4.tex`, `thesis.bib`
- 远程仓库: https://github.com/tian969/graduation_design.git

## 论文内容摘要

**标题**: 面向多模态理解的对话安全模型构建与应用

**研究方向**: 信息安全

**主要章节**:
1. 绪论 - 研究背景、意义及工作内容
2. 相关工作 - 大模型微调、思维链、安全风险、RAG 技术综述
3. 方法设计 - 多模态安全数据构造与训练框架
4. 实验分析 - 评估设计与结果分析
5. 总结与展望

**核心关键词**: 大语言模型(LLM)、视觉语言模型(VLM)、多模态安全、越狱攻击、检索增强生成(RAG)