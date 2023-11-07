# 健壮性研究的要点

健壮性研究主要是关于采用一系列措施，增加对你有利的因素，使得未被发现的错误不会混淆你的结果。如上所示，除了防止可怕的沉默性错误之外，大多数实践也是有益的。这就是在你的日常生物信息学工作中应用以下建议的原因。

### 关注实验设计

可靠的研究始于良好的实验设计。再高明的分析也无法挽救设计糟糕的实验。引用一位杰出的统计学家和遗传学家的话:

> 在实验结束后咨询统计学家，通常只是要求他进行事后检验。他也许能说出实验的失败原因。 —R.A. Fisher

这句话直击要害;我曾见过，在花费了数千美元的测序资金后，一些项目被送到我的办公桌上，准备进行分析，但它们一开始就彻底夭折了。良好的实验设计并不困难，但由于它从根本上是一个统计学主题，因此超出了本书的范围。我之所以提到这个话题，是因为不幸的是，本书中没有任何其他内容可以挽救带有糟糕设计的实验。在高通量测序中对实验设计的思考尤为必要，因为技术上的“批处理效应”会严重混淆研究(关于这方面的观点，见Leek et al, 2010)。

大多数统计学入门课程和书籍涵盖了实验设计的基本主题。Quinn和Keough的《Experimental Design and Data Analysis for Biologists》(剑桥大学出版社，2002年)是一本关于这个的优秀书籍。Sarah Boslaugh所著的的《 Statistics in a Nutshell》第二版第18章也很好地涵盖了基础知识。但请注意，基因组学实验中的实验设计是另一回事，需要积极研究和改进。确保你价值几千美元的实验不白费的最好方法是查询你目前项目的最佳设计路线。在计划开展实验时，咨询身边的统计学家任何关于实验的设计问题或担忧，这也是一个好主意。

### 为人写代码，为计算机写数据

> 调试比写代码难两倍。如果你尽可能聪明地写代码。那么从定义上来说，你将没有能力调试它 ——Brian Kernighan

生信项目可能出现堆积如山的代码，防止出现bug的最好办法是为人写代码，而不是为计算机。（2012年Wilson等人在一篇文章里提出这一点）。人是用来调试的，把代码写得简单清楚有利于调试。 代码应该是可读的，分解成小的组件(模块化)，并且是可重用的(这样就不用重写代码执行相同的任务)。这些实践在软件世界中是至关重要的，也应该应用于你的生物信息学工作。注释代码和采用风格指南是提高代码可读性的简单方法。谷歌有许多语言的[公共风格指南](https://github.com/google/styleguide)，可以作为优秀的模板。为什么代码的可读性如此重要?首先，可读代码使项目更具可重复性，因为其他人可以更容易地理解脚本的功能和工作方式。其次，在可读性强、注释良好的代码中查找和纠正软件bug要比在乱七八糟的代码中容易得多。第三，当代码被很好地注释和清晰地编写时，将来重访代码总是很容易的。编写模块化和可重用的代码只需要练习——我们将在本书中看到一些这样的例子。

与代码相反，数据应该以一种便于计算机读取的方式进行格式化。作为人类，我们经常以一种最大限度地提高其可读性的方式记录数据，但在计算机处理之前，需要对数据进行大量的清理和整理。计算机可读的数据(和元数据)越多，我们就越能利用计算机来处理这些数据。

### 让计算机为你工作

人们在做死记硬背的活动时往往会犯很多错误。使工作更健壮的最简单方法之一是让计算机尽可能多地完成这些机械工作。这种自动化任务的方法更健壮，因为它减少了你犯一个小错误的几率，比如不小心遗漏了一个文件或错误地命名输出文件。

例如，通过单独输入(或复制粘贴)每个命令运行一个程序处理20个不同的文件是很脆弱的——随着处理文件的增加，犯粗心错误的几率也会增加。在生物信息学工作中，最好养成让计算机为你做这种重复性工作的习惯。不要粘贴同一个命令20次，只是改变输入和输出文件，写一个脚本做到这一点。这不仅更容易做到，更容易不出错，而且还增加了可重复性，因为您的脚本可以作为对每个文件所做操作的参考。

要获得自动化任务的收益，需要在组织项目、数据和代码方面进行一些思考。简单的习惯，比如以计算机(而不仅仅是人类)能够理解的一致方式命名数据文件，可以极大地促进任务的自动化，使工作变得更容易。我们将在第2章看到这样的例子。

### 在代码和方法中积极使用断言

当我们编写代码时，我们倾向于对数据有隐含的假设。例如，我们期望只有三种DNA链选项(正链、负链和未知)，基因的起始位置小于结束位置，并且我们不能有负位置。我们对数据的这些隐含假设会影响我们编写代码的方式;例如，如果我们认为某种情况不会发生，我们可能不会考虑在代码中处理这种情况。不幸的是，这可能导致可怕的沉默的错误:我们的代码或程序接收超出预期的值，行为不正确，但仍然返回输出而没有警告。我们预防这类错误的最好方法是在代码中显式地声明和测试我们对数据的假设，使用声明和断言语句如Python的assert()和R的stopifnot()。

几乎每种编程语言都有自己版本的assert函数。这些函数的操作方式类似:如果语句的求值为false，则assert函数将停止程序并抛出错误。这些函数可能很简单，但在可靠的研究中是不可或缺的。在我职业生涯的早期，一位导师鼓励我养成自由使用断言的习惯——即使在看起来绝对不可能出错的地方。我一直惊讶于这些断言有多少次发现了一个微妙的错误。在生物信息学(以及所有领域)中，尽可能地把可怕的无声错误变成可见的错误至关重要。

### 测试代码

软件工程师是一群聪明的人，他们把让电脑完成工作的想法提升到了一个新的高度。他们让代码测试其他代码，而不是手工完成。测试代码的一种常用方法称为单元测试。在单元测试中，我们将代码分解为单独的模块单元(这也有提高可读性的副作用)，并编写额外的代码来测试这些代码。在实践中，这意味着如果我们有一个名为add()的函数，我们编写一个名为test\_add()的附加函数(通常在单独的文件中)。这个test\_add()函数将调用带有特定输入的add()函数，并测试输出是否符合预期。在Python中，这看起来像

```python
EPS = 0.00001 # a small number to use when comparing floating-point values
def add(x, y):
 """Add two things together."""
 return x + y
def test_add():
 """Test that the add() function works for a variety of numeric types."""
 assert(add(2, 3) == 5)
 assert(add(-2, 3) == 1)
 assert(add(-1, -1) == -2)
 assert(abs(add(2.4, 0.1) - 2.5) < EPS)
```

test\_add()函数的最后一行看起来比其他一行更复杂，因为它比较的是浮点值。在计算机上比较浮点值是很困难的，因为存在表示和舍入错误。然而，这是一个很好的提醒，我们总是受到我们的机器性能的限制，我们必须在分析中注意这些限制。

单元测试在科学代码中的使用要比在软件行业中少得多，尽管科学代码更有可能包含错误(因为我们的代码通常只运行一次以生成发表的结果，并且科学代码中的许多错误是无声的)。我把这称为科学编码的悖论: _科学编码容易出错的本质意味着我们应该像软件行业一样或更多地利用测试，但我们实际上做的测试要少得多(如果有的话)。_ 这是令人遗憾的，因为现在许多科学结论都是堆积如山的代码的结果。

虽然测试代码是发现、修复和防止软件错误的最佳方式，但测试并不便宜。测试代码使我们的结果健壮，但它也花费了我们相当多的时间。不幸的是，对于研究人员来说，为他们编写的每一段代码编写单元测试需要花费太多的时间。科学发展很快，在编写和执行单元测试所需的时间里，您的研究可能会过时或被抢先。更明智的策略是每次编写代码时考虑三个重要的变量: •这个代码被其他代码调用了多少次? •如果这个代码是错误的，它对最终结果的危害有多大? •如果发生错误，会有多明显? 测试一段代码的重要性与前两个变量成正比，与第三个变量成反比(例如，如果一个bug非常明显，那么就没有理由为它编写测试)。我们将在本书的示例中使用这种策略。

### 尽可能使用现有包和库

在每一个崭露头角的程序员的职业生涯中都有一个转折点，当他们觉得写代码足够舒服时，他们会想:“嘿，为什么我要用一个库来做这个，我自己可以很容易地实现这个功能。”你觉得这是一种自信，但是有很好的理由使用现有的软件库来代替你写的内容。

现有的开源库与自己编写的库相比有两个优势:更长的历史和更广泛的受众。这两个优点都可以减少bug。软件中的bug类似于大海捞针的问题。如果你编写自己的软件库(其中必然潜伏着一些bug)，你就是一个人在找几根针。相比之下，开源软件库实际上让更多的人花了更长的时间来寻找这些针。因此，在这些开源库中，bug比自己编写的版本更容易被发现、报告和修复。

一个很好的例子是，在编写将核苷酸翻译成蛋白质的脚本时，可能会出现一个小问题。大多数有编程经验的生物学家可以很容易地编写一个脚本来完成这项任务。但是，在这些简单的编程练习背后，隐藏着你一个人可能不会想到的复杂性。如果你的核苷酸序列中有N/Y/Ws怎么办?Ns, Ys和Ws可能看起来不是有效的碱基，但这些是国际纯粹与应用化学联合会(IUPAC)标准规定的歧义核苷酸，在生物信息学中是完全有效的。在许多情况下，经过严格审查的软件库已经发现并修复了这些隐藏的问题。

### 将数据视为只读

许多科学家花了很多时间使用Excel，不需要眨一下眼睛就可以改变单元格中的值并保存结果。我强烈反对以这种方式修改数据。相反，更好的方法是将所有数据视为只读，只允许程序读取数据并创建新的单独的结果文件。

为什么将数据视为只读在生物信息学中很重要?首先，就地修改数据很容易导致结果损坏。例如，假设你编写了一个直接修改文件的脚本。在处理一个大文件的过程中，脚本遇到错误并崩溃。因为已经修改了原始文件，所以你无法撤消更改并再次尝试(除非有备份)!实际上，这个文件已经损坏，不能再使用了。

其次，当我们修改源文件时，很容易忘记我们是如何修改它的。与每个步骤都有一个输入文件和一个输出文件的工作流不同，直接修改的源文件不会给我们任何提示告诉我们做了什么。如果我们忘记了我们是如何更改文件的，并且没有原始数据的备份副本，那么我们的更改基本上是不可复制的。

对于熟悉在Excel中工作的科学家来说，将数据视为只读似乎是违反直觉的，但这对于稳健的研究是必不可少的(并且可以防止灾难，有助于可重复性)。最初的困难是值得的;除了保护数据免受损坏和不正确的更改之外，它还促进了可重复性。此外，分析的任何步骤都可以很容易地重做，因为输入数据没有被程序更改。

### 花时间把经常使用的脚本开发成工具

在你成为一个训练有素的生物信息学家的发展过程中，你最终会创建一些你会一遍又一遍地使用的脚本。这些脚本可以从数据库中下载数据，或者处理某种类型的文件，或者只是生成相同的漂亮图形。这些脚本可以与实验室成员共享，甚至可以跨实验室共享。你应该投入额外的精力和注意力，使这些高使用或高共享的脚本尽可能健壮。在实践中，我认为这个过程是将一次性脚本转变为工具。

与脚本不同，工具被设计为可以反复运行。它们有良好的文档，有明确的版本控制，有可理解的命令行参数，并且保存在共享的版本控制存储库中。这些可能看起来是微小的细节，但健壮性研究是关于做一些对你有利的小事来防止错误。重复应用于大量数据集的脚本会影响更多的结果，值得进一步开发，使它们更加健壮和用户友好。对于你与其他研究人员共享的脚本尤其如此，他们需要能够查阅文档并将你的工具安全地应用于他们自己的数据。虽然开发工具是一个比编写一次性脚本更费力的过程，但从长远来看，它可以节省时间并防止头痛。

### 让数据证明可靠性

当科学家分析数据时，他们通常会想分析实验数据以得出生物学结论。然而，要进行可靠的生物信息学工作，我们实际上需要分析的不仅仅是实验数据。这包括检查和分析有关实验数据质量、程序生成的中间结果文件，以及模拟测试数据的数据。这样做可以确保数据处理按照我们的预期运行，并体现了生物信息学的黄金法则:不要相信你的工具或数据。

永远不要假设数据集是高质量的。相反，数据的质量应该通过探索性数据分析(称为EDA)来证明。EDA既不复杂也不耗时，而且会让你的研究在面对大型数据集中潜伏的意外时更加稳健。我们将在第8章学习更多关于使用R进行EDA的知识。