# 08 使用 Pandoc 将 Markdown 渲染成 HTML

我们将使用流行的文档转换器 Pandoc 来将我们的 Markdown 文档s转换为有效的 HTML。然后，这些 HTML 文件就可以与协作者共享托管到网站上。有关如何在系统中安装 Pandoc 的说明，请参阅 Pandoc 安装页面。

Pandoc 可以在各种不同的标记和输出格式之间进行转换。使用方法 非常简单--从 Markdown 转换为 HTML，使用 --from markdown 和 --to html 选项，并将输入文件作为最后一个参数：

```bash
$ pandoc --from markdown --to html notebook.md > output.html
```

默认情况下，Pandoc 会将输出写入标准输出，我们可以将其重定向到文件中（我们将在第 3 章中学习更多关于标准输出和重定向的知识）。我们也可以使用--output output.html指定输出文件。最后，请注意 Pandoc 可以在多种格式之间转换。我在GitHub上的本章的README中包含了更多的例子，包括如何从HTML转换到PDF。
