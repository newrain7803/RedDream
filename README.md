# -Dream
通过对120章回中主要人物名称出现的频率、虚词的词频、词与词之间的相关性以及前后的写作风格的比较来进行红楼梦作者异同的分析。
针对问题一，我们运用了Python工具分别统计主要人物分别在前八十和后四十出现的频数。我们得出前八十回与后四十回人物的出现频率与情节发展有关，并不能从中看出作者的差异。
针对问题二，我们先对前八十和后四十中出现的虚词和标点符号进行检索，再通过kNN算法对其进行分析，可以明显看出前八十回与后四十回的差异。
针对问题三，我们基于同一句话中两个人物出现的次数来提取人物关系，即若一句话中两个人物出现，则加两个节点name1-name2，weight=1，若以后在其他语句中再出现，则weight+1，以此类推，直到找到所有人物关系节点。分别建立前八十和后四十的人物节点图。
针对问题四，我们在语义用法方面对前八十章与后四十章的“这么”和“那么”进行了分析，并由此得出了其中的差异。
问题重述
文本分析是指对文本的信息及其特征项的选取，是文本挖掘、信息检索的一个基本问题，它把从文本中抽取出的特征词进行量化来表示文本信息。文本（text），与讯息（message）的意义大致相同，指的是由一定的符号或符码组成的信息结构体，这种结构体可采用不同的表现形态，如语言的、文字的、影像的等等。文本是由特定的人制作的，文本的语义不可避免地会反映人的特定立场、观点、价值和利益。因此，由文本内容分析，可以推断文本提供者的意图和目的。
作为中国古典四大名著的《红楼梦》，其影响深远，家喻户晓。历来红学家们都致力于研究《红楼梦》。本文基于Python语言对《红楼梦》中的语言进行一系列的处理，进而从中寻找一种能够推断《红楼梦》作者异同的方法。
判断后四十回是否曹雪芹本人所写是一个典型的文本分类（text category）问题。我们把每一回当成一个独立文本，对全书的一百二十回文本进行分类，若确实能分成两类，那就能说明问题了。
目前有关文本表示的研究主要集中于文本表示模型的选择和特征词选择算法的选取上。用于表示文本的基本单位通常称为文本的特征或特征项。特征项必须具备一定的特性：1)特征项要能够确实标识文本内容；2)特征项具有将目标文本与其他文本相区分的能力；3)特征项的个数不能太多；4)特征项分离要比较容易实现。在中文文本中可以采用字、词或短语作为表示文本的特征项。相比较而言，词比字具有更强的表达能力，而词和短语相比，词的切分难度比短语的切分难度小得多。因此，目前大多数中文文本分类系统都采用词作为特征项，称作特征词。这些特征词作为文档的中间表示形式，用来实现文档与文档、文档与用户目标之间的相似度计算 。如果把所有的词都作为特征项，那么特征向量的维数将过于巨大，从而导致计算量太大，在这样的情况下，要完成文本分类几乎是不可能的。特征抽取的主要功能是在不损伤文本核心信息的情况下尽量减少要处理的单词数，以此来降低向量空间维数，从而简化计算，提高文本处理的速度和效率。文本特征选择对文本内容的过滤和分类、聚类处理、自动摘要以及用户兴趣模式发现、知识发现等有关方面的研究都有非常重要的影响。通常根据某个特征评估函数计算各个特征的评分值，然后按评分值对这些特征进行排序，选取若干个评分值最高的作为特征词，这就是特征选择(Feature Selection)。
因此，我们通过前八十回和后四十回分别建立数学模型，分别从主要人物出现的频率、虚词的词频、词与词之间的相关性以及前后的艺术性来进行比较。
问题分析
本问题主要是通过不同的文本分析角度，建立数学模型，实现对文本的识别，来推断文本提供者的表述方式，意图和目的。
对于问题一，我们通过Python工具分别统计主要人物分别在前八十回和后四十回出现的频数。我们得出前八十回与后四十回作者存在的差异。
针对问题二，我们通过分析前八十和后四十中出现的虚词和标点符号，我们选择了
针对问题三，我们基于同一句话中两个人物出现的次数来提取人物关系，即一句话中两个人物出现，则加两个节点name1-name2，weight=1，若以后在其他语句中再出现，则weight+1，以此类推，直到找到所有人物关系节点。分别建立前八十和后四十的人物节点图。