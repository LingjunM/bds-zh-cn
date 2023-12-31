# 01 项目目录和目录结构

创建一个组织良好的目录结构是可重复生物信息学项目的基础。实际过程非常简单：布局一个项目只需要用 mkdir 创建几个目录，用 touch 创建空的 README 文件（稍后我们将深入了解这些命令)。这种简单的初始规划会获得长期的回报。对于大型项目，研究人员可能要花费数年时间在这种目录结构中工作。

其他研究人员也注意到良好项目组织的重要性（Noble，2009 年）。在本章中，我们将首先介绍我在工作中使用的方案（与 Noble 的方案类似），最终你会发展出适合自己的项目组织风格。

项目中使用的所有文件和目录都应存放在单个项目目录中，并有明确的名称。在项目过程中，你会积累大量的数据文件、笔记和脚本，如果这些文件分散在硬盘上（更有甚者，散落在多台计算机的硬盘上），那么要追踪文件和目录就是噩梦。更糟糕的是，这种无序的项目以后会让你的研究几乎无法重现。

将所有文件保存在一个目录中，将大大简化你和合作者的工作，并提高可重复性（我们将在第 5 章讨论如何使用 Git 在项目目录中协同工作）。假设你正在研究玉米的SNP calling。第一步是选择一个简短、合适的项目名称，并创建一些基本目录：

```bash
$ mkdir zmays-snps
$ cd zmays-snps
$ mkdir data
$ mkdir data/seqs scripts analysis
$ ls -l
total 0
drwxr-xr-x 2 vinceb staff 68 Apr 15 01:10 analysis
drwxr-xr-x 3 vinceb staff 102 Apr 15 01:10 data
drwxr-xr-x 2 vinceb staff 68 Apr 15 01:10 scripts
```

这是一个合理的项目布局方案。data/ 包含所有原始数据和中间数据。正如我们将要看到的，数据处理步骤被分解为该data/ 目录中独立的子项目。我将整个项目的通用脚本放在 scripts/ 目录中。如果脚本包含很多文件（例如多个 Python 模块），它们应该放在自己的子目录中。将脚本隔离在自己的子目录中还能在开发这些脚本时保持项目目录的整洁（当它们生成测试输出文件时）。

生物信息学项目包含许多较小的分析--例如，分析原始测序的质量、比对结果以及最终生成论文图表的数据。我更喜欢将这些数据保存在单独的 analysis/ 目录中，这样合作者就能看到这些高级分析，而无需深入子项目目录。
