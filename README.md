---
title: "Natural Language Processing"
aliases: ["NLP", "Language Models", "Text Mining"]
tags:
  - nlp
  - deep-learning
  - transformers
  - language-models
---
# Natural Language Processing

## Statistical models and structured prediction

- **Maximum-entropy language models** - Combines observed feature statistics in a probabilistic model and estimates parameters by maximum likelihood. Develops feature selection and estimation procedures for language-processing tasks. [Berger et al. 1996](<https://aclanthology.org/J96-1002/> "A Maximum Entropy Approach to Natural Language Processing; Computational Linguistics").
- **N-gram smoothing comparisons** - Compares smoothing methods across corpora, training sizes, and n-gram orders using held-out cross-entropy. Shows that model settings and data scale affect which estimator works best. [Chen and Goodman 1996](<https://aclanthology.org/P96-1041/> "An Empirical Study of Smoothing Techniques for Language Modeling; ACL").
- **Naive Bayes and SVM baselines** - Studies unigram/bigram features and NB/SVM variants for sentiment and topic classification. Uses NB log-count ratios as SVM features and shows why a precisely specified baseline matters. [Wang and Manning 2012](<https://aclanthology.org/P12-2018/> "Baselines and Bigrams: Simple, Good Sentiment and Topic Classification; ACL").
- **Conditional random fields** - Models label sequences conditional on observations, allowing dependent labels and rich input features. Avoids the label-bias limitation of locally normalized maximum-entropy Markov models. [Lafferty et al. 2001](<https://daiwk.github.io/assets/Conditional%20random%20fields%20Probabilistic%20models%20for%20segmenting%20and%20labeling%20sequence%20data.pdf> "Conditional Random Fields: Probabilistic Models for Segmenting and Labeling Sequence Data; ICML").
- **Neural tagging from learned features** - Uses a shared neural approach for part-of-speech tagging, chunking, entity recognition, and semantic roles. Learns representations from largely unlabeled text instead of engineering separate input features for every task. [Collobert et al. 2011](<https://arxiv.org/abs/1103.0398> "Natural Language Processing (almost) from Scratch; arXiv").
- **Neural dependency parsing** - Uses learned dense features to choose transitions in a greedy dependency parser. Replaces large sparse feature-template sets with compact representations of parsing configurations. [Chen and Manning 2014](<https://aclanthology.org/D14-1082/> "A Fast and Accurate Dependency Parser using Neural Networks; EMNLP").

## Tokenization and word representations

- **Subword translation with BPE** - Represents rare and unseen words as sequences of subword units. Adapts byte-pair encoding to vocabulary construction for translation, reducing dependence on whole-word dictionaries. [Sennrich et al. 2016](<https://arxiv.org/abs/1508.07909> "Neural Machine Translation of Rare Words with Subword Units; ACL").
- **SentencePiece** - Trains subword tokenization directly from raw sentences without requiring prior word segmentation. Provides tokenization and detokenization for languages with different writing conventions. [Kudo and Richardson 2018](<https://arxiv.org/abs/1808.06226> "SentencePiece: A simple and language independent subword tokenizer and detokenizer for Neural Text Processing; arXiv").
- **word2vec** - Learns word vectors through continuous bag-of-words and skip-gram prediction objectives. Produces a reusable vector per vocabulary word; the representation does not change with each sentence context. [Mikolov et al. 2013](<https://arxiv.org/abs/1301.3781> "Efficient Estimation of Word Representations in Vector Space; arXiv").
- **GloVe** - Fits a weighted log-bilinear model to global word co-occurrence statistics. Combines corpus-level counts with vector representations rather than learning only from individual context windows. [Pennington et al. 2014](<https://aclanthology.org/D14-1162/> "GloVe: Global Vectors for Word Representation; EMNLP").
- **fastText subword vectors** - Represents words by sums of character n-gram vectors within a skip-gram model. Can construct vectors for unseen words from their subword components. [Bojanowski et al. 2016](<https://arxiv.org/abs/1607.04606> "Enriching Word Vectors with Subword Information; arXiv").
- **fastText classification** - Uses a simple supervised text-classification architecture with word and n-gram features. Provides a computationally inexpensive baseline distinct from the fastText method for unsupervised word vectors. [Joulin et al. 2016](<https://arxiv.org/abs/1607.01759> "Bag of Tricks for Efficient Text Classification; arXiv").

## Contextual pretraining

- **ELMo** - Builds context-dependent word representations from internal states of a pretrained bidirectional language model. Allows downstream tasks to combine signals from different layers. [Peters et al. 2018](<https://arxiv.org/abs/1802.05365> "Deep contextualized word representations; arXiv").
- **BERT** - Pretrains bidirectional Transformer representations with masked-token prediction and an original next-sentence objective. Fine-tunes the encoder for tasks such as classification and extractive question answering. [Devlin et al. 2019](<https://arxiv.org/abs/1810.04805> "BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding; NAACL").
- **RoBERTa** - Reexamines BERT training choices, data size, and optimization. Demonstrates that training conditions can explain apparent differences between pretraining methods. [Liu et al. 2019](<https://arxiv.org/abs/1907.11692> "RoBERTa: A Robustly Optimized BERT Pretraining Approach; arXiv").
- **XLNet** - Trains autoregressive predictions across permutations of the factorization order to learn bidirectional context. Integrates Transformer-XL mechanisms without using BERT's masked-token objective. [Yang et al. 2019](<https://arxiv.org/abs/1906.08237> "XLNet: Generalized Autoregressive Pretraining for Language Understanding; NeurIPS").
- **ELECTRA** - Trains an encoder to distinguish original tokens from plausible generator replacements. Uses a discrimination target across input positions rather than predicting only the identities of masked tokens. [Clark et al. 2020](<https://arxiv.org/abs/2003.10555> "ELECTRA: Pre-training Text Encoders as Discriminators Rather Than Generators; ICLR").
- **ModernBERT** - Updates bidirectional encoder pretraining with rotary positions and alternating local/global attention; evaluated for classification and both single-vector and late-interaction retrieval. [Warner et al. 2024](<https://arxiv.org/abs/2412.13663> "Smarter, Better, Faster, Longer: A Modern Bidirectional Encoder for Fast, Memory Efficient, and Long Context Finetuning and Inference; arXiv").

## Sequence generation and translation

- **Sequence-to-sequence LSTMs** - Encodes an input sequence into a fixed-dimensional vector and decodes a target sequence with another LSTM. Establishes a jointly trained neural architecture for sequence transduction. [Sutskever et al. 2014](<https://arxiv.org/abs/1409.3215> "Sequence to Sequence Learning with Neural Networks; NeurIPS").
- **Neural attention for translation** - Learns soft alignments so each generated word can depend on relevant source positions. Relieves the fixed-vector bottleneck of early encoder-decoder translation models. [Bahdanau et al. 2015](<https://arxiv.org/abs/1409.0473> "Neural Machine Translation by Jointly Learning to Align and Translate; ICLR").
- **Transformer** - Uses attention-based encoder and decoder layers for sequence transduction, dispensing with recurrence and convolution. Makes interactions between sequence positions explicit through attention. [Vaswani et al. 2017](<https://arxiv.org/abs/1706.03762> "Attention Is All You Need; NeurIPS").
- **T5** - Expresses classification, question answering, translation, and other tasks in a common text-to-text format. Compares pretraining objectives, architectures, datasets, and transfer procedures within that framework. [Raffel et al. 2020](<https://arxiv.org/abs/1910.10683> "Exploring the Limits of Transfer Learning with a Unified Text-to-Text Transformer; JMLR").
- **BART** - Pretrains an encoder-decoder by reconstructing text corrupted with noise, including span masking and sentence reordering. Connects bidirectional encoding with left-to-right generation. [Lewis et al. 2019](<https://arxiv.org/abs/1910.13461> "BART: Denoising Sequence-to-Sequence Pre-training for Natural Language Generation, Translation, and Comprehension; arXiv").

## Multilingual learning

- **XLM-R** - Pretrains a masked language model across 100 languages. Studies cross-lingual transfer and the tradeoff between sharing representations and dividing finite model capacity among languages. [Conneau et al. 2020](<https://arxiv.org/abs/1911.02116> "Unsupervised Cross-lingual Representation Learning at Scale; ACL").
- **mT5** - Extends text-to-text pretraining to multilingual data. Studies cross-lingual task transfer and accidental translation, where generated answers switch away from the requested language. [Xue et al. 2020](<https://arxiv.org/abs/2010.11934> "mT5: A massively multilingual pre-trained text-to-text transformer; arXiv").

## Scaling and in-context learning

- **Language-model scaling laws** - Fits empirical relationships among language-model loss, parameter count, data size, and training compute. Its compute-allocation recommendations depend on the investigated training regime. [Kaplan et al. 2020](<https://arxiv.org/abs/2001.08361> "Scaling Laws for Neural Language Models; arXiv").
- **GPT-3 and few-shot prompting** - Studies task demonstrations supplied in the prompt without task-specific gradient updates. Distinguishes in-context conditioning from fine-tuning and reports limitations alongside successful tasks. [Brown et al. 2020](<https://arxiv.org/abs/2005.14165> "Language Models are Few-Shot Learners; NeurIPS").
- **Compute-optimal training** - Studies how to allocate a fixed training budget between model size and token count. Finds a different allocation from earlier scaling work; the optimum depends on the objective and cost assumptions. [Hoffmann et al. 2022](<https://arxiv.org/abs/2203.15556> "Training Compute-Optimal Large Language Models; arXiv").

## Instruction and preference learning

- **Instruction tuning / FLAN** - Fine-tunes on multiple tasks expressed as natural-language instructions and evaluates unseen task types. Studies how instruction format, task diversity, and model scale affect transfer. [Wei et al. 2021](<https://arxiv.org/abs/2109.01652> "Finetuned Language Models Are Zero-Shot Learners; arXiv").
- **InstructGPT** - Combines supervised demonstrations with preference rankings and reinforcement learning. Studies following instructions on a specified prompt distribution; preference training does not eliminate factual errors. [Ouyang et al. 2022](<https://arxiv.org/abs/2203.02155> "Training language models to follow instructions with human feedback; NeurIPS").
- **Constitutional AI** - Uses written principles to guide model critiques, revised responses, and AI-generated preference feedback. Combines supervised and reinforcement learning while retaining human choices about the principles. [Bai et al. 2022](<https://arxiv.org/abs/2212.08073> "Constitutional AI: Harmlessness from AI Feedback; arXiv").
- **Direct Preference Optimization** - Reparameterizes a reward-based preference objective as direct policy training with a classification loss. Uses preference pairs without a separate reward-model fitting stage or online sampling during fine-tuning. [Rafailov et al. 2023](<https://arxiv.org/abs/2305.18290> "Direct Preference Optimization: Your Language Model is Secretly a Reward Model; NeurIPS").

## Sentence representations and retrieval

- **Sentence-BERT** - Uses siamese and triplet training to produce sentence embeddings comparable by cosine similarity. Enables precomputing candidate representations instead of encoding every sentence pair jointly. [Reimers and Gurevych 2019](<https://arxiv.org/abs/1908.10084> "Sentence-BERT: Sentence Embeddings using Siamese BERT-Networks; EMNLP").
- **SimCSE** - Learns sentence embeddings contrastively using dropout views, or supervised entailment positives and contradiction negatives. Studies how these objectives shape embedding alignment and uniformity. [Gao et al. 2021](<https://arxiv.org/abs/2104.08821> "SimCSE: Simple Contrastive Learning of Sentence Embeddings; EMNLP").
- **Dense Passage Retrieval** - Learns separate question and passage encoders for dense-vector retrieval. Trains from question-passage examples to select contexts for open-domain question answering. [Karpukhin et al. 2020](<https://arxiv.org/abs/2004.04906> "Dense Passage Retrieval for Open-Domain Question Answering; EMNLP").
- **ColBERT** - Encodes query and document tokens separately, then scores fine-grained matches through late interaction. Retains multiple token representations while allowing document encoding before query time. [Khattab and Zaharia 2020](<https://arxiv.org/abs/2004.12832> "ColBERT: Efficient and Effective Passage Search via Contextualized Late Interaction over BERT; SIGIR").
- **SPLADE** - Learns sparse lexical representations with explicit sparsity regularization and saturated term weights. Supports retrieval with inverted indexes and an effectiveness-sparsity tradeoff. [Formal et al. 2021](<https://arxiv.org/abs/2107.05720> "SPLADE: Sparse Lexical and Expansion Model for First Stage Ranking; arXiv").
- **Retrieval-Augmented Generation** - Combines a pretrained sequence generator with a learned retriever and an external passage index. Compares retrieval shared across a response with retrieval varying by token; retrieved context does not guarantee factuality. [Lewis et al. 2020](<https://arxiv.org/abs/2005.11401> "Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks; NeurIPS").
- **RAGTruth** - Annotates unsupported or contradictory spans in nearly 18,000 retrieval-augmented responses. Demonstrates that providing retrieved evidence does not ensure faithful generation; retrieval quality and support for generated claims need separate evaluation. [Niu et al. 2024](<https://aclanthology.org/2024.acl-long.585/> "RAGTruth: A Hallucination Corpus for Developing Trustworthy Retrieval-Augmented Language Models; ACL").
- **Late chunking** - Encodes a longer text before dividing token representations into chunks for pooling. Produces one vector per chunk informed by surrounding context, unlike late-interaction retrieval's multiple stored token vectors. [Günther et al. 2024](<https://arxiv.org/abs/2409.04701> "Late Chunking: Contextual Chunk Embeddings Using Long-Context Embedding Models; arXiv").

## Long-context models

- **Transformer-XL** - Combines segment-level recurrence with a positional encoding scheme to extend context across segments. Reuses prior representations while addressing fragmentation from fixed-length training windows. [Dai et al. 2019](<https://arxiv.org/abs/1901.02860> "Transformer-XL: Attentive Language Models Beyond a Fixed-Length Context; ACL").
- **Longformer** - Combines local sliding-window attention with task-specific global attention. Reduces attention cost for long documents when window size and the number of global positions remain bounded. [Beltagy et al. 2020](<https://arxiv.org/abs/2004.05150> "Longformer: The Long-Document Transformer; arXiv").
- **Lost in the Middle** - Finds position-dependent failures in long-context question answering and key-value retrieval. In the studied models, relevant information near the middle can be harder to use than information near either end. [Liu et al. 2023](<https://arxiv.org/abs/2307.03172> "Lost in the Middle: How Language Models Use Long Contexts; arXiv").

## Decoding and reasoning procedures

- **Nucleus sampling** - Samples from a dynamically selected high-probability portion of the next-token distribution. Studies how decoding changes repetition and diversity even when the underlying language model is unchanged. [Holtzman et al. 2020](<https://arxiv.org/abs/1904.09751> "The Curious Case of Neural Text Degeneration; ICLR").
- **Chain-of-thought prompting** - Supplies worked reasoning examples in the prompt before asking for a solution. Studies arithmetic, commonsense, and symbolic tasks; generated explanations are not themselves a correctness check. [Wei et al. 2022](<https://arxiv.org/abs/2201.11903> "Chain-of-Thought Prompting Elicits Reasoning in Large Language Models; NeurIPS").
- **Self-consistency** - Samples multiple reasoning paths and aggregates their answers instead of choosing one greedy path. Improves the studied reasoning benchmarks at the cost of additional generation. [Wang et al. 2023](<https://arxiv.org/abs/2203.11171> "Self-Consistency Improves Chain of Thought Reasoning in Language Models; ICLR").
- **ReAct** - Interleaves generated reasoning with actions that query external information or interact with an environment. Studies how observations can update task plans instead of relying only on an uninterrupted text completion. [Yao et al. 2022](<https://arxiv.org/abs/2210.03629> "ReAct: Synergizing Reasoning and Acting in Language Models; arXiv").
- **Speculative decoding** - A smaller model drafts tokens that the target model verifies in parallel. A sampling correction preserves the target distribution; speed depends on draft cost and acceptance. [Leviathan et al. 2023](<https://arxiv.org/abs/2211.17192> "Fast Inference from Transformers via Speculative Decoding; ICML").
- **PICARD constrained decoding** - Rejects tokens that violate incremental parsing constraints during generation. Improves validity and text-to-SQL performance on Spider and CoSQL; a syntactically valid query can still answer the wrong question. [Scholak et al. 2021](<https://aclanthology.org/2021.emnlp-main.779/> "PICARD: Parsing Incrementally for Constrained Auto-Regressive Decoding from Language Models; EMNLP").
- **Process supervision** - Trains reward models from human judgments of individual solution steps rather than only final answers; introduces PRM800K for studying process supervision in mathematical reasoning. [Lightman et al. 2023](<https://arxiv.org/abs/2305.20050> "Let&#x27;s Verify Step by Step; arXiv").

## Text-generation metrics

- **BLEU** - Compares generated translations with references using modified n-gram precision and a brevity penalty. A corpus-level overlap metric; it does not directly establish factual or semantic equivalence. [Papineni et al. 2002](<https://aclanthology.org/P02-1040/> "Bleu: a Method for Automatic Evaluation of Machine Translation; ACL").
- **ROUGE** - Evaluates summaries using overlap with reference summaries, including n-grams and sequence-based measures. Different ROUGE variants capture different forms of overlap. [Lin 2004](<https://aclanthology.org/W04-1013/> "ROUGE: A Package for Automatic Evaluation of Summaries; Text Summarization Branches Out").
- **chrF** - Uses character n-gram precision and recall for translation evaluation. Avoids dependence on a particular word tokenizer and exposes a parameter controlling the recall-precision balance. [Popović 2015](<https://aclanthology.org/W15-3049/> "chrF: character n-gram F-score for automatic MT evaluation; WMT").
- **SacreBLEU and reproducibility** - Shows that tokenization and normalization choices can make BLEU scores incomparable. Provides standardized reference processing and reporting to make evaluations easier to reproduce. [Post 2018](<https://arxiv.org/abs/1804.08771> "A Call for Clarity in Reporting BLEU Scores; arXiv").
- **BERTScore** - Matches candidate and reference tokens using contextual embedding similarity rather than exact lexical equality. Measures representation-level agreement; it is not a factuality verifier. [Zhang et al. 2019](<https://arxiv.org/abs/1904.09675> "BERTScore: Evaluating Text Generation with BERT; arXiv").

## Benchmarks and behavioral evaluation

- **SQuAD** - Tests reading comprehension with questions whose answers are spans of the supplied Wikipedia passage. Measures extractive question answering rather than unrestricted open-domain knowledge. [Rajpurkar et al. 2016](<https://arxiv.org/abs/1606.05250> "SQuAD: 100,000+ Questions for Machine Comprehension of Text; EMNLP").
- **MultiNLI** - Provides entailment, contradiction, and neutral sentence pairs across genres of written and spoken English. Includes evaluation of transfer across genres. [Williams et al. 2017](<https://arxiv.org/abs/1704.05426> "A Broad-Coverage Challenge Corpus for Sentence Understanding through Inference; arXiv").
- **GLUE** - Combines language-understanding tasks with a diagnostic suite for linguistic behavior. Encourages shared representations across tasks rather than optimizing a single dataset. [Wang et al. 2019](<https://arxiv.org/abs/1804.07461> "GLUE: A Multi-Task Benchmark and Analysis Platform for Natural Language Understanding; ICLR").
- **SuperGLUE** - Introduces a harder collection of language-understanding tasks following progress on GLUE. Supplies a toolkit and shared evaluation; aggregate scores still combine distinct abilities. [Wang et al. 2019](<https://arxiv.org/abs/1905.00537> "SuperGLUE: A Stickier Benchmark for General-Purpose Language Understanding Systems; NeurIPS").
- **MMLU** - Tests knowledge and problem solving across 57 academic and professional subjects. Supports per-subject analysis; performance on these questions is not a general measure of real-world competence. [Hendrycks et al. 2021](<https://arxiv.org/abs/2009.03300> "Measuring Massive Multitask Language Understanding; ICLR").
- **BIG-bench** - Collects diverse tasks for examining language-model capabilities and scaling. Studies differences across tasks, model sizes, and evaluation metrics instead of treating aggregate improvement as uniform progress. [Srivastava et al. 2022](<https://arxiv.org/abs/2206.04615> "Beyond the Imitation Game: Quantifying and extrapolating the capabilities of language models; TMLR").
- **TruthfulQA** - Tests whether generated answers reproduce common misconceptions. Targets a particular source of falsehood; passing the benchmark does not establish truthfulness on arbitrary questions. [Lin et al. 2022](<https://arxiv.org/abs/2109.07958> "TruthfulQA: Measuring How Models Mimic Human Falsehoods; ACL").
- **HELM** - Evaluates language models across shared scenarios and multiple criteria, including accuracy, calibration, robustness, bias, toxicity, and efficiency. Makes coverage gaps and metric tradeoffs explicit. [Liang et al. 2023](<https://arxiv.org/abs/2211.09110> "Holistic Evaluation of Language Models; TMLR").
- **CheckList** - Organizes behavioral tests by linguistic capability and test type. Uses generated cases to reveal failures that aggregate held-out accuracy can conceal. [Ribeiro et al. 2020](<https://arxiv.org/abs/2005.04118> "Beyond Accuracy: Behavioral Testing of NLP models with CheckList; ACL").

## Software

- **Transformers** - Provides a library of pretrained Transformer architectures and task interfaces. The paper describes reusable implementations for NLP research and applications, rather than a single model release. [Wolf et al. 2019](<https://arxiv.org/abs/1910.03771> "HuggingFace&#x27;s Transformers: State-of-the-art Natural Language Processing; arXiv").
- **Stanza** - Provides a multilingual NLP pipeline for tokenization, morphology, syntax, and named entities. Packages neural processing components for text analysis across languages. [Qi et al. 2020](<https://arxiv.org/abs/2003.07082> "Stanza: A Python Natural Language Processing Toolkit for Many Human Languages; arXiv").

## Related topics

- [Neural Networks](https://mlpapers.org/neural-nets/)
- [Transfer Learning](https://mlpapers.org/transfer-learning/)
- [Generative Models](https://mlpapers.org/generative-models/)
- [Computer Vision](https://mlpapers.org/computer-vision/)
