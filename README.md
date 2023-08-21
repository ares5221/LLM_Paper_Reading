# LLM_Paper_Reading



本文整理了大模型技术（LLM）目前发展历程上最重要的100+论文

其中第一列的🌟表示论文重要程度，星级越高表明越重要。

本文仍在继续更新中，当前更新时间2023/08/20

1. # OpenAI/Google 基础语⾔⼤模型

| **ID** | **Paper**                                                    | **Introduction**                                             |
| ------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 1✡✡✡   | [Improving Language Understanding by Generative Pre-Training](https://www.mikecaptain.com/resources/pdf/GPT-1.pdf) | Open AI GPT原始论⽂提出了解码器架构，以及使用下一个单词预测进行预训练的方法 |
| 2✡✡✡   | [Language Models are Unsupervised Multitask Learners](https://d4mucfpksywv.cloudfront.net/better-language-models/language_models_are_unsupervised_multitask_learners.pdf) | Open AI GPT2原始论⽂GPT-2和后续的GPT-3论文说明了LLM能够进行零样本（Zero-shot）和少样本学习（Few-shot），指出了大型语言模型的**涌现能力** |
| 3✡     | [Emergent Abilities of Large Language Models](https://arxiv.org/abs/2206.07682) | Google 22年8⽉份，探讨⼤语⾔模型的涌现能⼒                   |
| 4✡✡✡✡✡ | [Language Models are Few-Shot Learners](https://arxiv.org/pdf/2005.14165) | Open AI **GPT3原始论⽂**GPT-3仍然是训练当下大语言模型（如ChatGPT）的常用基线和基础模型 |
| 5✡✡✡✡  | [Training language models to follow instructions with human feedback](https://arxiv.org/pdf/2203.02155) | **Open** **AI** **InstructGPT原始论⽂**，也被称为描述ChatGPT背后想法的论文研究人员使用了一种强化学习机制，其中包括人类反馈强化学习方法（RLHF）研究人员从预训练的GPT-3基础模型开始，使用监督学习对人类生成的提示与模型回复进行进一步微调；然后要求人类对模型输出进行排名，以训练奖励模型；最后使用奖励模型通过PPO使用强化学习来更新预训练和微调的GPT-3模型。 |
| 6      | [Evaluating Large Language Models Trained on Code](https://arxiv.org/pdf/2107.03374) | Codex原始论⽂                                                |
| 7✡     | [Exploring the Limits of Transfer Learning with a Unified Text-to-Text Transformer](https://arxiv.org/abs/1910.10683) | Google T5模型，区别于BERT的编码器架构与GPT的解码器架构，T5是transformer的encoder-decoder架构，这是[解读之⼀ ](https://zhuanlan.zhihu.com/p/88438851) |
| 8✡     | [GPT-4 Technical Report](https://arxiv.org/pdf/2303.08774)   | GPT4的技术报告，增加了多模态能⼒                             |

1. # LLM的关键技术：

**核心基石, The Beganing of Story.**

| **ID** | **Paper**                                                    | **Introduction**                                             |
| ------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 1✡✡✡✡✡ | [Attention Is All You Need](https://arxiv.org/pdf/1706.03762) | Transformer原始论⽂提出了由编码器和解码器部分组成的原始Transformer架构，并且文中提出的概念，如缩放点积（scale dot product）注意力机制，多头注意块、位置输入编码等 |

1. ## ICL

"in context learning"（上下文学习）是指在特定上下文环境中学习的机器学习方法。它考虑到文本、语音、图像、视频等数据的上下文环境，以及数据之间的关系和上下文信息的影响。在这种方法中，学习算法会利用上下文信息来提高预测和分类的准确性和有效性。例如，在自然语言处理中，上下文学习可以帮助机器学习算法更好地理解一个句子中的词语含义和关系。

在in-context learning中，模型不根据下游任务调整参数，而是将下游任务的输入输出接起来之后作为prompt，引导模型根据测试集的输入生成预测结果。该方法的表现可以大幅超越零监督学习，并给大模型高效运用提供了新的思路。

in-context learning学习的并不是输入与标注之间的关联，而是通过展示数据形式，来激活预训练模型的能力。也就是提示中的示例使模型可以进入相应的任务模式，然后执行任务。

| **ID** | **Paper**                                                    | **Introduction**                                             |
| ------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 1✡✡✡   | [A Survey on In-context Learning](https://arxiv.org/pdf/2301.00234) | ICL 综述 **[Paper List for In-context Learning](https://github.com/dqxiu/ICL_PaperList)**i[n-context learning 研究梳理：](https://zhuanlan.zhihu.com/p/583028638)[In-Context Learning到底有没有Learning？](https://zhuanlan.zhihu.com/p/626292035) |
| 2✡     | [Rethinking the Role of Demonstrations: What Makes In-Context Learning Work?](https://arxiv.org/pdf/2202.12837) | 当某些标签错误时，模型仍然可以做出正确的预测。这表明模型更受提示的 [格式] 影响，而不是提示的 [意义] 。作者Sewon对这部分内容还做了其他研究[Noisy Channel Language Model Prompting for Few-Shot Text Classification ](https://arxiv.org/pdf/2108.04106.pdf)[MetaICL: Learning to Learn In Context](https://arxiv.org/pdf/2110.15943.pdf) |
| 3✡     | [Why Can GPT Learn In-Context? Language Models Secretly Perform Gradient Descent as Meta-Optimizers](https://arxiv.org/abs/2212.10559) | 这篇⽂章则将ICL看作是⼀种隐式的Fine-tuning，代码地址：https://github.com/microsoft/LMOps[论⽂的解读之⼀：https://mp.weixin.qq.com/s/sTTRl7QPyFDYVw4Jwzn9dQ](https://mp.weixin.qq.com/s?__biz=MzA4MjY4NTk0NQ==&mid=2247508429&idx=1&sn=aed7acb81b941db32cccede3c69b7350&scene=21#wechat_redirect) |
| 4✡     | [Meta-learning via Language Model In-context Tuning](https://arxiv.org/abs/2110.07814) | 将元学习引入到In-Context Learning中                          |
| 5✡     | [WHAT LEARNING ALGORITHM IS IN-CONTEXT LEARNING? INVESTIGATIONS WITH LINEAR MODELS](https://arxiv.org/pdf/2211.15661.pdf) | 神经序列模型，特别是转化器，表现出显著的语境中学习的能力     |
| 5✡✡✡✡  | [Finetuned Language Models Are Zero-Shot Learners](https://arxiv.org/pdf/2109.01652) | 21年9⽉，Google提出FLAN⼤模型，提出**Instruct Learning**     |
| 6✡✡    | [The Flan Collection: Designing Data and Methods for Effective Instruction Tuning](https://arxiv.org/pdf/2301.13688.pdf) | 谷歌介绍大模型指令调优的相关工作，[解读](https://zhuanlan.zhihu.com/p/633346577) |
| 7✡✡✡✡  | [Pre-train, Prompt, and Predict: A Systematic Survey of Prompting Methods in Natural Language Processing](https://arxiv.org/pdf/2107.13586.pdf) | CMU 相关资源 http://pretrain.nlpedia.ai/NLP 的范式演进历程大体经历了这样四个阶段：特征工程—>深度学习—>预训练+精调—>Prompt**Prompt** 是研究者们为了下游任务设计出来的一种输入形式或模板，它能够帮助预训练模型“回忆”起自己在预训练时“学习”到的东西。本文调查并组织了NLP中的一个新范式的研究工作：“基于 prompt 的学习”。 |
| 8✡✡    | [SELF-INSTRUCT: Aligning Language Models with Self-Generated Instructions](https://arxiv.org/pdf/2212.10560.pdf) | 代码地址 https://github.com/yizhongw/self-instruct解读1 https://zhuanlan.zhihu.com/p/614916562解读2 https://zhuanlan.zhihu.com/p/6115704013⽉中旬，斯坦福发布Alpaca：只花100美元，⼈⼈都可微调Meta家70亿参数的LLaMA⼤模型⽽斯坦福团队微调LLaMA的⽅法，便是来⾃华盛顿⼤学Yizhong Wang等去年底提出的这个Self-Instruct具体⽽⾔，论⽂中提出，⾸先从⾃⽣成指令种⼦集中的175个⼈⼯编写的「指令-输出」对开始，然后，提示text-davinci-003使⽤种⼦集作为上下⽂示例来⽣成更多指令⽽斯坦福版Alpaca，就是花了不到500美元使⽤OpenAI API⽣成了5.2万个这样的示例微调LLaMA搞出来的 |
| 9✡     | [Offsite-Tuning: Transfer Learning without Full Model](https://arxiv.org/pdf/2302.04870.pdf) |                                                              |

## 2.2CoT

人类在遇到一系列问题时所产生的推理步骤，而它们的表现形式就是一系列的短句子（比如说在背景介绍中所提到的遇到数学问题时所产生的中间推理步骤）

| **ID** | **Paper**                                                    | **Introduction**                                             |
| ------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 1✡✡✡   | [Chain-of-Thought Prompting Elicits Reasoning in Large Language Models](https://paperswithcode.com/paper/chain-of-thought-prompting-elicits-reasoning) | CoT原始论⽂，印证了instructGPT从22年1⽉份之前 就开始迭代了   |
| 2✡✡✡   | [Large Language Models are Zero-Shot Reasoners](https://openreview.net/pdf?id=e2TBb5y0yFf) | 来⾃东京⼤学和⾕歌的⼯作，关于预训练⼤型语⾔模型的推理能⼒的探究，chain of thought（CoT）能够显著的提升大模型的推理能力，而现有研究工作大都研究的是few shot设置下CoT，因此本文主要研究zero shot设置下的大模型推理能力。[解读](https://zhuanlan.zhihu.com/p/610535012)。“Let's think step by step”的梗即来源于此篇论⽂ |
| 3✡     | [Automatic Chain of thought Prompting in Large Language Models](https://arxiv.org/pdf/2210.03493.pdf) | auto-CoT                                                     |
| 4✡     | [Multimodal Chain-of-Thought Reasoning in Language Models](https://arxiv.org/abs/2302.00923) | 23年2⽉，亚⻢逊的研究者在这篇论⽂⾥提出了基于多模态思维链技术改进语⾔模型复杂推理能⼒的思想 |

## 2.3RLHF

| **ID** | **Paper**                                                    | **Introduction**                                             |
| ------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 1✡✡✡✡✡ | [Fine-Tuning Language Models from Human Preferences](https://arxiv.org/pdf/1909.08593.pdf) | RLHF原始论⽂ [解读](https://huggingface.co/blog/zh/rlhf) 代码 https://github.com/openai/lm-human-preferences相关论文包括在现有 LM 前的 RLHF 进展和基于当前 LM 的 RLHF 工作：[TAMER: Training an Agent Manually via Evaluative Reinforcement](https://www.cs.utexas.edu/~pstone/Papers/bib2html-links/ICDL08-knox.pdf) (Knox and Stone 2008)[Interactive Learning from Policy-Dependent Human Feedback](http://proceedings.mlr.press/v70/macglashan17a/macglashan17a.pdf) (MacGlashan et al. 2017)[Deep TAMER: Interactive Agent Shaping in High-Dimensional State Spaces](https://ojs.aaai.org/index.php/AAAI/article/view/11485)[Learning to summarize with human feedback](https://proceedings.neurips.cc/paper/2020/hash/1f89885d556929e98d3ef9b86448f951-Abstract.html) (Stiennon et al., 2020)[Recursively Summarizing Books with Human Feedback](https://arxiv.org/abs/2109.10862) (OpenAI Alignment Team 2021)[WebGPT: Browser-assisted question-answering with human feedback](https://arxiv.org/abs/2112.09332) (OpenAI, 2021)GopherCite: [Teaching language models to support answers with verified quotes](https://www.deepmind.com/publications/gophercite-teaching-language-models-to-support-answers-with-verified-quotes) (Menick et al. 2022)Sparrow: [Improving alignment of dialogue agents via targeted human judgements](https://arxiv.org/abs/2209.14375) (Glaese et al. 2022)[ChatGPT: Optimizing Language Models for Dialogue](https://openai.com/blog/chatgpt/) (OpenAI 2022)[Scaling Laws for Reward Model Overoptimization](https://arxiv.org/abs/2210.10760) (Gao et al. 2022)[Training a Helpful and Harmless Assistant with Reinforcement Learning from Human Feedback](https://arxiv.org/abs/2204.05862) (Anthropic, 2022)[Red Teaming Language Models to Reduce Harms: Methods, Scaling Behaviors, and Lessons Learned](https://arxiv.org/abs/2209.07858) (Ganguli et al. 2022)[Dynamic Planning in Open-Ended Dialogue using Reinforcement Learning](https://arxiv.org/abs/2208.02294) (Cohen at al. 2022)[Is Reinforcement Learning (Not) for Natural Language Processing?: Benchmarks, Baselines, and Building Blocks for Natural Language Policy Optimization](https://arxiv.org/abs/2210.01241) (Ramamurthy and Ammanabrolu et al. 2022)[Kojima et al. 2021](https://arxiv.org/abs/2108.04812)[Suhr and Artzi 2022](https://arxiv.org/abs/2212.09710)[Sokolov et al. 2016](https://arxiv.org/abs/1601.04468), [Gao et al. 2022](https://arxiv.org/abs/2203.10079)[Ranzato et al. 2015](https://arxiv.org/abs/1511.06732)[Bahdanau et al. 2016](https://arxiv.org/abs/1607.07086)[Nguyen et al. 2017](https://arxiv.org/abs/1707.07402) |
| 2✡✡    | [Deep Reinforcement Learning from Human Preferences](https://arxiv.org/pdf/1706.03741.pdf) | 最早提出的RLHF方法                                           |
| 3✡     | [Trust Region Policy Optimization](https://arxiv.org/abs/1502.05477) | TRPO论文，早于PPO方法，[解读](https://zhuanlan.zhihu.com/p/292361775) |
| 4✡     | [Asynchronous Methods for Deep Reinforcement Learning](https://arxiv.org/pdf/1602.01783.pdf) | 引入了策略梯度方法作为基于深度学习的RL中Q学习的替代方案。    |
| 5✡✡    | [Proximal Policy Optimization Algorithms](https://arxiv.org/pdf/1707.06347) | 2017年，OpenAI发布的PPO原始论⽂提出了一种改进的基于近似策略的强化学习过程，比上面的策略优化算法更具数据效率和可扩展性。 |
| 6✡     | [Fine-Tuning Language Models from Human Preferences ](https://arxiv.org/pdf/1909.08593.pdf) | 论文说明了PPO的概念和对预训练语言模型的奖励学习，包括KL正则化，以防止策略与自然语言偏离太远 |
| 7✡     | [Learning to Summarize from Human Feedback](https://arxiv.org/pdf/2009.01325.pdf) | 论文提出了常用的RLHF三步程序：预训练GPT-3以有监督的方式进行微调同样以有监督的方式训练奖励模型，然后使用具有邻近策略优化的奖励模型来训练微调模型。论文还表明，与常规有监督学习相比，具有近似策略优化的强化学习可以产生更好的模型。 |
| 8✡     | [Scaling Instruction-Finetuned Language Models](https://arxiv.org/pdf/2210.11416.pdf) | 微调PaLM-540B(2022年10⽉)从三个⽅⾯改变指令微调，⼀是改变模型参数，提升到了540B，⼆是增加到了1836个微调任务，三是加上Chain of thought微调的数据 |
|        | [Self-Instruct: Aligning Language Model with Self Generated Instruction](https://arxiv.org/pdf/2212.10560.pdf) | 指令微调是从GPT-3之类的预训练基础模型发展到ChatGPT类更强大语言模型的关键技术。Self-Instruct是一种几乎无需标注，即可将预训练的LLM与指令对齐的方法，总共包括4个步骤：用一组人工编写的指令和样本指令作为种子任务池。使用预训练的语言模型（如GPT-3）来确定任务类别。给定新指令，让预训练的语言模型生成回复。在将回复添加到任务池之前，收集、修剪和筛选这些响应。在实践中，整个过程可以基于ROUGE来评分，可以认为Self-Instruct-finetuned LLM的性能优于GPT-3基础LLM，并且可以与在大型人类编写的指令集上预训练的LLM竞争，self-instruct也可以使已经根据人类指令进行微调的LLM受益。当然，评估语言模型的黄金标准是询问人类评分员。基于人类评估，Self-Instruct优于基本LLM和以监督方式在人类指令数据集上训练的LLM（SuperNI，T0 Trainer），但有趣的是，Self-Instruct并没有优于通过人工反馈强化学习（RLHF）训练的方法。 |
|        | [Illustrating Reinforcement Learning from Human Feedback](https://huggingface.co/blog/rlhf) | huggingface解读RHLF算法                                      |
|        | [Augmenting Reinforcement Learning with Human Feedback](https://www.cs.utexas.edu/users/ai-lab/pubs/ICML_IL11-knox.pdf) | RHLF算法论文                                                 |

## 2.4 PEFT

高效参数微调(Parameter-Efficient Fine-Tuning)

| **ID** | **Paper**                                                    | **Introduction**                                             |
| ------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 1✡✡✡✡  | [Scaling Down to Scale Up: A Guide to Parameter-Efficient Fine-Tuning](https://arxiv.org/pdf/2303.15647.pdf) | 综述回顾了40多篇关于参数高效微调方法，包括prefix调整、adapter和LoRA等。[Parameter-Efficient Fine-Tuning (PEFT)](https://github.com/huggingface/peft) |
| 2✡✡✡✡✡ | [LORA: LOW-RANK ADAPTATION OF LARGE LANGUAGE MODELS](https://arxiv.org/pdf/2106.09685.pdf) | LoRa 微调方法论文在大型数据集上预训练的现代大型语言模型展现出了涌现能力，不过如果想提高Transformer在特定领域数据和特定任务上的性能，那么就需要对Transformer进行微调(SFT)。低秩自适应（LoRA）是一种参数高效（parameter-efficient-PEFT）的方式来微调大型语言模型，相比其他方法，LoRA既优雅又非常通用，可以应用于其他类型的模型。虽然预训练模型的权重在预训练任务上具有满秩，但LoRA作者指出，预训练的大型语言模型在适应新任务时具有较低的「内在维度」。因此，LoRA背后的主要思想是将权重变化ΔW分解为更低秩的表示，即更高效的参数。 |
| 3✡✡✡   | [Prefix-Tuning: Optimizing Continuous Prompts for Generation](https://arxiv.org/pdf/2101.00190.pdf) | Prefix-tuning 微调方法论文                                   |
| 4✡✡    | [GPT Understands, Too](https://arxiv.org/pdf/2103.10385)     | p-tuning V1论⽂                                              |
| 5✡✡✡   | [P-Tuning v2: Prompt Tuning Can Be Comparable to Fine-tuning Universally Across Scales and Tasks](https://arxiv.org/pdf/2110.07602.pdf) | p-tuning V2论⽂                                              |
| 6✡✡✡   | [The Power of Scale for Parameter-Efficient Prompt Tuning](https://arxiv.org/pdf/2104.08691.pdf) | Prompt Tuning                                                |
|        |                                                              |                                                              |

## 2.5 Embedding/位置编码/激活函数/attention加速

| **ID** | **Paper**                                                    | **Introduction**                                             |
| ------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 1✡     | [Distributed Representations of Sentences and Documents](https://arxiv.org/pdf/1405.4053.pdf) | Mikolov⾸次提出 Word2vec                                     |
| 2✡     | [Efficient estimation of word representations in vector space](https://arxiv.org/pdf/1301.3781.pdf) | Mikolov专⻔讲训练 Word2vec 中的两个trick：hierarchical softmax 和 negative sampling |
| 3✡     | [word2vec Explained: deriving Mikolov et al.'s negative-sampling word-embedding method](https://arxiv.org/pdf/1402.3722.pdf) | Yoav Goldberg关于word2vec的论⽂，对 negative-sampling 的公式推导⾮常完备 |
| 4✡     | [word2vec Parameter Learning Explained](https://arxiv.org/pdf/1411.2738.pdf) | Xin Rong关于word2vec的论⽂，⾮常不错                         |
| 5✡✡    | [ROFORMER: ENHANCED TRANSFORMER WITH ROTARY POSITION EMBEDDING](https://arxiv.org/pdf/2104.09864.pdf) | 旋转位置嵌⼊(RoPE)论⽂，[这是苏剑林本⼈对它的解读](https://kexue.fm/archives/8265) |
| 6✡✡    | [Linearized Relative Positional Encoding](https://openreview.net/pdf?id=xoLyps2qWc) | 统⼀了适⽤于linear transformer的相对 位置编码                |
| 7✡✡✡   | [SEARCHING FOR ACTIVATION FUNCTIONS](https://arxiv.org/pdf/1710.05941.pdf) | SwiGLU的原始论⽂                                             |
| 8✡     | [The Natural Language Decathlon: Multitask Learning as Question Answering](https://arxiv.org/pdf/1806.08730.pdf) | GPT-1、GPT-2论⽂的引⽤⽂献，Salesforce发表的⼀篇⽂章，写出了多任务单模型的根本思想 |
| 9✡✡    | [ZeRO: Memory Optimizations Toward Training Trillion Parameter Models](https://arxiv.org/pdf/1910.02054.pdf) | ZeRO是微软deepspeed的核⼼，这是关于ZeRO的[解读之⼀](https://basicv8vc.github.io/posts/zero/) |
| 10✡    | [Efficient Large-Scale Language Model Training on GPU Clusters Using Megatron-LM](https://arxiv.org/pdf/2104.04473.pdf) | Megatron-LM 论⽂原始论⽂对相关技术的解读：[千亿参数开源⼤模型 BLOOM 背后的技术](https://huggingface.co/blog/zh/bloom-megatron-deepspeed) |
| 11✡    | [Training Deep Nets with Sublinear Memory Cost](https://arxiv.org/pdf/1604.06174.pdf) | 提出了一种减少深度神经网络训练时内存消耗的系统性方法。       |
| 12✡✡   | [FlashAttention: Fast and Memory-Efficient Exact Attention with IO-Awareness](https://arxiv.org/pdf/2205.14135.pdf) | Flash attention 这是其[解读之⼀](https://zhuanlan.zhihu.com/p/639228219)虽然大多数transformer论文都没有替换原始的缩放点积机制来改进自注意力，但FlashAttention是其中最常引用的一种机制。 |
| 13✡    | [Fast Transformer Decoding: One Write-Head is All You Need](https://arxiv.org/pdf/1911.02150.pdf) | Muti Query Attention论⽂，MQA 是 19 年提出的⼀种新的 Attention 机制，其能够在保证模型效果的同时加快 decoder ⽣成 token 的速度，这是其[解读之⼀](https://zhuanlan.zhihu.com/p/634236135) |
| 14✡✡   | [GQA: Training Generalized Multi-Query Transformer Models fromMulti-Head Checkpoints](https://arxiv.org/pdf/2305.13245.pdf) | GQALLaMA-2 使用了该技术来加速                                |
| 15✡    | [Cramming: Training a Language Model on a Single GPU in One Day](https://arxiv.org/pdf/2212.14034.pdf) | 在这篇论文中，研究人员使用单个GPU用了24个小时训练了一个遮罩语言模型/编码器风格的语言模型，在单个GPU上进行24小时，相比之下，2018年BERT刚提出来的时候，在16个TPU上训练了四天。有趣的结论是，虽然较小的模型具有更高的吞吐量，但小模型的学习效率也比较低，所以较大的模型不需要更多的训练时间来达到特定的预测性能阈值。 |
| 16✡✡   | [Scaling Language Models: Methods, Analysis & Insights from Training Gopher](https://arxiv.org/pdf/2112.11446.pdf) | Gopher论文中有大量的分析来理解大型语言模型的训练过程。研究人员在3000亿个token上训练了一个80层、2800亿参数的模型，还提出了一些架构上的修改，如使用RMSNorm（均方根归一化）而非LayerNorm（层归一化）。LayerNorm和RMSNorm都优于BatchNorm，因为它们并不依赖于batch size，也不需要同步，对于在batch size较小的分布式设置中是一个优势，而且RMSNorm通常被认为可以稳定更深层次架构中的训练。这篇论文的主要重点是不同尺度（sacle）模型在任务性能上的分析。对152个不同任务的评估表明，增加模型尺寸对理解、事实核查和有毒语言识别等任务的益处最大，而与逻辑和数学推理相关的任务从架构扩展中受益较少。 |
| 17✡✡   | [Training Compute-Optimal Large Language Models](https://arxiv.org/pdf/2203.15556.pdf) | 论文中定义了大型语言模型训练的线性缩放律（linear scaling low），例如虽然Chinchilla的大小只有GPT-3的一半，但它的表现优于GPT-3，因为它是在1.4万亿（而不是3000亿）个token上训练的。换句话说，训练语料中token的数量与模型大小一样重要。 |
| 18     | [Transformer-XL: Attentive language models beyond a fixed-length context](https://arxiv.org/pdf/1901.02860.pdf) |                                                              |

## 2.6 综述及其他

| **ID** | **Paper**                                                    | **Introduction**                                             |
| ------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 1✡✡    | [Deep Residual Learning for Image Recognition](https://openaccess.thecvf.com/content_cvpr_2016/papers/He_Deep_Residual_Learning_CVPR_2016_paper) | ResNet论⽂这是[李沐针对ResNet的解读](https://www.bilibili.com/video/BV1P3411y7nn/?vd_source=0534c0954ddd3d4c4bd8113d31975f6a)，另 这是李[沐针对⼀些paper的解读列表](https://github.com/mli/paper-reading) |
| 2✡✡    | [BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding](https://arxiv.org/pdf/1810.04805.pdf) | BERT论文提出了遮罩语言建模(Mask LM)，并且下一句预测（next-sentence prediction）仍然是一种有影响力的解码器架构，不过后续的RoberTa删除了下一句预测任务，简化了预训练目标。 |
| 3✡✡    | [BART: Denoising Sequence-to-Sequence Pre-training for Natural Language Generation, Translation, and Comprehension](https://arxiv.org/pdf/1910.13461.pdf) | BERT类语言模型主要关注编码器，通常是预测建模任务的首选，而GPT类型的解码器风格的语言模型在文本生成方面更好。为了同时利用二者的优势，BART论文结合了编码器和解码器部分。 |
| 4✡✡    | [Efficient Transformers: A Survey](https://arxiv.org/pdf/2009.06732.pdf) | 综述报告，关于提高Transformer效率的各种技术-1。主要针对一类X-former模型，例如Reformer, Linformer, Performer, Longformer为例，这些对原版Transformer做了改进，提高了其计算和内存的效率。 |
| 5✡✡    | [A Survey on Efficient Training of Transformers](https://arxiv.org/pdf/2302.01107.pdf) | 综述报告，关于提高Transformer效率的各种技术。                |
| 6✡✡    | [Harnessing the Power of LLMs in Practice: A Survey on ChatGPT and Beyond](https://arxiv.org/pdf/2304.13712.pdf) | 综述报告，说明了不同的架构是如何演变的，提供了LLM family tree除了讨论BERT风格的遮罩语言模型（编码器）和GPT风格的自回归语言模型（解码器）之外，还提供了关于预训练和微调数据的讨论和指导。 |
| 7✡✡    | [Unifying Large Language Models and Knowledge Graphs: A Roadmap](https://arxiv.org/pdf/2306.08302.pdf) | LLM与知识图谱的结合实战                                      |
| 8✡✡    | [A Comprehensive Survey on Pretrained Foundation Models: A History from BERT to ChatGPT](https://arxiv.org/pdf/2302.09419.pdf) | 预训练基础模型的演变史                                       |
| 9✡✡    | [Pre-Trained Models: Past, Present and Future](https://arxiv.org/pdf/2106.07139v3.pdf) | 21年1⽉初在CCF启智会⽀持下，⽂继荣、唐杰和⻩⺠烈三位⽼师召集了以预训练模型为主题的闭⻔研讨会，此后22位⽼师和同学经过近半年准备，共同形成了这篇43⻚的综述和观点⽂章 Pre-Trained Models: Past, Present and Future |

1. # 大模型与多模态相关

| **ID** | **Paper**                                                    | **Introduction**                                             |
| ------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 1✡     | [BEiT: BERT Pre-Training of Image Transformers](https://arxiv.org/pdf/2106.08254.pdf) |                                                              |
| 2✡     | [BEiT v2: Masked Image Modeling with Vector-Quantized Visual Tokenizers](https://arxiv.org/pdf/2208.06366.pdf) |                                                              |
| 3✡     | [Image as a Foreign Language: BEIT Pretraining for All Vision and Vision-Language Tasks](https://arxiv.org/pdf/2208.10442.pdf) | 这是针对该论⽂的[解读之⼀](https://www.msra.cn/zh-cn/news/features/beit-3)2022年8⽉，微软提出的多模态预训练模型BEiT-3 |
| 4✡     | [Language Is Not All You Need: Aligning Perception with Language Models](https://arxiv.org/pdf/2302.14045.pdf) | 微软23年3⽉1⽇发布的多模态⼤语⾔模型Kosmos-1的论⽂           |
| 5✡     | [PaLM-E: An Embodied Multimodal Language Model](https://palm-e.github.io/assets/palm-e.pdf) | https://palm-e.github.io/Google于23年3⽉6⽇发布的关于多模态LLM：PaLM-E，可让能听懂⼈类指令且具备视觉能⼒的机器⼈⼲活 |
| 6✡     | [Visual ChatGPT: Talking, Drawing and Editing with Visual Foundation Models](https://arxiv.org/pdf/2303.04671.pdf) | Visual ChatGPT                                               |
| 7✡     | [MiniGPT-4: Enhancing Vision-language Understanding with Advanced Large Language Models](https://arxiv.org/pdf/2304.10592.pdf) | https://minigpt-4.github.io/https://github.com/Vision-CAIR/MiniGPT-4/tree/main |
| 8✡     | [Flamingo: a visual language model for few-shot learning](https://arxiv.org/pdf/2204.14198.pdf) |                                                              |
| 9✡     | [Tensor Programs V: Tuning Large Neural Networks via Zero-Shot Hyperparameter Transfer](https://arxiv.org/pdf/2203.03466.pdf) |                                                              |
| 10✡✡   | [End-to-End Object Detection with Transformers](https://arxiv.org/pdf/2005.12872.pdf) | DETR by 2020年5⽉，这是针对DETR的[解读之⼀](https://www.bilibili.com/video/BV1GB4y1X72R/?spm_id_from=888.80997.embed_other.whitelist)目标检测任务模型演化路线：[一文读懂目标检测：R-CNN、Fast R-CNN、Faster R-CNN、YOLO、SSD](https://blog.csdn.net/v_july_v/article/details/80170182)2014 R-CNN2015 Fast R-CNN、Faster R-CNN2016 YOLO、SSD2017 Mask R-CNN、YOLOv22018 YOLOv32019 CenterNet2020.6 DETR从2020年开始，进入多模态 [从VAE、扩散模型DDPM、DETR到ViT/MAE/Swin transformer](https://blog.csdn.net/v_JULY_v/article/details/130361959) |
| 11✡✡✡  | [Denoising Diffusion Implicit Models](https://arxiv.org/pdf/2010.02502.pdf) | 2020.10⽉ DDIM                                               |
| 12✡✡✡  | [AN IMAGE IS WORTH 16X16 WORDS: TRANSFORMERS FOR IMAGE RECOGNITION AT SCALE](https://arxiv.org/pdf/2010.11929.pdf) | Vision Transformer，本文为ViT模型论文，表示可以完全抛弃卷积思路处理CV任务，同样使用Transformer来完成，CV和NLP殊途同归 |
| 13✡✡✡  | [Learning Transferable Visual Models From Natural Language Supervision](https://arxiv.org/pdf/2103.00020.pdf) | CLIP由OpenAI在2021年1⽉发布，超⼤规模模型预训练提取视觉特征，图⽚和⽂本之间的对⽐学习(简单粗暴理解就是发微博/朋友圈时，⼈喜欢发⼀段⽂字然后再配⼀张或⼏张图，CLIP便是学习这种对应关系)。[解读之一](https://www.bilibili.com/video/BV1SL4y1s7LQ/?vd_source=02a7bf3dbb14104d4c31a9017ba6bd89)https://github.com/openai/CLIP [CLIP: Connecting Text and Images](https://openai.com/research/clip)2021年10⽉，Accomplice发布的disco diffusion，便是第⼀个结合CLIP模型和diffusion模型的AI开源绘画⼯具，其内核便是采⽤的CLIP引导扩散模型(CLIP-Guided diffusion model)且后续有很多基于CLIP的⼀系列改进模型，⽐如[Lseg](http://bilibili.com/video/BV1FV4y1p7Lm/?spm_id_from=333.788.recommend_more_video.0&vd_source=02a7bf3dbb14104d4c31a9017ba6bd89)、[GroupViT](https://www.bilibili.com/video/BV1FV4y1p7Lm/?spm_id_from=333.788.recommend_more_video.0&vd_source=02a7bf3dbb14104d4c31a9017ba6bd89)、[ViLD](https://www.bilibili.com/video/BV1FV4y1p7Lm/?spm_id_from=333.788.recommend_more_video.0&vd_source=02a7bf3dbb14104d4c31a9017ba6bd89)、[GLIP](https://www.bilibili.com/video/BV1FV4y1p7Lm/?spm_id_from=333.788.recommend_more_video.0&vd_source=02a7bf3dbb14104d4c31a9017ba6bd89) |
| 14✡✡✡✡ | [Zero-Shot Text-to-Image Generation](https://arxiv.org/pdf/2102.12092.pdf) | DALL·E原始论⽂                                               |
| 15✡    | [Swin Transformer: Hierarchical Vision Transformer using Shifted Windows](https://arxiv.org/pdf/2103.14030.pdf) | 3⽉ Swin Transformer [解读之一](https://www.bilibili.com/video/BV13L4y1475U/?vd_source=0534c0954ddd3d4c4bd8113d31975f6a) |
| 16✡    | [Swin Transformer V2: Scaling Up Capacity and Resolution](https://arxiv.org/pdf/2111.09883.pdf) | Swin Transformer V2 解读之一                                 |
| 17✡    | [Auto-Encoding Variational Bayes](https://arxiv.org/pdf/1312.6114.pdf) | 苏剑林关于VAE的[解读之⼀](https://kexue.fm/archives/5253)另外⼀个作者：[基于苏这个VAE的解读对扩散模型的理解](https://zhuanlan.zhihu.com/p/563543020) |
| 18✡✡   | [Denoising Diffusion Probabilistic Models](https://arxiv.org/pdf/2006.11239.pdf) | 2020年6⽉提出DDPM，即众⼈⼝中常说的diffusion model这是苏剑林[关于DDPM的相对通俗的系列解读](https://kexue.fm/search/DDPM/1/)另⼀份解读：[What are Diffusion Models?(该解读的中⽂笔记)](https://lilianweng.github.io/posts/2021-07-11-diffusion-models/#forward-diffusion-process) |
| 19✡✡   | [BLIP: Bootstrapping Language-Image Pre-training for Unified Vision-Language Understanding and Generation](https://arxiv.org/pdf/2201.12086.pdf) | 2022年1⽉ BLIPSalesforce                                     |
| 20✡✡   | [Hierarchical Text-Conditional Image Generation with CLIP Latents](https://arxiv.org/pdf/2204.06125.pdf) | 2022年4⽉ DALL·E 2，[解读之一](https://www.bilibili.com/video/BV17r4y1u77B/?spm_id_from=333.788&vd_source=02a7bf3dbb14104d4c31a9017ba6bd89)通过CLIP + Diffusion models，达到⽂本⽣成图像新⾼度 |
| 21✡✡✡✡ | [High-Resolution Image Synthesis with Latent Diffusion Models](https://arxiv.org/pdf/2112.10752.pdf) | 2022年8⽉发布的Stable Diffusion基于Latent Diffusion Models，专⻔⽤于⽂图⽣成任务这些是相关解读：[图解stable diffusion(翻译版之⼀)](https://jalammar.github.io/illustrated-stable-diffusion/)、这是[另⼀解读](https://zhuanlan.zhihu.com/p/583124756)，这⾥有篇[AI绘画发展史](https://mp.weixin.qq.com/s?__biz=MzIxODUzNTg2MA==&mid=2247483967&idx=1&sn=0a78b6e69486de29b89272fa14392949&chksm=97e840e4a09fc9f2a99a482e5cc860c38d5b50d31cabbf190e21787dabcdf0d5894d161a1359&mpshare=1&scene=23&srcid=0312mEP6h7CabVqXw6DqLR4j&sharer_sharetime=1678633719409&sharer_shareid=8dff0e13d79dbe85e759d04101e63bbf#rd)的总结Stable Diffusion和之前的Diffusion扩散化模型相⽐, 重点是做了⼀件事, 那就是把模型的计算空间，从像素空间经过数学变换，在尽可能保留细节信息的情况下降维到⼀个称之为潜空间(Latent Space)的低维空间⾥，然后再进⾏繁重的模型训练和图像⽣成计算 |
| 22✡✡   | [BLIP-2: Bootstrapping Language-Image Pre-training with Frozen Image Encoders and Large Language Models](https://arxiv.org/pdf/2301.12597.pdf) | 2023年1⽉ BLIP2Salesforce                                    |
| 23✡✡   | [Aligning Text-to-Image Models using Human Feedback](https://arxiv.org/pdf/2302.12192.pdf) | ChatGPT的主要成功要归结于采⽤RLHF来精调LLM，近⽇⾕歌AI团队将类似的思路⽤于⽂⽣图⼤模型：基于⼈类反馈（Human Feedback）来精调Stable Diffusion模型来提升⽣成效果⽬前的⽂⽣图模型虽然已经能够取得⽐较好的图像⽣成效果，但是很多时候往往难以⽣成与输⼊⽂本精确匹配的图像，特别是在组合图像⽣成⽅⾯。为此，⾕歌最新的论⽂提出了基于⼈类反馈的三步精调⽅法来改善这个问题 |
| 24✡✡   | [InstructBLIP: Towards General-purpose Vision-Language Models with Instruction Tuning](https://arxiv.org/pdf/2305.06500v1.pdf) | 23年5⽉发布的InstructBLIP论⽂，这是其[解读之一](https://aijishu.com/a/1060000000403483) |
| 25✡    | [LAVIS: A Library for Language-Vision Intelligence](https://arxiv.org/pdf/2209.09019.pdf) | Salesforce开源⼀站式视觉语⾔学习框架LAVIS，这是其GitHub地址：https://github.com/salesforce/LAVIS |
| 26✡    | [MME: A Comprehensive Evaluation Benchmark for Multimodal Large Language Models](https://arxiv.org/pdf/2306.13394.pdf) | 对各种多模态模型的评测，这是其[解读之⼀](https://mp.weixin.qq.com/s?__biz=MzI3MTA0MTk1MA==&mid=2652347745&idx=3&sn=76b3a814bcc6ccb37406533ed0480b48&chksm=f124e990c6536086a799e24d957e5aa20af33d8aa83d8c826902c8cf3867fff0bb01a8ea5ac0&mpshare=1&scene=23&srcid=0712TK888nWW6AbQGmdGlLdz&sharer_sharetime=1689177014339&sharer_shareid=8dff0e13d79dbe85e759d04101e63bbf#rd) |
| 27✡✡✡  | [Segment Anything](https://scontent-hkg4-1.xx.fbcdn.net/v/t39.2365-6/10000000_900554171201033_1602411987825904100_n.pdf?_nc_cat=100&ccb=1-7&_nc_sid=3c67a6&_nc_ohc=mmvtlZMA04wAX-RwgTa&_nc_ht=scontent-hkg4-1.xx&oh=00_AfBuHxlkg_suWaHlbfcxnHKk3OlAF2H70izO36Hx3wlHhg&oe=64E10CA7) | 23年4.6⽇，Meta发布史上⾸个图像分割基础模型SAM，将NLP领域的prompt范式引进CV，让模型可以通过prompt⼀键抠图 |
| 28✡    | [A Comprehensive Survey on Segment Anything Model for Vision and Beyond](https://arxiv.org/pdf/2305.08196.pdf) | 对分割⼀切模型SAM的⾸篇全⾯综述：28⻚、200+篇参考⽂献，这是其[中⽂介绍链接](https://mp.weixin.qq.com/s?__biz=MzA3MzI4MjgzMw==&mid=2650877786&idx=2&sn=7264a23e74fc81daaac7fae0de247941&chksm=84e4eb24b39362325b30d718124cca7c70325f9cdd771fbc1166d300d2a767177d11cb691462&mpshare=1&scene=23&srcid=0522z3SBExD0DdKqKoXQL8R2&sharer_sharetime=1684766416477&sharer_shareid=8dff0e13d79dbe85e759d04101e63bbf%23rd) |
| 29✡    | [Fast Segment Anything](https://arxiv.org/pdf/2306.12156.pdf) | 中科院版的分割⼀切，这是[FastSAM的解读之⼀](https://www.36kr.com/p/2319699358433664) |
| 30✡    | [FASTER SEGMENT ANYTHING: TOWARDS LIGHTWEIGHT SAM FOR MOBILE APPLICATIONS](https://arxiv.org/pdf/2306.14289.pdf) | ⽐SAM⼩60倍，⽐FastSAM快4倍，速度和效果双赢                  |

1. # 类ChatGPT及垂域版类ChatGPT开源模型

| **ID**  | **Paper**                                                    | **Introduction**                                             |
| ------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 1✡✡     | **LaMDA**: [Language Models for Dialog Applications](https://arxiv.org/pdf/2201.08239) | Google LaMDA模型，参数137B，transformer decoder架构，这是[简要解读之⼀](https://zhuanlan.zhihu.com/p/573654291)在微调阶段 使⽤58K的对话数据，过程类似真⼈的对话过程，给定⼀个Query，⽐如 How old is Rafael Nadal? ，如果⼈知道答案，那么直接回答35岁即可，如果不知道，则需要去 Research ⼀下，借助搜索引擎找到答案，然后再回答35岁**ChatGPT****的替代方案** |
| 2✡      | [PaLM: Scaling Language Modeling with Pathways](https://arxiv.org/pdf/2204.02311) | 22年3⽉，Google的Barham等⼈发布了Pathways系统，⽤于更⾼效地训练⼤型模型；Pathways 的愿景是实现⼀个很接近⼈脑的框架：⼀个模型，可以做多任务，多模态且在做任务时，只是 sparsely activated，只使⽤⼀部分的参数22年4⽉，Google发布PaLM模型，基于Transformer decoder架构，参数规模达540B，使⽤multi-query注意⼒、SwiGLU激活函数以及RoPE位置嵌⼊，这是[翻译之⼀](https://zhuanlan.zhihu.com/p/503968575)PaLM⾸次展示了Pathways的⼤规模使⽤——能够以⾼效的⽅式在数千或数万个加速器芯⽚上训练⼀个模型 |
| 3✡      | [Constitutional AI: Harmlessness from AI Feedback](https://arxiv.org/pdf/2212.08073) | ChatGPT的竞品，ChatGPT⽤⼈类偏好训练RM再RL(即RLHF)，Claude则基于AI偏好模型训练RM再RL(即RLAIF) ，研究人员将对齐思想更进一步，提出了一种创建无害AI系统的训练机制，提出了一种基于规则列表（由人类提供）的自训练机制，而非人类监督。从技术上来说，Consitutinal AI使用的是AI反馈而非人类反馈。 |
| 4✡      | [Improving alignment of dialogue agents via targeted human judgements](https://arxiv.org/pdf/2209.14375) | DeepMind的Sparrow，这个⼯作发表时间稍晚于instructGPT，其⼤致的技术思路和框架与 instructGPT 的三阶段基本类似，但Sparrow 中把奖励模型分为两个不同 RM 的思路**ChatGPT****的替代方案** |
| 5✡      | [Crosslingual Generalization through Multitask Finetuning](https://arxiv.org/pdf/2211.01786.pdf) | **ChatGPT****的替代方案**                                    |
| 6✡      | [LLaMA: Open and Efficient Foundation Language Models](https://scontent-hkg4-1.xx.fbcdn.net/v/t39.8562-6/333078981_693988129081760_4712707815225756708_n.pdf?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=iVbwJKA_j4MAX-6b3k4&_nc_ht=scontent-hkg4-1.xx&oh=00_AfCWx7Ip8eypOwJrdtL-cD4lezDdlN8TbWQnXmz8YeAn4w&oe=64E14022) | 2023年2⽉24⽇Meta发布了全新的65B参数⼤语⾔模型LLaMA，开源，⼤部分任务的效果好于2020年的GPT-3 |
| 7✡✡✡    | [Alpaca: A Strong Open-Source Instruction-Following Model](https://crfm.stanford.edu/2023/03/13/alpaca.html) | alpaca论文https://github.com/tatsu-lab/stanford_alpaca       |
| 8✡✡✡    | [Vicuna: An Open-Source Chatbot Impressing GPT-4 with 90%* ChatGPT Quality](https://lmsys.org/blog/2023-03-30-vicuna/) | Vicuna论文                                                   |
| 9✡✡✡    | [GLM: General Language Model Pretraining with Autoregressive Blank Infilling](https://arxiv.org/pdf/2103.10360.pdf) | https://zhuanlan.zhihu.com/p/6294619542022年5⽉，正式提出了GLM框架 |
| 10✡✡✡   | [GLM-130B: AN OPEN BILINGUAL PRE-TRAINED MODEL](https://arxiv.org/pdf/2210.02414.pdf) | GLM-130B便是基于的GLM框架的⼤语⾔模型                        |
| 11✡✡✡✡✡ | [ChatGLM-6B](https://github.com/THUDM/ChatGLM-6B)            | ChatGLM-6B 是一个开源的、支持中英双语的对话语言模型，基于 [General Language Model (GLM)](https://github.com/THUDM/GLM) 架构，具有 62 亿参数。结合模型量化技术，用户可以在消费级的显卡上进行本地部署（INT4 量化级别下最低只需 6GB 显存）。 ChatGLM-6B 使用了和 ChatGPT 相似的技术，针对中文问答和对话进行了优化。经过约 1T 标识符的中英双语训练，辅以监督微调、反馈自助、人类反馈强化学习等技术的加持，62 亿参数的 ChatGLM-6B 已经能生成相当符合人类偏好的回答，更多信息请参考我们的[博客](https://chatglm.cn/blog)。欢迎通过 [chatglm.cn](https://chatglm.cn/) 体验更大规模的 ChatGLM 模型。 |
| 12✡     | [Opt: Open pre-trained transformer language models](https://arxiv.org/pdf/2205.01068.pdf) | GPT开源平替                                                  |
| 13✡     | [BLOOM: A 176B-Parameter Open-Access Multilingual Language Model](https://arxiv.org/pdf/2211.05100.pdf) | GPT开源平替                                                  |
| 14✡     | [UL2: Unifying Language Learning Paradigms](https://arxiv.org/pdf/2205.05131.pdf) | GPT开源平替                                                  |
| 15✡     | [Large Language Models Encode Clinical Knowledge](https://arxiv.org/pdf/2212.13138.pdf) | 从palm - flan palm(指令微调palm模型) - instruction prompt-tuned Flan-PaLM(提示指令调优flan-palm模型)的过程中，通过instruction prompt-tuned Flan-PaLM得到医疗问答模型med-palm，⽽提出了instruction prompt tuning |
| 16✡     | [Towards Expert-Level Medical Question Answering with Large Language Models](https://arxiv.org/pdf/2305.09617.pdf) | 继上篇论⽂提出medpalm之后，5⽉16⽇，Google Research和DeepMind发布了Med-PaLM 2，相⽐第⼀代最显著的改进是基座模型换成了Google的最新⼤模型PaLM2(据说有着340b参数，⽤于训练的token数达3.6万亿) |
| 17✡     | [ChatDoctor: A Medical Chat Model Fine-Tuned on a Large Language Model Meta-AI (LLaMA) Using Medical Domain Knowledge](https://arxiv.org/pdf/2303.14070.pdf) | 医疗ChatDoctor论⽂                                           |
| 18✡✡    | [BloombergGPT: A Large Language Model for Finance](https://arxiv.org/pdf/2303.17564.pdf) | ⾦融BloombergGPT论⽂，这是其[解读之⼀](https://zhuanlan.zhihu.com/p/619444812) |
| 19✡     | [COLT5: Faster Long-Range Transformers with Conditional Computation](https://arxiv.org/pdf/2303.09752.pdf) |                                                              |
| 20✡     | [ProtTrans：Towards Cracking the Language of Life’s Code Through Self-Supervised Deep Learning and High Performance Computing](https://arxiv.org/pdf/2007.06225.pdf) |                                                              |
| 21✡     | [Highly accurate protein structure prediction with AlphaFold](https://www.nature.com/articles/s41586-021-03819-2) |                                                              |
| 22✡     | [Large Language Models Generate Functional Protein Sequences Across Diverse Families](https://www.nature.com/articles/s41587-022-01618-2) |                                                              |
| 23✡     | [Pythia: A Suite for Analyzing Large Language Models Across Training and Scaling](https://arxiv.org/pdf/2304.01373.pdf) | Pythia是一组开源的大型语言模型，参数量从7千万到120亿不等，以用于研究大型语言模型在训练过程中的演变模型架构类似于GPT-3，但包括一些组件改进，例如用Flash Attention和Rotary Positional Embeddings。Pythia研究的主要结论如下：在重复数据上进行训练（超过1个epoch）不会提升或降低性能。训练顺序不会影响记忆。这个结论让我们无法通过重新排序训练数据来缓解不希望的逐字记忆问题。预训练词频影响任务性能。例如，对于更频繁的术语，少样本学习往往准确度更高。将batch size加倍可以将训练时间减半，但不会影响收敛。 |