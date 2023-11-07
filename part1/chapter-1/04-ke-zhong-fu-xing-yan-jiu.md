# 可重复性研究



> Since the computer is a sharp enough tool to be really useful, you can cut yourself on it — The Technical Skills of Statistics(1964) John Tukey

重复科学发现是唯一确认它们正确的方法，而不是一次实验和分析的产物。Karl Popper(1959)在《The Logic of Scientific Discovery》里有一句名言:"不可重复的单一事件对科学没有意义。"独立重复实验和分析是我们评估科学发现有效性的黄金标准。不幸的是，大多数测序实验太昂贵，无法从试管开始复制，所以我们越来越依赖于计算机的可重复性。生物信息学项目的复杂性通常会对复现不利，所以作为优秀的科学家，我们的工作就是通过简化步骤来提高计算机上的可重复性。正如我们稍后将看到的，采用良好的可重复性实践也可以使你作为研究人员的生活更轻松。

那么什么是可复制的生物信息学项目呢?至少，它可以共享项目的代码和数据。大多数期刊和资助机构都要求你分享你的项目数据，像NCBI的Sequence Read Archive 这样的资源就是为了这个目的而存在的。现在，编辑和审稿人通常会建议(或者在某些情况下要求)项目的代码也需要共享，特别是当代码是研究结果的重要组成部分时。然而，为了确保项目的可重复性，我们还需要做很多事情。我通过重复生物信息学分析来验证结果，从这些练习中学到，细节才是关键。

例如，我和同事曾经在复现我们自己完成的rna测序差异表达分析时遇到了困难。几周前，我们对一小部分样本进行分析得出了初步结果，但令我们惊讶的是，我们目前的分析得出的差异表达基因组要小得多。在重新检查过去的结果是如何产生，比较数据版本和文件创建时间，并查看分析代码中的差异之后，我们仍然感到困惑——没有什么可以解释结果之间的差异。最后，我们检查了R包的版本，发现它在我们的服务器上已经更新了。然后，我们重新安装了旧版本，以确认这是差异的来源，事实确实如此。这里的教训是，无论是你将来还是其他人的重现，通常不仅依赖于数据和代码，还依赖于软件版本、数据下载时间和版本等细节。这种元数据，或关于数据的数据，是确保再现性的关键细节。

另一个关于生物信息学可重复性的案例是所谓的“Duke Saga”。杜克大学的Anil Potti博士和其他研究人员创造了一种方法，利用高通量微阵列的表达数据来检测和预测对不同化疗药物的反应。这些方法是个性化医疗新的起点，并被用于确定临床试验中患者的最佳治疗方案。然而，两位生物统计学家Keith Baggerly和Kevin Coombes在试图重现该研究时发现了该研究分析中的严重缺陷(Baggerly和Coombes, 2009)。在没有足够的文件来追溯每一步的情况下,许多错误都需要通过调查来重现研究的发现,他们称调查为“法医生物信息学”。 Baggerly和Coombes总共发现了多个严重错误，包括: •一个大小差一的错误，因为整个基因表达值列表相对于它们的正确标识符向下移动了 •两个具有生物学意义的异常基因不在使用的微阵列上 •治疗日期与微阵列运行日期存在混淆 •样本组名称混淆 Baggerly和Coombes的工作在他们的开放获取文章中得到了最好的总结，“Deriving Chemosensitivity from Cell Lines: Forensic Bioinformatics and Reproducible Research in High-Throughput Biology”(参见本章的GitHub目录，获取这篇文章和有关杜克传奇的更多信息)。Baggerly和Coombes的工作告诉我们，“常见的错误很简单，简单的错误也很常见”，而糟糕的文档会导致错误和不可复制。为方法、数据版本和代码写文档不仅可以促进再现性，而且可以防止他们研究中的一些严重错误。在项目中追求最大的可重复性通常也会使你的工作更加健壮。


