# 生信起源 不断增长的生物学数据

生物信息学家关注的是使用专业技能和工具从大量数据中获取生物学的新知识。生物学发展早期，数据集比较小，方便管理。大多数生物学家可以学习统计学课程，然后使用个人电脑上的excel进行自己的数据分析。然而，事情正在起变化。大规模测序数据集开始流行，并且将来只会变得更普遍。分析这种数据需要不同的工具、新的技能以及拥有大内存、多处理器和大量磁盘空间的电脑。

在一段相对较短的时间内，测序成本指数级下降。因此研究者可以使用测序数据来回答重大生物学问题。早期测序是低通量测序且成本昂贵。全基因组测序成本高昂(人类基因组测序要花费27亿美元左右)并且只有通过大规模合作才能实现。从人类基因组发布开始直到2008年，测序成本指数级下降。如图1-1所示，随着下一代测序技术的发展，每百万碱基对DNA测序成本下降得更快了。在这个关键节点，从前只有通过大规模合作或者腰包鼓鼓的独立研究者才能完成的测序项目，现在变成了所有生物学研究者都可以承担的技术。你可能正是为了学习处理测序数据才阅读本书，实际上这些数据在不到十年前是十分昂贵的。

这些新技术出现带来了测序成本下降，那么代价是什么？你可能已经猜到了，堆积如山的数据。生物数据库大小也开始了指数级膨胀。曾经只要合作者之间共享小型数据库即可,现在千兆字节的有用数据存放在世界各地的服务器上。对生物学问题的关键见解不仅存在于你硬盘上未经分析的实验数据中，而且还存储在数千英里外数据中心的磁盘上。

生物数据库的增长和测序成本的下降一样令人震惊。例如[Sequence Read Archive](https://www.ncbi.nlm.nih.gov/sra)，它是测序实验的测序数据的存储库。自2010年以来，它经历了显著的增长;如图1-2所示。

为了更好地理解测序数据的惊人增长，我们来看看摩尔定律。戈登·摩尔(英特尔的联合创始人)观察到，计算机芯片中的晶体管数量大约每两年翻一番。每个芯片上更多的晶体管意味着更快的计算机处理器速度，更多的随机存取存储器，从而带来性能更强大的计算机。这种非凡的技术进步速度——产量每两年翻一番——可能是人类所见过的最快的技术发展速度。然而，自2011年以来，存储在Short Read Archive中的测序数据量已经超过了这一令人难以置信的增长速度，它每年都翻一番。

让事情变得更加复杂的是，分析生物数据的新工具不断被创造出来，它们的底层算法也在不断进步。2012年的一篇综述列出了70多个短读长映射工具(Fonseca et al, 2012;)。同样，我们的基因组组装方法在过去五年中发生了很大变化，因为组装长序列的方法(如重叠布局共识算法)随着短高通量测序读取方法的出现而被抛弃。现在，测序化学的进步正在导致更长的测序读取长度，新的算法正在取代几年前的其他算法。

不幸的是，这些快速发展的生物信息学工具有严重的缺点。通常，生物信息学工具没有充分的标准，或者即使有，也只是在一个生物体中进行标准测试。这使得新的生物学家很难找到和选择最好的工具来分析他们的数据。雪上加霜的是，一些生物信息学程序没有积极开发，因此它们失去了相关性或携带可能对结果产生负面影响的错误。所有这些都使得在你自己的研究中选择一个合适的生物信息学程序变得困难。更重要的是，必须严格评估生物信息学程序运行你自己数据得到的输出。我们将在第二部分中看到数据技能如何帮助我们评估程序输出的例子。