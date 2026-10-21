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

- **[Maximum-entropy language models](https://aclanthology.org/J96-1002/)** — 1996. Combines observed feature statistics in a probabilistic model and estimates parameters by maximum likelihood. Develops feature selection and estimation procedures for language-processing tasks.
- **[N-gram smoothing comparisons](https://aclanthology.org/P96-1041/)** — 1996. Compares smoothing methods across corpora, training sizes, and n-gram orders using held-out cross-entropy. Shows that model settings and data scale affect which estimator works best.
- **[Naive Bayes and SVM baselines](https://aclanthology.org/P12-2018/)** — 2012. Studies unigram/bigram features and NB/SVM variants for sentiment and topic classification. Uses NB log-count ratios as SVM features and shows why a precisely specified baseline matters.
- **[Conditional random fields](https://daiwk.github.io/assets/Conditional%20random%20fields%20Probabilistic%20models%20for%20segmenting%20and%20labeling%20sequence%20data.pdf)** — 2001. Models label sequences conditional on observations, allowing dependent labels and rich input features. Avoids the label-bias limitation of locally normalized maximum-entropy Markov models.
- **[Neural tagging from learned features](https://arxiv.org/abs/1103.0398)** — 2011. Uses a shared neural approach for part-of-speech tagging, chunking, entity recognition, and semantic roles. Learns representations from largely unlabeled text instead of engineering separate input features for every task.
- **[Neural dependency parsing](https://aclanthology.org/D14-1082/)** — 2014. Uses learned dense features to choose transitions in a greedy dependency parser. Replaces large sparse feature-template sets with compact representations of parsing configurations.

## Tokenization and word representations

- **[Subword translation with BPE](https://arxiv.org/abs/1508.07909)** — 2015. Represents rare and unseen words as sequences of subword units. Adapts byte-pair encoding to vocabulary construction for translation, reducing dependence on whole-word dictionaries.
- **[SentencePiece](https://arxiv.org/abs/1808.06226)** — 2018. Trains subword tokenization directly from raw sentences without requiring prior word segmentation. Provides tokenization and detokenization for languages with different writing conventions.
- **[word2vec](https://arxiv.org/abs/1301.3781)** — 2013. Learns word vectors through continuous bag-of-words and skip-gram prediction objectives. Produces a reusable vector per vocabulary word; the representation does not change with each sentence context.
- **[GloVe](https://aclanthology.org/D14-1162/)** — 2014. Fits a weighted log-bilinear model to global word co-occurrence statistics. Combines corpus-level counts with vector representations rather than learning only from individual context windows.
- **[fastText subword vectors](https://arxiv.org/abs/1607.04606)** — 2016. Represents words by sums of character n-gram vectors within a skip-gram model. Can construct vectors for unseen words from their subword components.
- **[fastText classification](https://arxiv.org/abs/1607.01759)** — 2016. Uses a simple supervised text-classification architecture with word and n-gram features. Provides a computationally inexpensive baseline distinct from the fastText method for unsupervised word vectors.

## Contextual pretraining

- **[ELMo](https://arxiv.org/abs/1802.05365)** — 2018. Builds context-dependent word representations from internal states of a pretrained bidirectional language model. Allows downstream tasks to combine signals from different layers.
- **[BERT](https://arxiv.org/abs/1810.04805)** — 2018. Pretrains bidirectional Transformer representations with masked-token prediction and an original next-sentence objective. Fine-tunes the encoder for tasks such as classification and extractive question answering.
- **[RoBERTa](https://arxiv.org/abs/1907.11692)** — 2019. Reexamines BERT training choices, data size, and optimization. Demonstrates that training conditions can explain apparent differences between pretraining methods.
- **[XLNet](https://arxiv.org/abs/1906.08237)** — 2019. Trains autoregressive predictions across permutations of the factorization order to learn bidirectional context. Integrates Transformer-XL mechanisms without using BERT's masked-token objective.
- **[ELECTRA](https://arxiv.org/abs/2003.10555)** — 2020. Trains an encoder to distinguish original tokens from plausible generator replacements. Uses a discrimination target across input positions rather than predicting only the identities of masked tokens.
- **[ModernBERT](https://arxiv.org/abs/2412.13663)** — 2024. Updates bidirectional encoder pretraining with rotary positions and alternating local/global attention; evaluated for classification and both single-vector and late-interaction retrieval.

## Sequence generation and translation

- **[Sequence-to-sequence LSTMs](https://arxiv.org/abs/1409.3215)** — 2014. Encodes an input sequence into a fixed-dimensional vector and decodes a target sequence with another LSTM. Establishes a jointly trained neural architecture for sequence transduction.
- **[Neural attention for translation](https://arxiv.org/abs/1409.0473)** — 2014. Learns soft alignments so each generated word can depend on relevant source positions. Relieves the fixed-vector bottleneck of early encoder–decoder translation models.
- **[Transformer](https://arxiv.org/abs/1706.03762)** — 2017. Uses attention-based encoder and decoder layers for sequence transduction, dispensing with recurrence and convolution. Makes interactions between sequence positions explicit through attention.
- **[T5](https://arxiv.org/abs/1910.10683)** — 2019. Expresses classification, question answering, translation, and other tasks in a common text-to-text format. Compares pretraining objectives, architectures, datasets, and transfer procedures within that framework.
- **[BART](https://arxiv.org/abs/1910.13461)** — 2019. Pretrains an encoder–decoder by reconstructing text corrupted with noise, including span masking and sentence reordering. Connects bidirectional encoding with left-to-right generation.

## Multilingual learning

- **[XLM-R](https://arxiv.org/abs/1911.02116)** — 2019. Pretrains a masked language model across 100 languages. Studies cross-lingual transfer and the tradeoff between sharing representations and dividing finite model capacity among languages.
- **[mT5](https://arxiv.org/abs/2010.11934)** — 2020. Extends text-to-text pretraining to multilingual data. Studies cross-lingual task transfer and accidental translation, where generated answers switch away from the requested language.

## Scaling and in-context learning

- **[Language-model scaling laws](https://arxiv.org/abs/2001.08361)** — 2020. Fits empirical relationships among language-model loss, parameter count, data size, and training compute. Its compute-allocation recommendations depend on the investigated training regime.
- **[GPT-3 and few-shot prompting](https://arxiv.org/abs/2005.14165)** — 2020. Studies task demonstrations supplied in the prompt without task-specific gradient updates. Distinguishes in-context conditioning from fine-tuning and reports limitations alongside successful tasks.
- **[Compute-optimal training](https://arxiv.org/abs/2203.15556)** — 2022. Studies how to allocate a fixed training budget between model size and token count. Finds a different allocation from earlier scaling work; the optimum depends on the objective and cost assumptions.

## Instruction and preference learning

- **[Instruction tuning / FLAN](https://arxiv.org/abs/2109.01652)** — 2021. Fine-tunes on multiple tasks expressed as natural-language instructions and evaluates unseen task types. Studies how instruction format, task diversity, and model scale affect transfer.
- **[InstructGPT](https://arxiv.org/abs/2203.02155)** — 2022. Combines supervised demonstrations with preference rankings and reinforcement learning. Studies following instructions on a specified prompt distribution; preference training does not eliminate factual errors.
- **[Constitutional AI](https://arxiv.org/abs/2212.08073)** — 2022. Uses written principles to guide model critiques, revised responses, and AI-generated preference feedback. Combines supervised and reinforcement learning while retaining human choices about the principles.
- **[Direct Preference Optimization](https://arxiv.org/abs/2305.18290)** — 2023. Reparameterizes a reward-based preference objective as direct policy training with a classification loss. Uses preference pairs without a separate reward-model fitting stage or online sampling during fine-tuning.

## Sentence representations and retrieval

- **[Sentence-BERT](https://arxiv.org/abs/1908.10084)** — 2019. Uses siamese and triplet training to produce sentence embeddings comparable by cosine similarity. Enables precomputing candidate representations instead of encoding every sentence pair jointly.
- **[SimCSE](https://arxiv.org/abs/2104.08821)** — 2021. Learns sentence embeddings contrastively using dropout views, or supervised entailment positives and contradiction negatives. Studies how these objectives shape embedding alignment and uniformity.
- **[Dense Passage Retrieval](https://arxiv.org/abs/2004.04906)** — 2020. Learns separate question and passage encoders for dense-vector retrieval. Trains from question–passage examples to select contexts for open-domain question answering.
- **[ColBERT](https://arxiv.org/abs/2004.12832)** — 2020. Encodes query and document tokens separately, then scores fine-grained matches through late interaction. Retains multiple token representations while allowing document encoding before query time.
- **[SPLADE](https://arxiv.org/abs/2107.05720)** — 2021. Learns sparse lexical representations with explicit sparsity regularization and saturated term weights. Supports retrieval with inverted indexes and an effectiveness–sparsity tradeoff.
- **[Retrieval-Augmented Generation](https://arxiv.org/abs/2005.11401)** — 2020. Combines a pretrained sequence generator with a learned retriever and an external passage index. Compares retrieval shared across a response with retrieval varying by token; retrieved context does not guarantee factuality.
- **[RAGTruth](https://aclanthology.org/2024.acl-long.585/)** — 2024. Annotates unsupported or contradictory spans in nearly 18,000 retrieval-augmented responses. Demonstrates that providing retrieved evidence does not ensure faithful generation; retrieval quality and support for generated claims need separate evaluation.
- **[Late chunking](https://arxiv.org/abs/2409.04701)** — 2024. Encodes a longer text before dividing token representations into chunks for pooling. Produces one vector per chunk informed by surrounding context, unlike late-interaction retrieval's multiple stored token vectors.

## Long-context models

- **[Transformer-XL](https://arxiv.org/abs/1901.02860)** — 2019. Combines segment-level recurrence with a positional encoding scheme to extend context across segments. Reuses prior representations while addressing fragmentation from fixed-length training windows.
- **[Longformer](https://arxiv.org/abs/2004.05150)** — 2020. Combines local sliding-window attention with task-specific global attention. Reduces attention cost for long documents when window size and the number of global positions remain bounded.
- **[Lost in the Middle](https://arxiv.org/abs/2307.03172)** — 2023. Finds position-dependent failures in long-context question answering and key-value retrieval. In the studied models, relevant information near the middle can be harder to use than information near either end.

## Decoding and reasoning procedures

- **[Nucleus sampling](https://arxiv.org/abs/1904.09751)** — 2019. Samples from a dynamically selected high-probability portion of the next-token distribution. Studies how decoding changes repetition and diversity even when the underlying language model is unchanged.
- **[Chain-of-thought prompting](https://arxiv.org/abs/2201.11903)** — 2022. Supplies worked reasoning examples in the prompt before asking for a solution. Studies arithmetic, commonsense, and symbolic tasks; generated explanations are not themselves a correctness check.
- **[Self-consistency](https://arxiv.org/abs/2203.11171)** — 2022. Samples multiple reasoning paths and aggregates their answers instead of choosing one greedy path. Improves the studied reasoning benchmarks at the cost of additional generation.
- **[ReAct](https://arxiv.org/abs/2210.03629)** — 2022. Interleaves generated reasoning with actions that query external information or interact with an environment. Studies how observations can update task plans instead of relying only on an uninterrupted text completion.
- **[Speculative decoding](https://arxiv.org/abs/2211.17192)** — 2022. A smaller model drafts tokens that the target model verifies in parallel. A sampling correction preserves the target distribution; speed depends on draft cost and acceptance.
- **[PICARD constrained decoding](https://aclanthology.org/2021.emnlp-main.779/)** — 2021. Rejects tokens that violate incremental parsing constraints during generation. Improves validity and text-to-SQL performance on Spider and CoSQL; a syntactically valid query can still answer the wrong question.
- **[Process supervision](https://arxiv.org/abs/2305.20050)** — 2023. Trains reward models from human judgments of individual solution steps rather than only final answers; introduces PRM800K for studying process supervision in mathematical reasoning.

## Text-generation metrics

- **[BLEU](https://aclanthology.org/P02-1040/)** — 2002. Compares generated translations with references using modified n-gram precision and a brevity penalty. A corpus-level overlap metric; it does not directly establish factual or semantic equivalence.
- **[ROUGE](https://aclanthology.org/W04-1013/)** — 2004. Evaluates summaries using overlap with reference summaries, including n-grams and sequence-based measures. Different ROUGE variants capture different forms of overlap.
- **[chrF](https://aclanthology.org/W15-3049/)** — 2015. Uses character n-gram precision and recall for translation evaluation. Avoids dependence on a particular word tokenizer and exposes a parameter controlling the recall–precision balance.
- **[SacreBLEU and reproducibility](https://arxiv.org/abs/1804.08771)** — 2018. Shows that tokenization and normalization choices can make BLEU scores incomparable. Provides standardized reference processing and reporting to make evaluations easier to reproduce.
- **[BERTScore](https://arxiv.org/abs/1904.09675)** — 2019. Matches candidate and reference tokens using contextual embedding similarity rather than exact lexical equality. Measures representation-level agreement; it is not a factuality verifier.

## Benchmarks and behavioral evaluation

- **[SQuAD](https://arxiv.org/abs/1606.05250)** — 2016. Tests reading comprehension with questions whose answers are spans of the supplied Wikipedia passage. Measures extractive question answering rather than unrestricted open-domain knowledge.
- **[MultiNLI](https://arxiv.org/abs/1704.05426)** — 2017. Provides entailment, contradiction, and neutral sentence pairs across genres of written and spoken English. Includes evaluation of transfer across genres.
- **[GLUE](https://arxiv.org/abs/1804.07461)** — 2018. Combines language-understanding tasks with a diagnostic suite for linguistic behavior. Encourages shared representations across tasks rather than optimizing a single dataset.
- **[SuperGLUE](https://arxiv.org/abs/1905.00537)** — 2019. Introduces a harder collection of language-understanding tasks following progress on GLUE. Supplies a toolkit and shared evaluation; aggregate scores still combine distinct abilities.
- **[MMLU](https://arxiv.org/abs/2009.03300)** — 2020. Tests knowledge and problem solving across 57 academic and professional subjects. Supports per-subject analysis; performance on these questions is not a general measure of real-world competence.
- **[BIG-bench](https://arxiv.org/abs/2206.04615)** — 2022. Collects diverse tasks for examining language-model capabilities and scaling. Studies differences across tasks, model sizes, and evaluation metrics instead of treating aggregate improvement as uniform progress.
- **[TruthfulQA](https://arxiv.org/abs/2109.07958)** — 2021. Tests whether generated answers reproduce common misconceptions. Targets a particular source of falsehood; passing the benchmark does not establish truthfulness on arbitrary questions.
- **[HELM](https://arxiv.org/abs/2211.09110)** — 2022. Evaluates language models across shared scenarios and multiple criteria, including accuracy, calibration, robustness, bias, toxicity, and efficiency. Makes coverage gaps and metric tradeoffs explicit.
- **[CheckList](https://arxiv.org/abs/2005.04118)** — 2020. Organizes behavioral tests by linguistic capability and test type. Uses generated cases to reveal failures that aggregate held-out accuracy can conceal.

## Software

- **[Transformers](https://arxiv.org/abs/1910.03771)** — 2019. Provides a library of pretrained Transformer architectures and task interfaces. The paper describes reusable implementations for NLP research and applications, rather than a single model release.
- **[Stanza](https://arxiv.org/abs/2003.07082)** — 2020. Provides a multilingual NLP pipeline for tokenization, morphology, syntax, and named entities. Packages neural processing components for text analysis across languages.

## Related Topics

- [Neural Networks](https://mlpapers.org/neural-nets/)
- [Transfer Learning](https://mlpapers.org/transfer-learning/)
- [Generative Models](https://mlpapers.org/generative-models/)
- [Computer Vision](https://mlpapers.org/computer-vision/)
