# Natural Language Processing — Interview Questions

100 interview practice questions and concise answers. Product and runtime behavior can vary; check current documentation.

## 1. Explain tokenization in NLP.

Tokenization maps text to words, subwords, or bytes. Use the model's associated tokenizer.

**Remember:** Token counts differ from word counts and vary across languages.

## 2. How would you apply tokenization in a practical NLP task?

Use the model's associated tokenizer. Tokenization maps text to words, subwords, or bytes.

**Remember:** Test Unicode, punctuation, whitespace, and rare terms.

## 3. What mistake should you avoid with tokenization in NLP?

Token counts differ from word counts and vary across languages. Use the model's associated tokenizer.

**Remember:** Tokenization maps text to words, subwords, or bytes.

## 4. How would you verify tokenization in a NLP implementation?

Test Unicode, punctuation, whitespace, and rare terms. Token counts differ from word counts and vary across languages.

**Remember:** Use the model's associated tokenizer.

## 5. Explain subword vocabularies in NLP.

Subwords compose many words from reusable smaller units. Use a vocabulary compatible with the trained model.

**Remember:** Changing vocabulary can invalidate token embeddings.

## 6. How would you apply subword vocabularies in a practical NLP task?

Use a vocabulary compatible with the trained model. Subwords compose many words from reusable smaller units.

**Remember:** Measure fragmentation and downstream quality.

## 7. What mistake should you avoid with subword vocabularies in NLP?

Changing vocabulary can invalidate token embeddings. Use a vocabulary compatible with the trained model.

**Remember:** Subwords compose many words from reusable smaller units.

## 8. How would you verify subword vocabularies in a NLP implementation?

Measure fragmentation and downstream quality. Changing vocabulary can invalidate token embeddings.

**Remember:** Use a vocabulary compatible with the trained model.

## 9. Explain text normalization in NLP.

Normalization standardizes selected variations in text. Choose Unicode and case handling for the task.

**Remember:** Lowercasing can erase distinctions in code, names, or scientific symbols.

## 10. How would you apply text normalization in a practical NLP task?

Choose Unicode and case handling for the task. Normalization standardizes selected variations in text.

**Remember:** Test required distinctions before and after normalization.

## 11. What mistake should you avoid with text normalization in NLP?

Lowercasing can erase distinctions in code, names, or scientific symbols. Choose Unicode and case handling for the task.

**Remember:** Normalization standardizes selected variations in text.

## 12. How would you verify text normalization in a NLP implementation?

Test required distinctions before and after normalization. Lowercasing can erase distinctions in code, names, or scientific symbols.

**Remember:** Choose Unicode and case handling for the task.

## 13. Explain stemming and lemmatization in NLP.

Stemming applies reduction rules; lemmatization aims for dictionary forms. Use them when they improve the lexical task.

**Remember:** Aggressive reduction can merge distinct domain terms.

## 14. How would you apply stemming and lemmatization in a practical NLP task?

Use them when they improve the lexical task. Stemming applies reduction rules; lemmatization aims for dictionary forms.

**Remember:** Compare task quality with and without preprocessing.

## 15. What mistake should you avoid with stemming and lemmatization in NLP?

Aggressive reduction can merge distinct domain terms. Use them when they improve the lexical task.

**Remember:** Stemming applies reduction rules; lemmatization aims for dictionary forms.

## 16. How would you verify stemming and lemmatization in a NLP implementation?

Compare task quality with and without preprocessing. Aggressive reduction can merge distinct domain terms.

**Remember:** Use them when they improve the lexical task.

## 17. Explain TF-IDF in NLP.

TF-IDF weights terms by occurrence and corpus rarity. Fit vocabulary and IDF on training data only.

**Remember:** Fitting before the evaluation split leaks information.

## 18. How would you apply TF-IDF in a practical NLP task?

Fit vocabulary and IDF on training data only. TF-IDF weights terms by occurrence and corpus rarity.

**Remember:** Check split hygiene and compare a count-vector baseline.

## 19. What mistake should you avoid with TF-IDF in NLP?

Fitting before the evaluation split leaks information. Fit vocabulary and IDF on training data only.

**Remember:** TF-IDF weights terms by occurrence and corpus rarity.

## 20. How would you verify TF-IDF in a NLP implementation?

Check split hygiene and compare a count-vector baseline. Fitting before the evaluation split leaks information.

**Remember:** Fit vocabulary and IDF on training data only.

## 21. Explain static word embeddings in NLP.

Static embeddings assign learned vectors to vocabulary items. Use them for suitable semantic features with known coverage.

**Remember:** One vector cannot distinguish all senses of a word.

## 22. How would you apply static word embeddings in a practical NLP task?

Use them for suitable semantic features with known coverage. Static embeddings assign learned vectors to vocabulary items.

**Remember:** Evaluate coverage and task-specific semantic distinctions.

## 23. What mistake should you avoid with static word embeddings in NLP?

One vector cannot distinguish all senses of a word. Use them for suitable semantic features with known coverage.

**Remember:** Static embeddings assign learned vectors to vocabulary items.

## 24. How would you verify static word embeddings in a NLP implementation?

Evaluate coverage and task-specific semantic distinctions. One vector cannot distinguish all senses of a word.

**Remember:** Use them for suitable semantic features with known coverage.

## 25. Explain contextual embeddings in NLP.

Contextual representations depend on surrounding text. Choose hidden states or pooling suited to the downstream task.

**Remember:** A token predictor is not automatically a good sentence encoder.

## 26. How would you apply contextual embeddings in a practical NLP task?

Choose hidden states or pooling suited to the downstream task. Contextual representations depend on surrounding text.

**Remember:** Compare pooling and models on actual labeled examples.

## 27. What mistake should you avoid with contextual embeddings in NLP?

A token predictor is not automatically a good sentence encoder. Choose hidden states or pooling suited to the downstream task.

**Remember:** Contextual representations depend on surrounding text.

## 28. How would you verify contextual embeddings in a NLP implementation?

Compare pooling and models on actual labeled examples. A token predictor is not automatically a good sentence encoder.

**Remember:** Choose hidden states or pooling suited to the downstream task.

## 29. Explain attention masks in NLP.

Attention masks control which tokens can influence representations. Apply padding and causal masks where required.

**Remember:** Missing causal masks can expose future tokens.

## 30. How would you apply attention masks in a practical NLP task?

Apply padding and causal masks where required. Attention masks control which tokens can influence representations.

**Remember:** Test controlled sequences and forbidden-position influence.

## 31. What mistake should you avoid with attention masks in NLP?

Missing causal masks can expose future tokens. Apply padding and causal masks where required.

**Remember:** Attention masks control which tokens can influence representations.

## 32. How would you verify attention masks in a NLP implementation?

Test controlled sequences and forbidden-position influence. Missing causal masks can expose future tokens.

**Remember:** Apply padding and causal masks where required.

## 33. Explain positional information in NLP.

Transformers need mechanisms representing position or relative order. Use supported positional encodings and context settings.

**Remember:** Unsupported context extension may degrade behavior.

## 34. How would you apply positional information in a practical NLP task?

Use supported positional encodings and context settings. Transformers need mechanisms representing position or relative order.

**Remember:** Test long inputs and ordering-sensitive examples.

## 35. What mistake should you avoid with positional information in NLP?

Unsupported context extension may degrade behavior. Use supported positional encodings and context settings.

**Remember:** Transformers need mechanisms representing position or relative order.

## 36. How would you verify positional information in a NLP implementation?

Test long inputs and ordering-sensitive examples. Unsupported context extension may degrade behavior.

**Remember:** Use supported positional encodings and context settings.

## 37. Explain encoder and decoder models in NLP.

Encoders commonly use bidirectional context; causal decoders use preceding context. Match the architecture and objective to the task.

**Remember:** The term transformer alone does not define attention behavior.

## 38. How would you apply encoder and decoder models in a practical NLP task?

Match the architecture and objective to the task. Encoders commonly use bidirectional context; causal decoders use preceding context.

**Remember:** Inspect masks and evaluate the target task.

## 39. What mistake should you avoid with encoder and decoder models in NLP?

The term transformer alone does not define attention behavior. Match the architecture and objective to the task.

**Remember:** Encoders commonly use bidirectional context; causal decoders use preceding context.

## 40. How would you verify encoder and decoder models in a NLP implementation?

Inspect masks and evaluate the target task. The term transformer alone does not define attention behavior.

**Remember:** Match the architecture and objective to the task.

## 41. Explain sequence classification in NLP.

Classification assigns labels to text sequences. Define labels and compare a simple baseline.

**Remember:** Accuracy can hide poor minority-class recall.

## 42. How would you apply sequence classification in a practical NLP task?

Define labels and compare a simple baseline. Classification assigns labels to text sequences.

**Remember:** Report per-class precision, recall, F1, and confusion patterns.

## 43. What mistake should you avoid with sequence classification in NLP?

Accuracy can hide poor minority-class recall. Define labels and compare a simple baseline.

**Remember:** Classification assigns labels to text sequences.

## 44. How would you verify sequence classification in a NLP implementation?

Report per-class precision, recall, F1, and confusion patterns. Accuracy can hide poor minority-class recall.

**Remember:** Define labels and compare a simple baseline.

## 45. Explain named entity recognition in NLP.

NER identifies typed entity spans. Define annotation boundaries and align subwords with source text.

**Remember:** Token accuracy can hide incorrect entity boundaries.

## 46. How would you apply named entity recognition in a practical NLP task?

Define annotation boundaries and align subwords with source text. NER identifies typed entity spans.

**Remember:** Measure entity-level precision, recall, and F1.

## 47. What mistake should you avoid with named entity recognition in NLP?

Token accuracy can hide incorrect entity boundaries. Define annotation boundaries and align subwords with source text.

**Remember:** NER identifies typed entity spans.

## 48. How would you verify named entity recognition in a NLP implementation?

Measure entity-level precision, recall, and F1. Token accuracy can hide incorrect entity boundaries.

**Remember:** Define annotation boundaries and align subwords with source text.

## 49. Explain sentiment analysis in NLP.

Sentiment predicts expressed attitude under a labeling scheme. Use domain-relevant examples and distinguish sentiment from intent.

**Remember:** Sarcasm, negation, and mixed sentiment challenge simple rules.

## 50. How would you apply sentiment analysis in a practical NLP task?

Use domain-relevant examples and distinguish sentiment from intent. Sentiment predicts expressed attitude under a labeling scheme.

**Remember:** Evaluate difficult slices and annotation disagreement.

## 51. What mistake should you avoid with sentiment analysis in NLP?

Sarcasm, negation, and mixed sentiment challenge simple rules. Use domain-relevant examples and distinguish sentiment from intent.

**Remember:** Sentiment predicts expressed attitude under a labeling scheme.

## 52. How would you verify sentiment analysis in a NLP implementation?

Evaluate difficult slices and annotation disagreement. Sarcasm, negation, and mixed sentiment challenge simple rules.

**Remember:** Use domain-relevant examples and distinguish sentiment from intent.

## 53. Explain extractive question answering in NLP.

Extractive QA selects answer spans from supplied context. Include answerable and unanswerable training and evaluation cases.

**Remember:** Forced span selection can imply certainty without evidence.

## 54. How would you apply extractive question answering in a practical NLP task?

Include answerable and unanswerable training and evaluation cases. Extractive QA selects answer spans from supplied context.

**Remember:** Measure exact match, overlap, and abstention.

## 55. What mistake should you avoid with extractive question answering in NLP?

Forced span selection can imply certainty without evidence. Include answerable and unanswerable training and evaluation cases.

**Remember:** Extractive QA selects answer spans from supplied context.

## 56. How would you verify extractive question answering in a NLP implementation?

Measure exact match, overlap, and abstention. Forced span selection can imply certainty without evidence.

**Remember:** Include answerable and unanswerable training and evaluation cases.

## 57. Explain summarization in NLP.

Summaries condense information while retaining relevant meaning. Specify audience, length, and faithfulness requirements.

**Remember:** Fluent text can omit qualifications or introduce unsupported facts.

## 58. How would you apply summarization in a practical NLP task?

Specify audience, length, and faithfulness requirements. Summaries condense information while retaining relevant meaning.

**Remember:** Use source-supported review alongside automated measures.

## 59. What mistake should you avoid with summarization in NLP?

Fluent text can omit qualifications or introduce unsupported facts. Specify audience, length, and faithfulness requirements.

**Remember:** Summaries condense information while retaining relevant meaning.

## 60. How would you verify summarization in a NLP implementation?

Use source-supported review alongside automated measures. Fluent text can omit qualifications or introduce unsupported facts.

**Remember:** Specify audience, length, and faithfulness requirements.

## 61. Explain machine translation in NLP.

Translation preserves meaning across languages and domain constraints. Check terminology, names, numbers, and negation.

**Remember:** Fluency does not guarantee meaning preservation.

## 62. How would you apply machine translation in a practical NLP task?

Check terminology, names, numbers, and negation. Translation preserves meaning across languages and domain constraints.

**Remember:** Combine appropriate metrics with bilingual critical-case review.

## 63. What mistake should you avoid with machine translation in NLP?

Fluency does not guarantee meaning preservation. Check terminology, names, numbers, and negation.

**Remember:** Translation preserves meaning across languages and domain constraints.

## 64. How would you verify machine translation in a NLP implementation?

Combine appropriate metrics with bilingual critical-case review. Fluency does not guarantee meaning preservation.

**Remember:** Check terminology, names, numbers, and negation.

## 65. Explain language modeling in NLP.

Language models estimate token sequences under an objective. Use matching tokenization when comparing held-out losses.

**Remember:** Perplexity across different tokenizers is not directly comparable.

## 66. How would you apply language modeling in a practical NLP task?

Use matching tokenization when comparing held-out losses. Language models estimate token sequences under an objective.

**Remember:** Evaluate downstream usefulness separately from language-model loss.

## 67. What mistake should you avoid with language modeling in NLP?

Perplexity across different tokenizers is not directly comparable. Use matching tokenization when comparing held-out losses.

**Remember:** Language models estimate token sequences under an objective.

## 68. How would you verify language modeling in a NLP implementation?

Evaluate downstream usefulness separately from language-model loss. Perplexity across different tokenizers is not directly comparable.

**Remember:** Use matching tokenization when comparing held-out losses.

## 69. Explain decoding strategies in NLP.

Decoding chooses outputs using greedy, sampling, beam, or other rules. Choose settings for the task's diversity and reproducibility needs.

**Remember:** Low temperature does not guarantee truth.

## 70. How would you apply decoding strategies in a practical NLP task?

Choose settings for the task's diversity and reproducibility needs. Decoding chooses outputs using greedy, sampling, beam, or other rules.

**Remember:** Compare quality and variation over repeated trials.

## 71. What mistake should you avoid with decoding strategies in NLP?

Low temperature does not guarantee truth. Choose settings for the task's diversity and reproducibility needs.

**Remember:** Decoding chooses outputs using greedy, sampling, beam, or other rules.

## 72. How would you verify decoding strategies in a NLP implementation?

Compare quality and variation over repeated trials. Low temperature does not guarantee truth.

**Remember:** Choose settings for the task's diversity and reproducibility needs.

## 73. Explain padding and truncation in NLP.

Batching uses padding and bounded sequence lengths. Use attention masks and preserve important input regions.

**Remember:** Truncation can discard the decisive evidence.

## 74. How would you apply padding and truncation in a practical NLP task?

Use attention masks and preserve important input regions. Batching uses padding and bounded sequence lengths.

**Remember:** Test empty, short, long, and boundary-length cases.

## 75. What mistake should you avoid with padding and truncation in NLP?

Truncation can discard the decisive evidence. Use attention masks and preserve important input regions.

**Remember:** Batching uses padding and bounded sequence lengths.

## 76. How would you verify padding and truncation in a NLP implementation?

Test empty, short, long, and boundary-length cases. Truncation can discard the decisive evidence.

**Remember:** Use attention masks and preserve important input regions.

## 77. Explain text data leakage in NLP.

Related or duplicated documents can cross evaluation boundaries. Split by entity, source, or time where appropriate.

**Remember:** Random row splits can put near-identical examples on both sides.

## 78. How would you apply text data leakage in a practical NLP task?

Split by entity, source, or time where appropriate. Related or duplicated documents can cross evaluation boundaries.

**Remember:** Audit overlap and compare grouped holdouts.

## 79. What mistake should you avoid with text data leakage in NLP?

Random row splits can put near-identical examples on both sides. Split by entity, source, or time where appropriate.

**Remember:** Related or duplicated documents can cross evaluation boundaries.

## 80. How would you verify text data leakage in a NLP implementation?

Audit overlap and compare grouped holdouts. Random row splits can put near-identical examples on both sides.

**Remember:** Split by entity, source, or time where appropriate.

## 81. Explain imbalanced labels in NLP.

Uneven class prevalence affects training and evaluation. Consider class weights and calibrated thresholds.

**Remember:** Resampling the test set can hide deployment prevalence.

## 82. How would you apply imbalanced labels in a practical NLP task?

Consider class weights and calibrated thresholds. Uneven class prevalence affects training and evaluation.

**Remember:** Report per-class metrics at realistic prevalence.

## 83. What mistake should you avoid with imbalanced labels in NLP?

Resampling the test set can hide deployment prevalence. Consider class weights and calibrated thresholds.

**Remember:** Uneven class prevalence affects training and evaluation.

## 84. How would you verify imbalanced labels in a NLP implementation?

Report per-class metrics at realistic prevalence. Resampling the test set can hide deployment prevalence.

**Remember:** Consider class weights and calibrated thresholds.

## 85. Explain multilingual evaluation in NLP.

Aggregate scores can conceal language-specific failure. Use representative language and code-switching slices.

**Remember:** High-resource languages may dominate the overall score.

## 86. How would you apply multilingual evaluation in a practical NLP task?

Use representative language and code-switching slices. Aggregate scores can conceal language-specific failure.

**Remember:** Report language-level quality and annotation coverage.

## 87. What mistake should you avoid with multilingual evaluation in NLP?

High-resource languages may dominate the overall score. Use representative language and code-switching slices.

**Remember:** Aggregate scores can conceal language-specific failure.

## 88. How would you verify multilingual evaluation in a NLP implementation?

Report language-level quality and annotation coverage. High-resource languages may dominate the overall score.

**Remember:** Use representative language and code-switching slices.

## 89. Explain domain adaptation in NLP.

Specialized language may require adapting a model or retrieval system. Compare retrieval, task fine-tuning, and continued training.

**Remember:** Target-domain gains can coincide with broader regressions.

## 90. How would you apply domain adaptation in a practical NLP task?

Compare retrieval, task fine-tuning, and continued training. Specialized language may require adapting a model or retrieval system.

**Remember:** Evaluate domain gains and important general tasks.

## 91. What mistake should you avoid with domain adaptation in NLP?

Target-domain gains can coincide with broader regressions. Compare retrieval, task fine-tuning, and continued training.

**Remember:** Specialized language may require adapting a model or retrieval system.

## 92. How would you verify domain adaptation in a NLP implementation?

Evaluate domain gains and important general tasks. Target-domain gains can coincide with broader regressions.

**Remember:** Compare retrieval, task fine-tuning, and continued training.

## 93. Explain parameter-efficient fine-tuning in NLP.

Adapters and low-rank updates train limited parameter additions or subsets. Compare a supported method with an unfine-tuned baseline.

**Remember:** Fewer trainable parameters do not remove activation-memory costs.

## 94. How would you apply parameter-efficient fine-tuning in a practical NLP task?

Compare a supported method with an unfine-tuned baseline. Adapters and low-rank updates train limited parameter additions or subsets.

**Remember:** Measure quality, memory, inference cost, and regressions.

## 95. What mistake should you avoid with parameter-efficient fine-tuning in NLP?

Fewer trainable parameters do not remove activation-memory costs. Compare a supported method with an unfine-tuned baseline.

**Remember:** Adapters and low-rank updates train limited parameter additions or subsets.

## 96. How would you verify parameter-efficient fine-tuning in a NLP implementation?

Measure quality, memory, inference cost, and regressions. Fewer trainable parameters do not remove activation-memory costs.

**Remember:** Compare a supported method with an unfine-tuned baseline.

## 97. Explain production monitoring in NLP.

Text, labels, and user behavior change after deployment. Monitor sampled quality, drift signals, latency, and escalations.

**Remember:** Distribution drift alone does not prove semantic degradation.

## 98. How would you apply production monitoring in a practical NLP task?

Monitor sampled quality, drift signals, latency, and escalations. Text, labels, and user behavior change after deployment.

**Remember:** Combine recent labels with operational outcomes.

## 99. What mistake should you avoid with production monitoring in NLP?

Distribution drift alone does not prove semantic degradation. Monitor sampled quality, drift signals, latency, and escalations.

**Remember:** Text, labels, and user behavior change after deployment.

## 100. How would you verify production monitoring in a NLP implementation?

Combine recent labels with operational outcomes. Distribution drift alone does not prove semantic degradation.

**Remember:** Monitor sampled quality, drift signals, latency, and escalations.

## Further reading

- [Hugging Face course](https://huggingface.co/learn/llm-course/chapter1/1)
- [Speech and Language Processing](https://web.stanford.edu/~jurafsky/slp3/)
