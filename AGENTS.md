# AGENTS.md

## 项目概览

这是一个毕业论文 LaTeX 工程，基于北京大学学位论文模板 `pkuthss` 组织。
当前仓库里真正需要频繁修改的内容，主要集中在 `doc/example/` 目录下；根目录的 `tex/` 更像模板与类文件区，通常不要随意改。

论文题目目前配置在 [doc/example/thesis.tex](/d:/01_DEV/DevRepository/graduation_design/doc/example/thesis.tex:62)：
- 中文题目：`面向多模态理解的对话安全模型构建与应用`
- 英文题目：`Construction and Application of a Dialogue Safety Model for Multimodal Understanding`

## 主要内容放置位置

核心入口文件：
- [doc/example/thesis.tex](/d:/01_DEV/DevRepository/graduation_design/doc/example/thesis.tex:1)
  负责整体导言区、论文信息、章节 `\include` 顺序、参考文献输出等。

章节正文：
- [doc/example/chap/chap1.tex](/d:/01_DEV/DevRepository/graduation_design/doc/example/chap/chap1.tex:4) `绪论`
- [doc/example/chap/chap2.tex](/d:/01_DEV/DevRepository/graduation_design/doc/example/chap/chap2.tex:3) `相关工作`
- [doc/example/chap/chap3.tex](/d:/01_DEV/DevRepository/graduation_design/doc/example/chap/chap3.tex:3) `需求分析`
- [doc/example/chap/chap4.tex](/d:/01_DEV/DevRepository/graduation_design/doc/example/chap/chap4.tex:4) `训练方法与数据构建`
- [doc/example/chap/chap5.tex](/d:/01_DEV/DevRepository/graduation_design/doc/example/chap/chap5.tex:3) `实验验证与效果分析`
- [doc/example/chap/chap6.tex](/d:/01_DEV/DevRepository/graduation_design/doc/example/chap/chap6.tex:1) `研究结论、局限与未来工作`

前后置材料：
- [doc/example/chap/abs.tex](/d:/01_DEV/DevRepository/graduation_design/doc/example/chap/abs.tex:1) 中英文摘要
- [doc/example/chap/ack.tex](/d:/01_DEV/DevRepository/graduation_design/doc/example/chap/ack.tex:4) 致谢
- [doc/example/chap/copy.tex](/d:/01_DEV/DevRepository/graduation_design/doc/example/chap/copy.tex:1) 版权声明
- [doc/example/chap/origin.tex](/d:/01_DEV/DevRepository/graduation_design/doc/example/chap/origin.tex:1) 原创性声明/授权相关内容

参考文献：
- [doc/example/thesis.bib](/d:/01_DEV/DevRepository/graduation_design/doc/example/thesis.bib:1)
- [doc/example/thesis-blx.bib](/d:/01_DEV/DevRepository/graduation_design/doc/example/thesis-blx.bib:1)
- [doc/example/andriushchenko.bib](/d:/01_DEV/DevRepository/graduation_design/doc/example/andriushchenko.bib:1)

图表与素材：
- [doc/example/figures](/d:/01_DEV/DevRepository/graduation_design/doc/example/figures)

构建脚本：
- [doc/example/Make.bat](/d:/01_DEV/DevRepository/graduation_design/doc/example/Make.bat:1)
  默认通过 `latexmk` 编译，`clean` 时执行 `latexmk -c`。

模板与样式：
- [tex/pkuthss.cls](/d:/01_DEV/DevRepository/graduation_design/tex/pkuthss.cls:1)
- [tex/pkuthss.def](/d:/01_DEV/DevRepository/graduation_design/tex/pkuthss.def:1)
- [tex/pkuthss-utf8.def](/d:/01_DEV/DevRepository/graduation_design/tex/pkuthss-utf8.def:1)
- [doc/example/ctexopts.cfg](/d:/01_DEV/DevRepository/graduation_design/doc/example/ctexopts.cfg:1)
- [doc/example/ctex-fontset-pkuthss.def](/d:/01_DEV/DevRepository/graduation_design/doc/example/ctex-fontset-pkuthss.def:1)

## 目录判断建议

如果只是写论文内容，优先改这些地方：
- 改章节正文：`doc/example/chap/*.tex`
- 改封面、摘要、章节顺序、宏包：`doc/example/thesis.tex`
- 改参考文献：`doc/example/thesis.bib`
- 加图片：`doc/example/figures/`

如果不是在修模板问题，尽量不要动这些地方：
- `tex/*.cls`
- `tex/*.def`
- `doc/readme/*`

`doc/readme/` 更像模板自带说明文档，不是你的论文正文。

## 编译方式

在 `doc/example/` 目录下：

```bat
Make.bat doc
```

或直接：

```bat
latexmk
```

清理中间文件：

```bat
Make.bat clean
```

## 当前仓库的一个小提醒

`doc/example/chap/` 目录下目前已经有不少 `*.aux` 编译中间文件，它们不是正文内容。编辑时应优先关注同名的 `*.tex` 文件，不要把 `*.aux` 当成需要维护的源文件。

## 给后续协作者/Agent 的约定

1. 默认把 `doc/example/` 视为论文工作区。
2. 修改正文时，优先最小改动，不重排整篇结构。
3. 若需改模板样式，先说明原因，再考虑动 `tex/` 下的类文件。
4. 新增图片或数据说明时，尽量放进 `doc/example/figures/` 或 `doc/example/chap/` 附近，保持相对路径简单。
5. 处理参考文献时，优先复用 `thesis.bib`，避免把引用分散到过多 bib 文件。
