# 04 使用目录把项目分解为子项目

生物信息学项目涉及许多子项目和子分析。在通过生物信息学工具运行原始实验数据之前，应评估其质量并去除质量较差的区域。(我们在 “Example: Inspecting and Trimming Low-Quality Bases” 第 346 页有一个例子）。甚至在实际分析序列之前，项目目录就会被中间文件弄得乱七八糟。

创建子项目，逻辑上分隔子项目（例如测序数据质量改进、比对、分析比对结果等）可以简化复杂的项目，并有助于保持文件的有序性。它还有助于降低错误脚本意外破坏文件的风险，因为子目录有助于隔离事故。将子项目保存在单独的子目录中，还能让记录工作变得更容易。每个 README 都与所在目录相关。最终，你会找到适合自己的项目组织系统。关键的一点是:利用目录来帮助保持组织。