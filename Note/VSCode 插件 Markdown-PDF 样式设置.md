# VSCode 插件 Markdown-PDF 样式设置

> TIME : 2024-07-29
> TAGS : VSCode ; Plugin

导出的 PDF 样式基于[本插件 Github 仓库](https://github.com/yzane/vscode-markdown-pdf/blob/master/styles/markdown-pdf.css)修改完善, 优化 Windows10 下的中文显示

样式在 `.\Misc\Markdown-PDF.css` 中

## 样式应用

settings.json 中加上样式路径:

```json
"markdown-pdf.styles": ["D:\\Path\\to\\Styles.css"],
```

在 markdown 文件中，右键空白区域, 选择 `Markdown PDF: Export(pdf)` 即可导出为应用了样式的 PDF

## 去除转 pdf 时的页眉和页脚

打开 vscode, 选择 `File -> Preferences -> Settings -> Extensions -> Markdown-pdf configuration ->Display Header Footer`, 取消该选择框前的对勾即可
