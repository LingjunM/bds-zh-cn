# 07 markdown语法基础

Markdown 的格式化功能符合生物信息学笔记本的所有需求： 文本可以分成不同的层次，有代码块和内联代码的语法，而且很容易嵌入链接和图片。虽然 Markdown 格式 格式非常简单，但也有几种不同的变体。我们将使用原始的 Markdown，它是由约翰-格鲁伯（John Gruber）发明的。约翰-格鲁伯的完整 Markdown 语法规范可在他的网站上查阅。下面是一个基本的 Markdown 文档，展示了 Markdown 的格式。

```
# *Zea Mays* SNP Calling

We sequenced three lines of *zea mays*, using paired-end
sequencing. This sequencing was done by our sequencing core and we
received the data on 2013-05-10. Each variety should have **two**
sequences files, with suffixes `_R1.fastq` and `_R2.fastq`, indicating
which member of the pair it is.

## Sequencing Files

All raw FASTQ sequences are in `data/seqs/`:
 $ find data/seqs -name "*.fastq"
 data/seqs/zmaysA_R1.fastq
 data/seqs/zmaysA_R2.fastq
 data/seqs/zmaysB_R1.fastq
 data/seqs/zmaysB_R2.fastq
 data/seqs/zmaysC_R1.fastq
 data/seqs/zmaysC_R2.fastq
 
## Quality Control Steps

After the sequencing data was received, our first stage of analysis
was to ensure the sequences were high quality. We ran each of the
three lines' two paired-end FASTQ files through a quality diagnostic
and control pipeline. Our planned pipeline is:

1. Create base quality diagnostic graphs.
2. Check reads for adapter sequences.
3. Trim adapter sequences.
4. Trim poor quality bases.

Recommended trimming programs:

 - Trimmomatic
 - Scythe
```

图2-1是由Pandoc以HTML5呈现的Markdown笔记本示例。Markdown之所以成为实验笔记本的好格式，是因为它在未渲染的纯文本中和在渲染的HTML中一样容易阅读。接下来，让我们看一下在这个例子中使用的markdown语法。(参考表2-2)。

[详细语法](https://markdown.com.cn/)

<figure><img src="../../.gitbook/assets/Pasted image 20231101204109.png" alt=""><figcaption><p>图2-1</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/Pasted image 20231101205636.png" alt=""><figcaption><p>表2-2</p></figcaption></figure>

标题、列表和代码块等块元素都很简单。不同级别的标题 可以用不同数量的#来指定。例如

```
# Header level 1
## Header level 2
### Header level 3
```

Markdown 支持深达六级的标题。也可以为标题使用一种替代语法，最多可达两个级别:

```
Header level 1
==============
Header level 2
--------------
```

有序和无序列表也很容易。对于无序列表，使用破折号、星号作为列表元素标记。例如，使用破折号

```markdown
- Francis Crick
- James D. Watson
- Rosalind Franklin
```

要给列表排序，只需使用数字（如 1、2、3 等）。 HTML 会自动递增这些数字。不过，最好还是给要点编上清楚的序号，这样纯文本版本才具有可读性。

代码块也很简单，只需在每行代码前添加四个空格或一个制表符即可。

```
I ran the following command:
	$ find seqs/ -name "*.fastq" 
```

如果要将代码块放在列表项中，则需要八个空格或两个制表符。

<pre><code><strong>1. I searched for all FASTQ files using:
</strong>              find seqs/ -name "*.fastq"
2. And finally, VCF files with:
              find vcf/ -name "*.vcf"
</code></pre>

我们在这里介绍的内容应该足以让你开始以数字方式记录生物信息学工作。此外，还有一些 Markdown 的扩展，如 MultiMarkdown 和 GitHub Flavored Markdown。这些变体拓展了功能（MultiMarkdown 增加了表格、脚注、LaTeX 数学支持等功能）并更改一些默认的渲染选项。如果你喜欢基于图形用户界面的Markdown 编辑应用程序（请参阅本章GitHub的README 获取一些建议）。
