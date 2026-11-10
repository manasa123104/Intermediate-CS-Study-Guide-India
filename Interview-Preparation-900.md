# AI, Programming & NLP: 900 Interview Questions and Answers

100 original practice questions per topic. These are concise answer outlines, not a ranked list or an employer question bank. Definition, application, pitfalls, and verification questions intentionally reinforce each technical concept. Use your own real experience for behavioral answers.


# RAG — Interview Questions

100 interview practice questions and concise answers. Product and runtime behavior can vary; check current documentation.

## 1. What is retrieval-augmented generation?

RAG retrieves external evidence at request time and supplies it to a model before generation. It helps answer from changing or private information without retraining model weights; its quality still depends on retrieval and evidence use.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 2. What are the main stages of a RAG pipeline?

Ingest and parse documents, split them into chunks, embed and index them, retrieve candidates, optionally rerank, and generate an evidence-grounded answer. Retain document IDs, versions, and permissions throughout the pipeline.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 3. When would you choose RAG over fine-tuning?

Use RAG for frequently changing knowledge and traceable evidence. Fine-tuning is useful for repeatable behavior, format, or domain patterns; it does not provide reliable document lookup. Evaluate whether either is needed before combining them.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 4. How do you choose chunk size?

Start with meaningful document boundaries and a modest size, then compare retrieval quality on representative queries. Small chunks may lose context; large chunks may dilute relevance and increase prompt cost. There is no universal best size.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 5. Why use chunk overlap?

Overlap preserves information crossing chunk boundaries. Too much creates duplicates and extra storage, so measure whether it improves retrieval and deduplicate the final context.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 6. What is an embedding?

An embedding is a numeric representation used to compare content in a learned space. Similarity can indicate related meaning, but it is not proof that two statements agree or that either is true.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 7. What is hybrid retrieval?

Hybrid retrieval combines lexical matching with semantic matching. It can preserve exact identifiers while finding paraphrases; combine rankings with a defined fusion method and validate against your query set.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 8. What does a reranker do?

A reranker scores query-document pairs after initial retrieval. It often improves ordering of a manageable candidate set but adds latency and compute, so compare the quality gain against those costs.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 9. How do you evaluate retrieval?

Use labeled relevant documents or chunks to measure recall at k, precision at k, and ranking metrics such as MRR or nDCG. Include hard negatives, exact identifiers, and permission-sensitive queries.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 10. How do you evaluate generated answers?

Check factual support, completeness, citation correctness, and appropriate abstention. Separate retrieval failures from generation failures and use human review to calibrate automated judges.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 11. What should happen when evidence is missing?

The system should state the limitation and ask a targeted clarification or abstain. A high similarity score alone should not authorize an unsupported answer; calibrate decisions with examples.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 12. How do you implement citations?

Pass stable source identifiers and locations with each chunk, require references to those identifiers, and validate that citations exist and support the associated claims. Linking a document is insufficient if the cited passage says something else.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 13. How do you keep an index fresh?

Track source versions and content hashes, process changes incrementally, and propagate deletions. Monitor ingestion lag and rebuild or re-embed when parsing or embedding models change.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 14. How do you handle PDFs and tables?

Use layout-aware extraction and preserve headings, row labels, units, and page references. Validate extraction on difficult samples; a table serialized without headers can retrieve well and still yield wrong answers.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 15. How do you prevent permission leaks?

Apply authorization using trusted server-side identity before returning retrieved content to the model. Enforce it on documents, caches, logs, and citations; do not rely on a prompt asking the model to hide restricted text.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 16. What is query rewriting?

Query rewriting converts an ambiguous or conversational request into a retrieval query. Preserve original intent, resolve references only from permitted context, and compare rewritten retrieval with a baseline to catch meaning drift.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 17. What is multi-hop RAG?

Multi-hop RAG gathers evidence through multiple linked retrieval steps. Bound the steps and preserve provenance so an incorrect intermediate assumption does not silently become evidence.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 18. How would you reduce RAG latency?

Measure parsing, embedding, retrieval, reranking, and generation separately. Consider caching permission-safe results, smaller candidate sets, shorter context, and parallel independent operations; check quality after each change.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 19. What is context poisoning?

Malicious or misleading retrieved content can try to change system behavior or contaminate an answer. Treat documents as untrusted data, separate instructions from evidence, limit tool permissions, and test adversarial documents.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 20. How would you debug a confidently wrong RAG answer?

Reproduce the request and inspect authorized retrieved chunks, rankings, prompt, and cited passages. Identify whether the fault is extraction, missing evidence, ranking, stale data, or unsupported synthesis, then add a regression case.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 21. Explain document deduplication in RAG.

Repeated chunks can crowd out independent evidence. Hash normalized text and preserve version metadata.

**Remember:** Do not collapse meaningfully different document versions.

## 22. How would you apply document deduplication in a practical RAG task?

Hash normalized text and preserve version metadata. Repeated chunks can crowd out independent evidence.

**Remember:** Measure duplicate top-k results and version-specific accuracy.

## 23. What mistake should you avoid with document deduplication in RAG?

Do not collapse meaningfully different document versions. Hash normalized text and preserve version metadata.

**Remember:** Repeated chunks can crowd out independent evidence.

## 24. How would you verify document deduplication in a RAG implementation?

Measure duplicate top-k results and version-specific accuracy. Do not collapse meaningfully different document versions.

**Remember:** Hash normalized text and preserve version metadata.

## 25. Explain parent-child retrieval in RAG.

Small chunks find precise matches while parent sections restore context. Store child-to-parent IDs and expand only authorized parents.

**Remember:** Unbounded expansion can overwhelm the prompt.

## 26. How would you apply parent-child retrieval in a practical RAG task?

Store child-to-parent IDs and expand only authorized parents. Small chunks find precise matches while parent sections restore context.

**Remember:** Compare completeness and token cost with child-only retrieval.

## 27. What mistake should you avoid with parent-child retrieval in RAG?

Unbounded expansion can overwhelm the prompt. Store child-to-parent IDs and expand only authorized parents.

**Remember:** Small chunks find precise matches while parent sections restore context.

## 28. How would you verify parent-child retrieval in a RAG implementation?

Compare completeness and token cost with child-only retrieval. Unbounded expansion can overwhelm the prompt.

**Remember:** Store child-to-parent IDs and expand only authorized parents.

## 29. Explain context ordering in RAG.

Evidence position can affect how a model uses long contexts. Group related passages with stable source labels.

**Remember:** More evidence can obscure the decisive passage.

## 30. How would you apply context ordering in a practical RAG task?

Group related passages with stable source labels. Evidence position can affect how a model uses long contexts.

**Remember:** Vary passage positions and measure grounded accuracy.

## 31. What mistake should you avoid with context ordering in RAG?

More evidence can obscure the decisive passage. Group related passages with stable source labels.

**Remember:** Evidence position can affect how a model uses long contexts.

## 32. How would you verify context ordering in a RAG implementation?

Vary passage positions and measure grounded accuracy. More evidence can obscure the decisive passage.

**Remember:** Group related passages with stable source labels.

## 33. Explain context compression in RAG.

Compression reduces retrieved text while retaining relevant evidence. Extract query-relevant spans with original references.

**Remember:** Summaries can remove qualifications or invent connections.

## 34. How would you apply context compression in a practical RAG task?

Extract query-relevant spans with original references. Compression reduces retrieved text while retaining relevant evidence.

**Remember:** Check compressed claims against original passages.

## 35. What mistake should you avoid with context compression in RAG?

Summaries can remove qualifications or invent connections. Extract query-relevant spans with original references.

**Remember:** Compression reduces retrieved text while retaining relevant evidence.

## 36. How would you verify context compression in a RAG implementation?

Check compressed claims against original passages. Summaries can remove qualifications or invent connections.

**Remember:** Extract query-relevant spans with original references.

## 37. Explain reciprocal rank fusion in RAG.

RRF merges rankings through reciprocal rank contributions. Deduplicate candidates and combine ranks using a fixed constant.

**Remember:** Raw scores from different retrievers may be incomparable.

## 38. How would you apply reciprocal rank fusion in a practical RAG task?

Deduplicate candidates and combine ranks using a fixed constant. RRF merges rankings through reciprocal rank contributions.

**Remember:** Compare fusion with individual retrievers on labeled queries.

## 39. What mistake should you avoid with reciprocal rank fusion in RAG?

Raw scores from different retrievers may be incomparable. Deduplicate candidates and combine ranks using a fixed constant.

**Remember:** RRF merges rankings through reciprocal rank contributions.

## 40. How would you verify reciprocal rank fusion in a RAG implementation?

Compare fusion with individual retrievers on labeled queries. Raw scores from different retrievers may be incomparable.

**Remember:** Deduplicate candidates and combine ranks using a fixed constant.

## 41. Explain BM25 retrieval in RAG.

BM25 weights lexical matches using frequency and document length. Choose an analyzer that preserves important identifiers.

**Remember:** Stemming can damage technical codes and proper names.

## 42. How would you apply BM25 retrieval in a practical RAG task?

Choose an analyzer that preserves important identifiers. BM25 weights lexical matches using frequency and document length.

**Remember:** Test exact identifiers, rare terms, and paraphrases separately.

## 43. What mistake should you avoid with BM25 retrieval in RAG?

Stemming can damage technical codes and proper names. Choose an analyzer that preserves important identifiers.

**Remember:** BM25 weights lexical matches using frequency and document length.

## 44. How would you verify BM25 retrieval in a RAG implementation?

Test exact identifiers, rare terms, and paraphrases separately. Stemming can damage technical codes and proper names.

**Remember:** Choose an analyzer that preserves important identifiers.

## 45. Explain late interaction retrieval in RAG.

Token-level matching preserves fine-grained document-query interactions. Use a compatible model and multi-vector index.

**Remember:** Token representations can significantly increase resource use.

## 46. How would you apply late interaction retrieval in a practical RAG task?

Use a compatible model and multi-vector index. Token-level matching preserves fine-grained document-query interactions.

**Remember:** Measure recall, index size, and latency under load.

## 47. What mistake should you avoid with late interaction retrieval in RAG?

Token representations can significantly increase resource use. Use a compatible model and multi-vector index.

**Remember:** Token-level matching preserves fine-grained document-query interactions.

## 48. How would you verify late interaction retrieval in a RAG implementation?

Measure recall, index size, and latency under load. Token representations can significantly increase resource use.

**Remember:** Use a compatible model and multi-vector index.

## 49. Explain synthetic query generation in RAG.

Generated questions can represent ways users ask about documents. Generate source-grounded queries offline with provenance.

**Remember:** Synthetic questions may introduce unsupported assumptions.

## 50. How would you apply synthetic query generation in a practical RAG task?

Generate source-grounded queries offline with provenance. Generated questions can represent ways users ask about documents.

**Remember:** Evaluate on independently written user questions.

## 51. What mistake should you avoid with synthetic query generation in RAG?

Synthetic questions may introduce unsupported assumptions. Generate source-grounded queries offline with provenance.

**Remember:** Generated questions can represent ways users ask about documents.

## 52. How would you verify synthetic query generation in a RAG implementation?

Evaluate on independently written user questions. Synthetic questions may introduce unsupported assumptions.

**Remember:** Generate source-grounded queries offline with provenance.

## 53. Explain hypothetical document retrieval in RAG.

A generated hypothetical passage can guide search without becoming evidence. Embed the hypothetical text and retrieve actual sources.

**Remember:** The generated passage can bias retrieval toward a wrong interpretation.

## 54. How would you apply hypothetical document retrieval in a practical RAG task?

Embed the hypothetical text and retrieve actual sources. A generated hypothetical passage can guide search without becoming evidence.

**Remember:** Compare with direct-query retrieval on ambiguous questions.

## 55. What mistake should you avoid with hypothetical document retrieval in RAG?

The generated passage can bias retrieval toward a wrong interpretation. Embed the hypothetical text and retrieve actual sources.

**Remember:** A generated hypothetical passage can guide search without becoming evidence.

## 56. How would you verify hypothetical document retrieval in a RAG implementation?

Compare with direct-query retrieval on ambiguous questions. The generated passage can bias retrieval toward a wrong interpretation.

**Remember:** Embed the hypothetical text and retrieve actual sources.

## 57. Explain query decomposition in RAG.

Compound requests can require several independent evidence searches. Retrieve for explicit subquestions then reconcile the answer.

**Remember:** Subqueries may silently change the original constraints.

## 58. How would you apply query decomposition in a practical RAG task?

Retrieve for explicit subquestions then reconcile the answer. Compound requests can require several independent evidence searches.

**Remember:** Check coverage and cross-source reasoning against the original request.

## 59. What mistake should you avoid with query decomposition in RAG?

Subqueries may silently change the original constraints. Retrieve for explicit subquestions then reconcile the answer.

**Remember:** Compound requests can require several independent evidence searches.

## 60. How would you verify query decomposition in a RAG implementation?

Check coverage and cross-source reasoning against the original request. Subqueries may silently change the original constraints.

**Remember:** Retrieve for explicit subquestions then reconcile the answer.

## 61. Explain temporal retrieval in RAG.

Historical questions need versions valid at the requested time. Store publication and effective dates separately.

**Remember:** The newest policy may be wrong for a historical question.

## 62. How would you apply temporal retrieval in a practical RAG task?

Store publication and effective dates separately. Historical questions need versions valid at the requested time.

**Remember:** Test current, historical, and future-effective documents.

## 63. What mistake should you avoid with temporal retrieval in RAG?

The newest policy may be wrong for a historical question. Store publication and effective dates separately.

**Remember:** Historical questions need versions valid at the requested time.

## 64. How would you verify temporal retrieval in a RAG implementation?

Test current, historical, and future-effective documents. The newest policy may be wrong for a historical question.

**Remember:** Store publication and effective dates separately.

## 65. Explain multilingual retrieval in RAG.

Queries and evidence may use different languages. Use validated multilingual embeddings or careful translation.

**Remember:** Translation can alter names, negation, or domain terminology.

## 66. How would you apply multilingual retrieval in a practical RAG task?

Use validated multilingual embeddings or careful translation. Queries and evidence may use different languages.

**Remember:** Report quality separately by language and mixed-language queries.

## 67. What mistake should you avoid with multilingual retrieval in RAG?

Translation can alter names, negation, or domain terminology. Use validated multilingual embeddings or careful translation.

**Remember:** Queries and evidence may use different languages.

## 68. How would you verify multilingual retrieval in a RAG implementation?

Report quality separately by language and mixed-language queries. Translation can alter names, negation, or domain terminology.

**Remember:** Use validated multilingual embeddings or careful translation.

## 69. Explain spreadsheet retrieval in RAG.

Headers, units, row labels, and formulas provide essential context. Represent bounded table regions with workbook references.

**Remember:** Flattened cell values can lose their entity and unit.

## 70. How would you apply spreadsheet retrieval in a practical RAG task?

Represent bounded table regions with workbook references. Headers, units, row labels, and formulas provide essential context.

**Remember:** Verify numeric answers against source cells and deterministic calculations.

## 71. What mistake should you avoid with spreadsheet retrieval in RAG?

Flattened cell values can lose their entity and unit. Represent bounded table regions with workbook references.

**Remember:** Headers, units, row labels, and formulas provide essential context.

## 72. How would you verify spreadsheet retrieval in a RAG implementation?

Verify numeric answers against source cells and deterministic calculations. Flattened cell values can lose their entity and unit.

**Remember:** Represent bounded table regions with workbook references.

## 73. Explain graph-assisted retrieval in RAG.

Entity relations can guide retrieval across linked sources. Store typed edges with provenance and version information.

**Remember:** Incorrect extracted relations can propagate reasoning errors.

## 74. How would you apply graph-assisted retrieval in a practical RAG task?

Store typed edges with provenance and version information. Entity relations can guide retrieval across linked sources.

**Remember:** Compare relation accuracy and downstream answers with a baseline.

## 75. What mistake should you avoid with graph-assisted retrieval in RAG?

Incorrect extracted relations can propagate reasoning errors. Store typed edges with provenance and version information.

**Remember:** Entity relations can guide retrieval across linked sources.

## 76. How would you verify graph-assisted retrieval in a RAG implementation?

Compare relation accuracy and downstream answers with a baseline. Incorrect extracted relations can propagate reasoning errors.

**Remember:** Store typed edges with provenance and version information.

## 77. Explain retrieval caching in RAG.

Caching saves repeated search work for equivalent authorized requests. Include permissions, tenant, index version, query, and filters in keys.

**Remember:** Shared caches can leak private or deleted content.

## 78. How would you apply retrieval caching in a practical RAG task?

Include permissions, tenant, index version, query, and filters in keys. Caching saves repeated search work for equivalent authorized requests.

**Remember:** Test permission changes, deletion, expiry, and cache isolation.

## 79. What mistake should you avoid with retrieval caching in RAG?

Shared caches can leak private or deleted content. Include permissions, tenant, index version, query, and filters in keys.

**Remember:** Caching saves repeated search work for equivalent authorized requests.

## 80. How would you verify retrieval caching in a RAG implementation?

Test permission changes, deletion, expiry, and cache isolation. Shared caches can leak private or deleted content.

**Remember:** Include permissions, tenant, index version, query, and filters in keys.

## 81. Explain answerability calibration in RAG.

Answerability estimates whether evidence supports a useful response. Tune abstention on labeled answerable and unanswerable examples.

**Remember:** Similarity scores are not calibrated truth probabilities.

## 82. How would you apply answerability calibration in a practical RAG task?

Tune abstention on labeled answerable and unanswerable examples. Answerability estimates whether evidence supports a useful response.

**Remember:** Measure unsupported-answer rate versus answer coverage.

## 83. What mistake should you avoid with answerability calibration in RAG?

Similarity scores are not calibrated truth probabilities. Tune abstention on labeled answerable and unanswerable examples.

**Remember:** Answerability estimates whether evidence supports a useful response.

## 84. How would you verify answerability calibration in a RAG implementation?

Measure unsupported-answer rate versus answer coverage. Similarity scores are not calibrated truth probabilities.

**Remember:** Tune abstention on labeled answerable and unanswerable examples.

## 85. Explain retrieval drift in RAG.

Changing queries or sources can degrade a previously effective retriever. Monitor relevance samples, query categories, and ingestion versions.

**Remember:** Average quality can hide failure in a new user segment.

## 86. How would you apply retrieval drift in a practical RAG task?

Monitor relevance samples, query categories, and ingestion versions. Changing queries or sources can degrade a previously effective retriever.

**Remember:** Use slice-based evaluation on recent and historical queries.

## 87. What mistake should you avoid with retrieval drift in RAG?

Average quality can hide failure in a new user segment. Monitor relevance samples, query categories, and ingestion versions.

**Remember:** Changing queries or sources can degrade a previously effective retriever.

## 88. How would you verify retrieval drift in a RAG implementation?

Use slice-based evaluation on recent and historical queries. Average quality can hide failure in a new user segment.

**Remember:** Monitor relevance samples, query categories, and ingestion versions.

## 89. Explain numerical grounding in RAG.

Numbers require matching units, scope, dates, and correct arithmetic. Retrieve source values and calculate derived quantities deterministically.

**Remember:** Combining incompatible currencies or time periods produces misleading results.

## 90. How would you apply numerical grounding in a practical RAG task?

Retrieve source values and calculate derived quantities deterministically. Numbers require matching units, scope, dates, and correct arithmetic.

**Remember:** Verify inputs, conversions, rounding, and calculation reproducibility.

## 91. What mistake should you avoid with numerical grounding in RAG?

Combining incompatible currencies or time periods produces misleading results. Retrieve source values and calculate derived quantities deterministically.

**Remember:** Numbers require matching units, scope, dates, and correct arithmetic.

## 92. How would you verify numerical grounding in a RAG implementation?

Verify inputs, conversions, rounding, and calculation reproducibility. Combining incompatible currencies or time periods produces misleading results.

**Remember:** Retrieve source values and calculate derived quantities deterministically.

## 93. Explain conflicting evidence in RAG.

Documents may disagree because of authority, version, or context. Apply documented authority and effective-date precedence.

**Remember:** Repeated outdated claims should not outweigh authoritative evidence.

## 94. How would you apply conflicting evidence in a practical RAG task?

Apply documented authority and effective-date precedence. Documents may disagree because of authority, version, or context.

**Remember:** Test conflicting versions and disclose unresolved disagreement.

## 95. What mistake should you avoid with conflicting evidence in RAG?

Repeated outdated claims should not outweigh authoritative evidence. Apply documented authority and effective-date precedence.

**Remember:** Documents may disagree because of authority, version, or context.

## 96. How would you verify conflicting evidence in a RAG implementation?

Test conflicting versions and disclose unresolved disagreement. Repeated outdated claims should not outweigh authoritative evidence.

**Remember:** Apply documented authority and effective-date precedence.

## 97. Explain RAG tracing in RAG.

Traces connect ingestion, retrieval, configuration, and answer generation. Record redacted stage events with stable source and request IDs.

**Remember:** Full-prompt logging can create an unprotected sensitive-data store.

## 98. How would you apply RAG tracing in a practical RAG task?

Record redacted stage events with stable source and request IDs. Traces connect ingestion, retrieval, configuration, and answer generation.

**Remember:** Reproduce failures while auditing log access and retention.

## 99. What mistake should you avoid with RAG tracing in RAG?

Full-prompt logging can create an unprotected sensitive-data store. Record redacted stage events with stable source and request IDs.

**Remember:** Traces connect ingestion, retrieval, configuration, and answer generation.

## 100. How would you verify RAG tracing in a RAG implementation?

Reproduce failures while auditing log access and retention. Full-prompt logging can create an unprotected sensitive-data store.

**Remember:** Record redacted stage events with stable source and request IDs.

## Further reading

- [RAG overview](https://www.pinecone.io/learn/retrieval-augmented-generation/)


# Vector Databases — Interview Questions

100 interview practice questions and concise answers. Product and runtime behavior can vary; check current documentation.

## 1. What is a vector database?

A vector database stores vectors and supports similarity search, usually with metadata and indexing features. Some applications instead use a relational database with vector support; choose based on workload and operations.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 2. How does cosine similarity differ from dot product?

Cosine compares direction after accounting for vector magnitude; dot product includes magnitude. For unit-normalized vectors they produce the same ranking, but use the metric expected by the embedding model.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 3. What is Euclidean distance?

It measures straight-line distance between vectors. Lower values indicate closer vectors under that metric; its usefulness depends on the embedding model, normalization, and data distribution.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 4. What is approximate nearest-neighbor search?

ANN trades guaranteed exact results for lower search cost. Evaluate recall relative to exact search on a representative sample, along with latency and memory use.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 5. What is HNSW?

HNSW is a graph-based ANN approach with multiple navigable layers. It often provides a useful latency-recall tradeoff, but construction parameters, query settings, and memory requirements must be benchmarked.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 6. What is IVFFlat?

IVFFlat groups vectors into lists and searches selected lists near the query. More probes typically increase recall and work; its index training and tuning should reflect the data distribution.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 7. How would you choose HNSW versus IVFFlat?

Benchmark recall, tail latency, build time, memory, updates, and filtered queries on realistic data. Treat default settings as a starting point rather than assuming one index wins every workload.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 8. What is metadata filtering?

It restricts eligible records by fields such as tenant, date, or document type. Index frequently filtered fields where supported and enforce authorization through trusted filters or database policies.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 9. Why can post-filtering reduce recall?

Filtering only after taking the nearest candidates may remove most candidates and miss eligible neighbors farther down the ranking. Use supported filtered search, iterative retrieval, or exact search on a selective subset when appropriate.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 10. How do you choose embedding dimensions?

Use a model and supported dimension setting that meet your quality and cost goals. Higher dimensions increase storage and compute but do not guarantee better retrieval; benchmark with representative queries.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 11. How do you migrate embedding models?

Build a versioned parallel index, re-embed the source corpus, and evaluate it before switching queries. Query vectors must match the indexed embedding space; matching dimension counts alone is insufficient.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 12. What is vector quantization?

Quantization stores lower-precision or compressed vector representations to reduce resources. It can affect ranking accuracy; measure recall and consider rescoring candidates with original vectors.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 13. How do you estimate vector storage?

A baseline for float32 vectors is record count times dimensions times four bytes. Add index overhead, metadata, replicas, and backups; real memory use can substantially exceed raw vector size.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 14. How would you design multi-tenant search?

Bind tenant identity server-side and choose isolation through separate collections, partitions, policies, or mandatory filters. Test cross-tenant access, backup access, and cache isolation, not only the normal search path.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 15. How do upserts and deletes affect retrieval?

Upserts should use stable IDs to avoid duplication. Deletion visibility and index maintenance vary by system, so verify consistency guarantees and ensure removed documents disappear from downstream caches and citations.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 16. When is exact search appropriate?

Exact search is useful for small datasets, highly selective subsets, and ground-truth evaluation. It can also be simpler and fast enough; measure it before introducing ANN complexity.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 17. What causes vector-search latency spikes?

Possible causes include cold caches, expensive filters, high concurrency, compaction, network delays, and large search budgets. Inspect percentile latency and resource saturation rather than average response time alone.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 18. How do you evaluate a vector database?

Use your own data and access patterns to test retrieval quality, filtered search, latency, throughput, updates, reliability, and total cost. Include operational needs such as backup, restore, observability, and migration.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 19. Can vector search replace SQL?

Vector search finds similar content; SQL expresses structured constraints and joins. Many applications need both, such as filtering authorized invoices by date before semantic retrieval of descriptions.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 20. How would you back up a vector index?

Back up source documents, IDs, metadata, permissions, embedding versions, and configuration alongside supported database snapshots. Test restoration and rebuilding, since an untested snapshot is not a recovery plan.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 21. Explain HNSW search budgets in Vector DB.

Search exploration trades additional work for improved recall. Tune supported exploration parameters against exact neighbors.

**Remember:** Unfiltered tuning may fail on selective filtered queries.

## 22. How would you apply HNSW search budgets in a practical Vector DB task?

Tune supported exploration parameters against exact neighbors. Search exploration trades additional work for improved recall.

**Remember:** Compare recall and p95 latency across filter selectivities.

## 23. What mistake should you avoid with HNSW search budgets in Vector DB?

Unfiltered tuning may fail on selective filtered queries. Tune supported exploration parameters against exact neighbors.

**Remember:** Search exploration trades additional work for improved recall.

## 24. How would you verify HNSW search budgets in a Vector DB implementation?

Compare recall and p95 latency across filter selectivities. Unfiltered tuning may fail on selective filtered queries.

**Remember:** Tune supported exploration parameters against exact neighbors.

## 25. Explain HNSW construction in Vector DB.

Graph connectivity and construction effort affect index size and quality. Build trial indexes under controlled workloads.

**Remember:** Higher construction effort may provide little extra quality.

## 26. How would you apply HNSW construction in a practical Vector DB task?

Build trial indexes under controlled workloads. Graph connectivity and construction effort affect index size and quality.

**Remember:** Compare build time, memory, and recall at equal latency.

## 27. What mistake should you avoid with HNSW construction in Vector DB?

Higher construction effort may provide little extra quality. Build trial indexes under controlled workloads.

**Remember:** Graph connectivity and construction effort affect index size and quality.

## 28. How would you verify HNSW construction in a Vector DB implementation?

Compare build time, memory, and recall at equal latency. Higher construction effort may provide little extra quality.

**Remember:** Build trial indexes under controlled workloads.

## 29. Explain IVF list selection in Vector DB.

List counts control how vectors are partitioned before probing. Benchmark list counts and query probe budgets together.

**Remember:** Poor partitioning can degrade performance after distribution shifts.

## 30. How would you apply IVF list selection in a practical Vector DB task?

Benchmark list counts and query probe budgets together. List counts control how vectors are partitioned before probing.

**Remember:** Evaluate recall with new data and realistic updates.

## 31. What mistake should you avoid with IVF list selection in Vector DB?

Poor partitioning can degrade performance after distribution shifts. Benchmark list counts and query probe budgets together.

**Remember:** List counts control how vectors are partitioned before probing.

## 32. How would you verify IVF list selection in a Vector DB implementation?

Evaluate recall with new data and realistic updates. Poor partitioning can degrade performance after distribution shifts.

**Remember:** Benchmark list counts and query probe budgets together.

## 33. Explain scalar quantization in Vector DB.

Scalar quantization reduces precision of vector components. Use supported compression and optional full-precision rescoring.

**Remember:** Close neighbors may change order after compression.

## 34. How would you apply scalar quantization in a practical Vector DB task?

Use supported compression and optional full-precision rescoring. Scalar quantization reduces precision of vector components.

**Remember:** Compare memory savings with recall and rescoring cost.

## 35. What mistake should you avoid with scalar quantization in Vector DB?

Close neighbors may change order after compression. Use supported compression and optional full-precision rescoring.

**Remember:** Scalar quantization reduces precision of vector components.

## 36. How would you verify scalar quantization in a Vector DB implementation?

Compare memory savings with recall and rescoring cost. Close neighbors may change order after compression.

**Remember:** Use supported compression and optional full-precision rescoring.

## 37. Explain product quantization in Vector DB.

Product quantization encodes subspaces with learned codebooks. Train codebooks on representative vectors.

**Remember:** Unrepresentative training data can create uneven retrieval errors.

## 38. How would you apply product quantization in a practical Vector DB task?

Train codebooks on representative vectors. Product quantization encodes subspaces with learned codebooks.

**Remember:** Evaluate difficult query slices and distribution changes.

## 39. What mistake should you avoid with product quantization in Vector DB?

Unrepresentative training data can create uneven retrieval errors. Train codebooks on representative vectors.

**Remember:** Product quantization encodes subspaces with learned codebooks.

## 40. How would you verify product quantization in a Vector DB implementation?

Evaluate difficult query slices and distribution changes. Unrepresentative training data can create uneven retrieval errors.

**Remember:** Train codebooks on representative vectors.

## 41. Explain sparse vector search in Vector DB.

Sparse vectors assign weights to selected vocabulary dimensions. Use a compatible sparse encoder and index.

**Remember:** Sparse and dense scores may require rank-based fusion.

## 42. How would you apply sparse vector search in a practical Vector DB task?

Use a compatible sparse encoder and index. Sparse vectors assign weights to selected vocabulary dimensions.

**Remember:** Evaluate sparse-only, dense-only, and combined retrieval.

## 43. What mistake should you avoid with sparse vector search in Vector DB?

Sparse and dense scores may require rank-based fusion. Use a compatible sparse encoder and index.

**Remember:** Sparse vectors assign weights to selected vocabulary dimensions.

## 44. How would you verify sparse vector search in a Vector DB implementation?

Evaluate sparse-only, dense-only, and combined retrieval. Sparse and dense scores may require rank-based fusion.

**Remember:** Use a compatible sparse encoder and index.

## 45. Explain multi-vector records in Vector DB.

A record can have distinct title, body, image, or token representations. Store named vectors with explicit model and metric configurations.

**Remember:** Equal dimensions do not imply compatible embedding spaces.

## 46. How would you apply multi-vector records in a practical Vector DB task?

Store named vectors with explicit model and metric configurations. A record can have distinct title, body, image, or token representations.

**Remember:** Test each field and the documented aggregation method.

## 47. What mistake should you avoid with multi-vector records in Vector DB?

Equal dimensions do not imply compatible embedding spaces. Store named vectors with explicit model and metric configurations.

**Remember:** A record can have distinct title, body, image, or token representations.

## 48. How would you verify multi-vector records in a Vector DB implementation?

Test each field and the documented aggregation method. Equal dimensions do not imply compatible embedding spaces.

**Remember:** Store named vectors with explicit model and metric configurations.

## 49. Explain payload indexes in Vector DB.

Metadata indexes speed supported filter operations. Index frequently queried fields with appropriate types.

**Remember:** Indexing every field increases storage and write overhead.

## 50. How would you apply payload indexes in a practical Vector DB task?

Index frequently queried fields with appropriate types. Metadata indexes speed supported filter operations.

**Remember:** Profile filter latency and ingestion cost before and after indexing.

## 51. What mistake should you avoid with payload indexes in Vector DB?

Indexing every field increases storage and write overhead. Index frequently queried fields with appropriate types.

**Remember:** Metadata indexes speed supported filter operations.

## 52. How would you verify payload indexes in a Vector DB implementation?

Profile filter latency and ingestion cost before and after indexing. Indexing every field increases storage and write overhead.

**Remember:** Index frequently queried fields with appropriate types.

## 53. Explain tenant partitioning in Vector DB.

Partitions organize records around access patterns and isolation needs. Choose partition keys and enforce authorization server-side.

**Remember:** Large tenants can create hotspots and uneven resource use.

## 54. How would you apply tenant partitioning in a practical Vector DB task?

Choose partition keys and enforce authorization server-side. Partitions organize records around access patterns and isolation needs.

**Remember:** Test skewed workloads and denied cross-tenant access.

## 55. What mistake should you avoid with tenant partitioning in Vector DB?

Large tenants can create hotspots and uneven resource use. Choose partition keys and enforce authorization server-side.

**Remember:** Partitions organize records around access patterns and isolation needs.

## 56. How would you verify tenant partitioning in a Vector DB implementation?

Test skewed workloads and denied cross-tenant access. Large tenants can create hotspots and uneven resource use.

**Remember:** Choose partition keys and enforce authorization server-side.

## 57. Explain sharding in Vector DB.

Sharding distributes data across nodes. Plan routing and shard counts around growth and query fan-out.

**Remember:** More shards can increase coordination overhead.

## 58. How would you apply sharding in a practical Vector DB task?

Plan routing and shard counts around growth and query fan-out. Sharding distributes data across nodes.

**Remember:** Load-test uneven data and node failures.

## 59. What mistake should you avoid with sharding in Vector DB?

More shards can increase coordination overhead. Plan routing and shard counts around growth and query fan-out.

**Remember:** Sharding distributes data across nodes.

## 60. How would you verify sharding in a Vector DB implementation?

Load-test uneven data and node failures. More shards can increase coordination overhead.

**Remember:** Plan routing and shard counts around growth and query fan-out.

## 61. Explain replication in Vector DB.

Replicas support availability and sometimes read capacity. Choose consistency and placement for freshness requirements.

**Remember:** Weak consistency may delay visibility on other replicas.

## 62. How would you apply replication in a practical Vector DB task?

Choose consistency and placement for freshness requirements. Replicas support availability and sometimes read capacity.

**Remember:** Test read-after-write behavior and failover guarantees.

## 63. What mistake should you avoid with replication in Vector DB?

Weak consistency may delay visibility on other replicas. Choose consistency and placement for freshness requirements.

**Remember:** Replicas support availability and sometimes read capacity.

## 64. How would you verify replication in a Vector DB implementation?

Test read-after-write behavior and failover guarantees. Weak consistency may delay visibility on other replicas.

**Remember:** Choose consistency and placement for freshness requirements.

## 65. Explain index rebuilds in Vector DB.

A new index can be validated before replacing the active one. Build, catch up writes, compare, and switch traffic atomically where supported.

**Remember:** Concurrent writes can disappear without a catch-up plan.

## 66. How would you apply index rebuilds in a practical Vector DB task?

Build, catch up writes, compare, and switch traffic atomically where supported. A new index can be validated before replacing the active one.

**Remember:** Check record parity, deletion parity, recall, and rollback.

## 67. What mistake should you avoid with index rebuilds in Vector DB?

Concurrent writes can disappear without a catch-up plan. Build, catch up writes, compare, and switch traffic atomically where supported.

**Remember:** A new index can be validated before replacing the active one.

## 68. How would you verify index rebuilds in a Vector DB implementation?

Check record parity, deletion parity, recall, and rollback. Concurrent writes can disappear without a catch-up plan.

**Remember:** Build, catch up writes, compare, and switch traffic atomically where supported.

## 69. Explain distance thresholds in Vector DB.

Thresholds limit accepted neighbors under a specific metric. Calibrate with labeled in-domain matches and nonmatches.

**Remember:** Distances are not universal probabilities.

## 70. How would you apply distance thresholds in a practical Vector DB task?

Calibrate with labeled in-domain matches and nonmatches. Thresholds limit accepted neighbors under a specific metric.

**Remember:** Inspect false positives and negatives for each query category.

## 71. What mistake should you avoid with distance thresholds in Vector DB?

Distances are not universal probabilities. Calibrate with labeled in-domain matches and nonmatches.

**Remember:** Thresholds limit accepted neighbors under a specific metric.

## 72. How would you verify distance thresholds in a Vector DB implementation?

Inspect false positives and negatives for each query category. Distances are not universal probabilities.

**Remember:** Calibrate with labeled in-domain matches and nonmatches.

## 73. Explain normalization in Vector DB.

Normalization changes magnitude, often to unit length. Apply model-supported preprocessing consistently to queries and records.

**Remember:** Normalizing only one side can change rankings unexpectedly.

## 74. How would you apply normalization in a practical Vector DB task?

Apply model-supported preprocessing consistently to queries and records. Normalization changes magnitude, often to unit length.

**Remember:** Inspect norms and known-neighbor rankings after preprocessing changes.

## 75. What mistake should you avoid with normalization in Vector DB?

Normalizing only one side can change rankings unexpectedly. Apply model-supported preprocessing consistently to queries and records.

**Remember:** Normalization changes magnitude, often to unit length.

## 76. How would you verify normalization in a Vector DB implementation?

Inspect norms and known-neighbor rankings after preprocessing changes. Normalizing only one side can change rankings unexpectedly.

**Remember:** Apply model-supported preprocessing consistently to queries and records.

## 77. Explain batch ingestion in Vector DB.

Batching reduces per-request overhead for writes. Use bounded batches, stable IDs, and failure accounting.

**Remember:** Blind batch retries can duplicate non-idempotent records.

## 78. How would you apply batch ingestion in a practical Vector DB task?

Use bounded batches, stable IDs, and failure accounting. Batching reduces per-request overhead for writes.

**Remember:** Reconcile input and stored IDs after partial failures.

## 79. What mistake should you avoid with batch ingestion in Vector DB?

Blind batch retries can duplicate non-idempotent records. Use bounded batches, stable IDs, and failure accounting.

**Remember:** Batching reduces per-request overhead for writes.

## 80. How would you verify batch ingestion in a Vector DB implementation?

Reconcile input and stored IDs after partial failures. Blind batch retries can duplicate non-idempotent records.

**Remember:** Use bounded batches, stable IDs, and failure accounting.

## 81. Explain deletion compliance in Vector DB.

Deletion must address vectors, metadata, caches, and retention policies. Track removal through all derived stores.

**Remember:** Removing source files alone leaves searchable copies.

## 82. How would you apply deletion compliance in a practical Vector DB task?

Track removal through all derived stores. Deletion must address vectors, metadata, caches, and retention policies.

**Remember:** Verify search absence and document backup-retention handling.

## 83. What mistake should you avoid with deletion compliance in Vector DB?

Removing source files alone leaves searchable copies. Track removal through all derived stores.

**Remember:** Deletion must address vectors, metadata, caches, and retention policies.

## 84. How would you verify deletion compliance in a Vector DB implementation?

Verify search absence and document backup-retention handling. Removing source files alone leaves searchable copies.

**Remember:** Track removal through all derived stores.

## 85. Explain capacity planning in Vector DB.

Capacity includes index overhead, metadata, replicas, and headroom. Measure actual resource use and forecast query and ingest demand.

**Remember:** Raw vector bytes alone underestimate requirements.

## 86. How would you apply capacity planning in a practical Vector DB task?

Measure actual resource use and forecast query and ingest demand. Capacity includes index overhead, metadata, replicas, and headroom.

**Remember:** Test growth, saturation, and reduced capacity during failures.

## 87. What mistake should you avoid with capacity planning in Vector DB?

Raw vector bytes alone underestimate requirements. Measure actual resource use and forecast query and ingest demand.

**Remember:** Capacity includes index overhead, metadata, replicas, and headroom.

## 88. How would you verify capacity planning in a Vector DB implementation?

Test growth, saturation, and reduced capacity during failures. Raw vector bytes alone underestimate requirements.

**Remember:** Measure actual resource use and forecast query and ingest demand.

## 89. Explain disk-backed search in Vector DB.

Disk-backed indexes trade storage access for reduced memory use. Benchmark cold and warm caches on intended storage.

**Remember:** Warm-cache benchmarks can conceal slow random reads.

## 90. How would you apply disk-backed search in a practical Vector DB task?

Benchmark cold and warm caches on intended storage. Disk-backed indexes trade storage access for reduced memory use.

**Remember:** Report I/O, recall, and tail latency under concurrency.

## 91. What mistake should you avoid with disk-backed search in Vector DB?

Warm-cache benchmarks can conceal slow random reads. Benchmark cold and warm caches on intended storage.

**Remember:** Disk-backed indexes trade storage access for reduced memory use.

## 92. How would you verify disk-backed search in a Vector DB implementation?

Report I/O, recall, and tail latency under concurrency. Warm-cache benchmarks can conceal slow random reads.

**Remember:** Benchmark cold and warm caches on intended storage.

## 93. Explain search observability in Vector DB.

Search health includes semantic quality and operational metrics. Track latency percentiles, freshness, errors, and sampled relevance.

**Remember:** Healthy CPU does not prove relevant search results.

## 94. How would you apply search observability in a practical Vector DB task?

Track latency percentiles, freshness, errors, and sampled relevance. Search health includes semantic quality and operational metrics.

**Remember:** Correlate regressions with corpus and configuration changes.

## 95. What mistake should you avoid with search observability in Vector DB?

Healthy CPU does not prove relevant search results. Track latency percentiles, freshness, errors, and sampled relevance.

**Remember:** Search health includes semantic quality and operational metrics.

## 96. How would you verify search observability in a Vector DB implementation?

Correlate regressions with corpus and configuration changes. Healthy CPU does not prove relevant search results.

**Remember:** Track latency percentiles, freshness, errors, and sampled relevance.

## 97. Explain recovery objectives in Vector DB.

Recovery targets specify acceptable downtime and data loss. Combine snapshots with source data and model-version records.

**Remember:** Restored vectors are unusable if their embedding configuration is unknown.

## 98. How would you apply recovery objectives in a practical Vector DB task?

Combine snapshots with source data and model-version records. Recovery targets specify acceptable downtime and data loss.

**Remember:** Rehearse restoration and compare measured RTO and RPO with requirements.

## 99. What mistake should you avoid with recovery objectives in Vector DB?

Restored vectors are unusable if their embedding configuration is unknown. Combine snapshots with source data and model-version records.

**Remember:** Recovery targets specify acceptable downtime and data loss.

## 100. How would you verify recovery objectives in a Vector DB implementation?

Rehearse restoration and compare measured RTO and RPO with requirements. Restored vectors are unusable if their embedding configuration is unknown.

**Remember:** Combine snapshots with source data and model-version records.

## Further reading

- [pgvector indexes](https://github.com/pgvector/pgvector)
- [Qdrant filtering](https://qdrant.tech/documentation/search/filtering/)


# Agentic AI — Interview Questions

100 interview practice questions and concise answers. Product and runtime behavior can vary; check current documentation.

## 1. What does agentic AI mean?

It describes systems in which a model helps choose actions toward a goal using feedback. The term varies, so specify the available tools, decision freedom, state, and stopping conditions rather than relying on the label.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 2. How does an agent differ from a workflow?

A workflow follows predefined control paths, while an agent can choose its next steps dynamically. Use the simplest approach that meets the task; dynamic control increases flexibility and the evaluation burden.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 3. When should you avoid an agent?

Avoid one when deterministic code or a fixed workflow is sufficient, or when errors cannot be contained. An agent should earn its additional latency, cost, and operational complexity through measured task success.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 4. What is a plan-act-observe loop?

The system chooses a step, invokes an allowed action, inspects the result, and updates its next decision. Bound iterations, time, cost, and permissions so the loop cannot run indefinitely.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 5. What is tool calling?

A model proposes a structured tool name and arguments; application code validates and executes the request. A tool call is not inherently trusted, and the model should not receive credentials just to request an action.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 6. How do you design a good tool schema?

Define one clear purpose, typed fields, required arguments, constraints, and understandable error outputs. Prefer narrow operations over an unrestricted shell or database tool when the task permits it.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 7. What is an autonomy boundary?

It defines which decisions and actions the system may take without human approval. Express it in executable policies, permissions, and budgets, with explicit review for consequential actions.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 8. What is human-in-the-loop control?

A person reviews a specific decision or action before execution or at a defined checkpoint. Present the exact proposed effect and preserve its identity so approval cannot accidentally authorize a changed action.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 9. How should an agent handle tool failures?

Classify errors as transient, invalid input, permission failure, or permanent failure. Retry only appropriate operations with bounds and backoff, and escalate when a safe recovery is unavailable.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 10. How do you prevent infinite agent loops?

Enforce iteration and time limits, detect repeated equivalent calls, and require progress signals. Return a clear partial result and reason for stopping instead of consuming the entire budget silently.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 11. How do you measure agent success?

Measure task completion, correctness, policy compliance, intervention rate, latency, and cost across realistic scenarios. Evaluate complete trajectories and side effects, not only the final answer's wording.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 12. What is trajectory evaluation?

It examines intermediate decisions, tool arguments, observations, and final outcomes. This reveals cases where an acceptable-looking answer hides unnecessary actions, unauthorized access, or fragile recovery behavior.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 13. What is prompt injection in an agent?

Untrusted content attempts to redirect the model's instructions or actions. Treat tool outputs and documents as data, enforce permissions outside the model, and isolate secrets from content the model can expose.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 14. How do you control agent cost?

Set task budgets for model calls, tokens, tools, and execution time. Use simpler routes when sufficient, cache safe repeat work, and monitor cost per successful task rather than cost per call alone.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 15. What is checkpointing?

Checkpointing saves execution state at defined boundaries so a run can resume after interruption. Include completed side effects and idempotency keys to prevent replay from duplicating real actions.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 16. How do you make agent actions auditable?

Record structured events with request IDs, decisions, policy checks, tool calls, and outcomes. Redact sensitive data and retain useful evidence without assuming private reasoning traces are required.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 17. What is an evaluator-optimizer pattern?

One component proposes a result and another assesses it against explicit criteria before revision. Cap revision cycles and independently verify objective requirements; an evaluator can also be wrong.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 18. What is routing in an AI system?

Routing selects a model, tool, or workflow based on the request. Validate the route and fallback behavior, and ensure routing never weakens the user's authorization boundaries.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 19. How do you deploy agent changes safely?

Version models, prompts, tools, and policies; run regression evaluations before a canary rollout. Monitor task success and harmful side effects with a fast rollback path.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 20. How would you design a customer-support agent?

Start with scoped retrieval and read-only account tools, authenticate the customer, and cite relevant policy. Add narrowly permitted actions with validation, approval where needed, escalation, and end-to-end evaluation.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 21. Explain risk-based action controls in Agentic AI.

Actions need controls proportional to consequence and reversibility. Enforce action policies and permissions in server code.

**Remember:** Model-generated risk labels cannot be the only gate.

## 22. How would you apply risk-based action controls in a practical Agentic AI task?

Enforce action policies and permissions in server code. Actions need controls proportional to consequence and reversibility.

**Remember:** Test denied actions and attempts to bypass approval.

## 23. What mistake should you avoid with risk-based action controls in Agentic AI?

Model-generated risk labels cannot be the only gate. Enforce action policies and permissions in server code.

**Remember:** Actions need controls proportional to consequence and reversibility.

## 24. How would you verify risk-based action controls in a Agentic AI implementation?

Test denied actions and attempts to bypass approval. Model-generated risk labels cannot be the only gate.

**Remember:** Enforce action policies and permissions in server code.

## 25. Explain approval binding in Agentic AI.

Approval must refer to the exact executable action. Bind identity, payload, expiry, and operation ID.

**Remember:** Changing arguments after approval can invalidate consent.

## 26. How would you apply approval binding in a practical Agentic AI task?

Bind identity, payload, expiry, and operation ID. Approval must refer to the exact executable action.

**Remember:** Test replay, expiry, and payload modification.

## 27. What mistake should you avoid with approval binding in Agentic AI?

Changing arguments after approval can invalidate consent. Bind identity, payload, expiry, and operation ID.

**Remember:** Approval must refer to the exact executable action.

## 28. How would you verify approval binding in a Agentic AI implementation?

Test replay, expiry, and payload modification. Changing arguments after approval can invalidate consent.

**Remember:** Bind identity, payload, expiry, and operation ID.

## 29. Explain budget-aware planning in Agentic AI.

Plans must fit finite time, tokens, and tool costs. Allocate budgets and simplify when limits approach.

**Remember:** Excessive planning can consume the budget without useful progress.

## 30. How would you apply budget-aware planning in a practical Agentic AI task?

Allocate budgets and simplify when limits approach. Plans must fit finite time, tokens, and tool costs.

**Remember:** Measure success per budget and graceful partial completion.

## 31. What mistake should you avoid with budget-aware planning in Agentic AI?

Excessive planning can consume the budget without useful progress. Allocate budgets and simplify when limits approach.

**Remember:** Plans must fit finite time, tokens, and tool costs.

## 32. How would you verify budget-aware planning in a Agentic AI implementation?

Measure success per budget and graceful partial completion. Excessive planning can consume the budget without useful progress.

**Remember:** Allocate budgets and simplify when limits approach.

## 33. Explain execution state machines in Agentic AI.

Explicit states constrain valid task transitions. Encode transitions and terminal outcomes deterministically.

**Remember:** Free-form status can hide duplicate side effects.

## 34. How would you apply execution state machines in a practical Agentic AI task?

Encode transitions and terminal outcomes deterministically. Explicit states constrain valid task transitions.

**Remember:** Test out-of-order events and duplicate completions.

## 35. What mistake should you avoid with execution state machines in Agentic AI?

Free-form status can hide duplicate side effects. Encode transitions and terminal outcomes deterministically.

**Remember:** Explicit states constrain valid task transitions.

## 36. How would you verify execution state machines in a Agentic AI implementation?

Test out-of-order events and duplicate completions. Free-form status can hide duplicate side effects.

**Remember:** Encode transitions and terminal outcomes deterministically.

## 37. Explain uncertainty escalation in Agentic AI.

Escalation requests help when evidence or authority is insufficient. Define triggers for missing inputs and conflicting permissions.

**Remember:** Unnecessary clarification can block authorized work.

## 38. How would you apply uncertainty escalation in a practical Agentic AI task?

Define triggers for missing inputs and conflicting permissions. Escalation requests help when evidence or authority is insufficient.

**Remember:** Measure missed and excessive escalations separately.

## 39. What mistake should you avoid with uncertainty escalation in Agentic AI?

Unnecessary clarification can block authorized work. Define triggers for missing inputs and conflicting permissions.

**Remember:** Escalation requests help when evidence or authority is insufficient.

## 40. How would you verify uncertainty escalation in a Agentic AI implementation?

Measure missed and excessive escalations separately. Unnecessary clarification can block authorized work.

**Remember:** Define triggers for missing inputs and conflicting permissions.

## 41. Explain tool-output validation in Agentic AI.

Tool outputs need structural and task-specific checks. Validate types, required fields, and critical semantic constraints.

**Remember:** Valid JSON can still contain stale or malicious content.

## 42. How would you apply tool-output validation in a practical Agentic AI task?

Validate types, required fields, and critical semantic constraints. Tool outputs need structural and task-specific checks.

**Remember:** Inject malformed and inconsistent responses in tests.

## 43. What mistake should you avoid with tool-output validation in Agentic AI?

Valid JSON can still contain stale or malicious content. Validate types, required fields, and critical semantic constraints.

**Remember:** Tool outputs need structural and task-specific checks.

## 44. How would you verify tool-output validation in a Agentic AI implementation?

Inject malformed and inconsistent responses in tests. Valid JSON can still contain stale or malicious content.

**Remember:** Validate types, required fields, and critical semantic constraints.

## 45. Explain policy-aware planning in Agentic AI.

Every intermediate step must respect task constraints. Maintain structured constraints and check proposed actions.

**Remember:** A legitimate goal does not authorize every route to it.

## 46. How would you apply policy-aware planning in a practical Agentic AI task?

Maintain structured constraints and check proposed actions. Every intermediate step must respect task constraints.

**Remember:** Evaluate entire trajectories including failed steps.

## 47. What mistake should you avoid with policy-aware planning in Agentic AI?

A legitimate goal does not authorize every route to it. Maintain structured constraints and check proposed actions.

**Remember:** Every intermediate step must respect task constraints.

## 48. How would you verify policy-aware planning in a Agentic AI implementation?

Evaluate entire trajectories including failed steps. A legitimate goal does not authorize every route to it.

**Remember:** Maintain structured constraints and check proposed actions.

## 49. Explain shadow deployment in Agentic AI.

Shadow mode proposes actions without changing production state. Compare read-only proposals with trusted decisions.

**Remember:** It cannot prove real side-effect recovery.

## 50. How would you apply shadow deployment in a practical Agentic AI task?

Compare read-only proposals with trusted decisions. Shadow mode proposes actions without changing production state.

**Remember:** Evaluate proposals first and execution separately in an isolated environment.

## 51. What mistake should you avoid with shadow deployment in Agentic AI?

It cannot prove real side-effect recovery. Compare read-only proposals with trusted decisions.

**Remember:** Shadow mode proposes actions without changing production state.

## 52. How would you verify shadow deployment in a Agentic AI implementation?

Evaluate proposals first and execution separately in an isolated environment. It cannot prove real side-effect recovery.

**Remember:** Compare read-only proposals with trusted decisions.

## 53. Explain canary releases in Agentic AI.

Canaries limit exposure to a new agent configuration. Use small cohorts and explicit rollback thresholds.

**Remember:** Aggregate success can conceal rare consequential failures.

## 54. How would you apply canary releases in a practical Agentic AI task?

Use small cohorts and explicit rollback thresholds. Canaries limit exposure to a new agent configuration.

**Remember:** Compare slices and inspect high-risk actions before expansion.

## 55. What mistake should you avoid with canary releases in Agentic AI?

Aggregate success can conceal rare consequential failures. Use small cohorts and explicit rollback thresholds.

**Remember:** Canaries limit exposure to a new agent configuration.

## 56. How would you verify canary releases in a Agentic AI implementation?

Compare slices and inspect high-risk actions before expansion. Aggregate success can conceal rare consequential failures.

**Remember:** Use small cohorts and explicit rollback thresholds.

## 57. Explain kill switches in Agentic AI.

A kill switch disables autonomous execution. Enforce server-side revocation before tools and long-running steps.

**Remember:** A UI-only switch may leave workers running.

## 58. How would you apply kill switches in a practical Agentic AI task?

Enforce server-side revocation before tools and long-running steps. A kill switch disables autonomous execution.

**Remember:** Verify cancellation propagation and prevention of new actions.

## 59. What mistake should you avoid with kill switches in Agentic AI?

A UI-only switch may leave workers running. Enforce server-side revocation before tools and long-running steps.

**Remember:** A kill switch disables autonomous execution.

## 60. How would you verify kill switches in a Agentic AI implementation?

Verify cancellation propagation and prevention of new actions. A UI-only switch may leave workers running.

**Remember:** Enforce server-side revocation before tools and long-running steps.

## 61. Explain decomposition quality in Agentic AI.

Useful subtasks have explicit inputs, outputs, and dependencies. Define acceptance criteria and integration ownership.

**Remember:** Too many tiny tasks increase coordination failures.

## 62. How would you apply decomposition quality in a practical Agentic AI task?

Define acceptance criteria and integration ownership. Useful subtasks have explicit inputs, outputs, and dependencies.

**Remember:** Compare completion quality and overhead with a simpler baseline.

## 63. What mistake should you avoid with decomposition quality in Agentic AI?

Too many tiny tasks increase coordination failures. Define acceptance criteria and integration ownership.

**Remember:** Useful subtasks have explicit inputs, outputs, and dependencies.

## 64. How would you verify decomposition quality in a Agentic AI implementation?

Compare completion quality and overhead with a simpler baseline. Too many tiny tasks increase coordination failures.

**Remember:** Define acceptance criteria and integration ownership.

## 65. Explain parallel execution in Agentic AI.

Independent work can run concurrently within controlled boundaries. Parallelize isolated reads and serialize dependent mutations.

**Remember:** Concurrent writes can overwrite state or duplicate effects.

## 66. How would you apply parallel execution in a practical Agentic AI task?

Parallelize isolated reads and serialize dependent mutations. Independent work can run concurrently within controlled boundaries.

**Remember:** Test races and measure actual wall-clock savings.

## 67. What mistake should you avoid with parallel execution in Agentic AI?

Concurrent writes can overwrite state or duplicate effects. Parallelize isolated reads and serialize dependent mutations.

**Remember:** Independent work can run concurrently within controlled boundaries.

## 68. How would you verify parallel execution in a Agentic AI implementation?

Test races and measure actual wall-clock savings. Concurrent writes can overwrite state or duplicate effects.

**Remember:** Parallelize isolated reads and serialize dependent mutations.

## 69. Explain completion criteria in Agentic AI.

Completion should reflect satisfied requirements or explicit stopping limits. Verify external state against predetermined checks.

**Remember:** An agent may declare success based on a convincing narrative.

## 70. How would you apply completion criteria in a practical Agentic AI task?

Verify external state against predetermined checks. Completion should reflect satisfied requirements or explicit stopping limits.

**Remember:** Use independent acceptance checks rather than final wording alone.

## 71. What mistake should you avoid with completion criteria in Agentic AI?

An agent may declare success based on a convincing narrative. Verify external state against predetermined checks.

**Remember:** Completion should reflect satisfied requirements or explicit stopping limits.

## 72. How would you verify completion criteria in a Agentic AI implementation?

Use independent acceptance checks rather than final wording alone. An agent may declare success based on a convincing narrative.

**Remember:** Verify external state against predetermined checks.

## 73. Explain adversarial evaluation in Agentic AI.

Adversarial cases probe injection and permission boundaries. Include credential, authority, and destructive-action attacks.

**Remember:** A static test set may miss evolving attack patterns.

## 74. How would you apply adversarial evaluation in a practical Agentic AI task?

Include credential, authority, and destructive-action attacks. Adversarial cases probe injection and permission boundaries.

**Remember:** Maintain fresh holdouts and generalize from discovered failures.

## 75. What mistake should you avoid with adversarial evaluation in Agentic AI?

A static test set may miss evolving attack patterns. Include credential, authority, and destructive-action attacks.

**Remember:** Adversarial cases probe injection and permission boundaries.

## 76. How would you verify adversarial evaluation in a Agentic AI implementation?

Maintain fresh holdouts and generalize from discovered failures. A static test set may miss evolving attack patterns.

**Remember:** Include credential, authority, and destructive-action attacks.

## 77. Explain model routing in Agentic AI.

Routing assigns stages to models suited to their requirements. Define measured capability needs and fallback rules.

**Remember:** Cheap calls can increase total cost through retries.

## 78. How would you apply model routing in a practical Agentic AI task?

Define measured capability needs and fallback rules. Routing assigns stages to models suited to their requirements.

**Remember:** Compare quality and cost per completed task by route.

## 79. What mistake should you avoid with model routing in Agentic AI?

Cheap calls can increase total cost through retries. Define measured capability needs and fallback rules.

**Remember:** Routing assigns stages to models suited to their requirements.

## 80. How would you verify model routing in a Agentic AI implementation?

Compare quality and cost per completed task by route. Cheap calls can increase total cost through retries.

**Remember:** Define measured capability needs and fallback rules.

## 81. Explain data minimization in Agentic AI.

Agents should receive only information required for the task. Redact unnecessary fields before model access.

**Remember:** Equivalent sensitive identifiers may remain in other fields.

## 82. How would you apply data minimization in a practical Agentic AI task?

Redact unnecessary fields before model access. Agents should receive only information required for the task.

**Remember:** Audit prompts, outputs, tool arguments, and logs.

## 83. What mistake should you avoid with data minimization in Agentic AI?

Equivalent sensitive identifiers may remain in other fields. Redact unnecessary fields before model access.

**Remember:** Agents should receive only information required for the task.

## 84. How would you verify data minimization in a Agentic AI implementation?

Audit prompts, outputs, tool arguments, and logs. Equivalent sensitive identifiers may remain in other fields.

**Remember:** Redact unnecessary fields before model access.

## 85. Explain deterministic components in Agentic AI.

Ordinary code provides reliable validation and fixed operations. Use code for arithmetic, authorization, and known sequencing.

**Remember:** Model-driven replacements add variability without guaranteed benefit.

## 86. How would you apply deterministic components in a practical Agentic AI task?

Use code for arithmetic, authorization, and known sequencing. Ordinary code provides reliable validation and fixed operations.

**Remember:** Compare reproducibility and failure rates with the coded baseline.

## 87. What mistake should you avoid with deterministic components in Agentic AI?

Model-driven replacements add variability without guaranteed benefit. Use code for arithmetic, authorization, and known sequencing.

**Remember:** Ordinary code provides reliable validation and fixed operations.

## 88. How would you verify deterministic components in a Agentic AI implementation?

Compare reproducibility and failure rates with the coded baseline. Model-driven replacements add variability without guaranteed benefit.

**Remember:** Use code for arithmetic, authorization, and known sequencing.

## 89. Explain service-level objectives in Agentic AI.

SLOs define acceptable quality and operational outcomes. Track success, latency, cost, and policy violations over explicit windows.

**Remember:** Latency-only goals can reward fast wrong answers.

## 90. How would you apply service-level objectives in a practical Agentic AI task?

Track success, latency, cost, and policy violations over explicit windows. SLOs define acceptable quality and operational outcomes.

**Remember:** Monitor violations and use error budgets for rollout decisions.

## 91. What mistake should you avoid with service-level objectives in Agentic AI?

Latency-only goals can reward fast wrong answers. Track success, latency, cost, and policy violations over explicit windows.

**Remember:** SLOs define acceptable quality and operational outcomes.

## 92. How would you verify service-level objectives in a Agentic AI implementation?

Monitor violations and use error budgets for rollout decisions. Latency-only goals can reward fast wrong answers.

**Remember:** Track success, latency, cost, and policy violations over explicit windows.

## 93. Explain configuration rollback in Agentic AI.

Rollback restores a compatible model, prompt, tool, and policy bundle. Version the full configuration and test reverting it.

**Remember:** Prompt rollback cannot undo already-completed actions.

## 94. How would you apply configuration rollback in a practical Agentic AI task?

Version the full configuration and test reverting it. Rollback restores a compatible model, prompt, tool, and policy bundle.

**Remember:** Test configuration recovery separately from compensation.

## 95. What mistake should you avoid with configuration rollback in Agentic AI?

Prompt rollback cannot undo already-completed actions. Version the full configuration and test reverting it.

**Remember:** Rollback restores a compatible model, prompt, tool, and policy bundle.

## 96. How would you verify configuration rollback in a Agentic AI implementation?

Test configuration recovery separately from compensation. Prompt rollback cannot undo already-completed actions.

**Remember:** Version the full configuration and test reverting it.

## 97. Explain evaluation dataset design in Agentic AI.

Evaluation cases need expected outcomes and allowed behavior. Version realistic examples and independent holdouts.

**Remember:** Repeated tuning on the holdout causes overfitting.

## 98. How would you apply evaluation dataset design in a practical Agentic AI task?

Version realistic examples and independent holdouts. Evaluation cases need expected outcomes and allowed behavior.

**Remember:** Report performance on fresh cases collected after configuration freeze.

## 99. What mistake should you avoid with evaluation dataset design in Agentic AI?

Repeated tuning on the holdout causes overfitting. Version realistic examples and independent holdouts.

**Remember:** Evaluation cases need expected outcomes and allowed behavior.

## 100. How would you verify evaluation dataset design in a Agentic AI implementation?

Report performance on fresh cases collected after configuration freeze. Repeated tuning on the holdout causes overfitting.

**Remember:** Version realistic examples and independent holdouts.

## Further reading

- [Agent patterns](https://www.anthropic.com/research/building-effective-agents)


# AI Agents — Interview Questions

100 interview practice questions and concise answers. Product and runtime behavior can vary; check current documentation.

## 1. What components make up an AI agent?

Typical components are a model, instructions, tools, state, and a control loop. Production systems also need authorization, observability, evaluation, and explicit termination behavior.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 2. What is short-term versus long-term memory?

Short-term memory holds current task context; long-term memory persists information across tasks. Persist only useful, consented data with provenance, expiry, and deletion controls.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 3. How do you manage limited context?

Keep relevant recent state, summarize older material with source references, and retrieve details when needed. Preserve constraints and unresolved actions so summarization does not silently change the task.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 4. When are multiple agents useful?

They can help when work splits into independent specialties or parallel subtasks. Compare against a single-agent baseline because coordination overhead and conflicting outputs can reduce reliability.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 5. What is an orchestrator-worker design?

An orchestrator assigns bounded work to workers and integrates their results. Define ownership, inputs, outputs, and verification so delegation does not create duplicated actions or inconsistent state.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 6. How do agents share state safely?

Use explicit structured state with access controls and concurrency rules. Version updates or use transactions where needed, and prevent a worker from overwriting another worker's newer result.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 7. What is an agent handoff?

A handoff transfers responsibility along with relevant context and constraints. Include completed actions, remaining work, permissions, and a clear return or escalation path.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 8. How do you avoid duplicate tool actions?

Use idempotency keys, persistent execution records, and transaction boundaries. Before retrying an uncertain action, query its status rather than assuming it did not happen.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 9. What is a structured output?

It is output constrained to a defined schema rather than free-form prose. Validate it in application code; syntactic validity does not guarantee semantic correctness or permission to execute it.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 10. What is a tool allowlist?

It explicitly limits available operations for a given task and identity. Combine it with argument validation and backend access checks; exposing a tool name should not confer unrestricted access.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 11. How should an agent use external APIs?

Use server-managed credentials, scoped access, input validation, timeouts, and rate limits. Treat returned content as untrusted and avoid logging tokens or unnecessary personal data.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 12. How do you handle API rate limits?

Apply bounded exponential backoff with jitter where safe, respect retry guidance, and queue work within task deadlines. Use concurrency limits and report partial completion if the deadline cannot be met.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 13. What is durable execution?

Durable execution preserves state and progress across process failures or long waits. It needs clear replay semantics and side-effect handling; simply saving a chat transcript is insufficient.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 14. How do you sandbox code-executing agents?

Use isolated execution with limited filesystem and network access, resource quotas, and short-lived credentials where required. Keep permission enforcement outside the generated code.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 15. How do you test a tool-using agent?

Test schema errors, denied permissions, timeouts, repeated calls, malicious results, and successful tasks. Use controlled tools or test environments and verify final state as well as messages.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 16. What should happen when agents disagree?

Resolve disagreements using evidence, deterministic checks, or human review according to task risk. Majority vote alone does not establish truth when agents share the same blind spot.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 17. How do you build a research agent?

Define scope and source criteria, search and retrieve within bounds, track claim-level provenance, and verify citations. Make uncertainty visible and prevent retrieved pages from changing the agent's instructions.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 18. How do you build a coding agent safely?

Provide a constrained repository, clear acceptance criteria, and appropriate test tools. Review diffs and dependencies, protect secrets, and gate production side effects according to policy.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 19. How do you personalize an agent responsibly?

Use explicit preferences and minimal relevant history with user controls. Separate preferences from instructions that authorize actions, and avoid inferring sensitive traits without a legitimate need.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 20. How would you investigate an agent incident?

Contain further actions, preserve redacted execution evidence, and identify the affected users and side effects. Fix the root policy or implementation issue and add a representative regression before restoring autonomy.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 21. Explain session isolation in Agents.

Different users and tasks need separate authorized state. Bind memory, credentials, caches, and execution IDs to identity.

**Remember:** A global chat buffer can leak another user's information.

## 22. How would you apply session isolation in a practical Agents task?

Bind memory, credentials, caches, and execution IDs to identity. Different users and tasks need separate authorized state.

**Remember:** Interleave sessions and verify state never crosses boundaries.

## 23. What mistake should you avoid with session isolation in Agents?

A global chat buffer can leak another user's information. Bind memory, credentials, caches, and execution IDs to identity.

**Remember:** Different users and tasks need separate authorized state.

## 24. How would you verify session isolation in a Agents implementation?

Interleave sessions and verify state never crosses boundaries. A global chat buffer can leak another user's information.

**Remember:** Bind memory, credentials, caches, and execution IDs to identity.

## 25. Explain working-memory summaries in Agents.

Summaries compress context while preserving decisions and constraints. Retain unresolved work, side effects, preferences, and source references.

**Remember:** Omitted restrictions can change resumed behavior.

## 26. How would you apply working-memory summaries in a practical Agents task?

Retain unresolved work, side effects, preferences, and source references. Summaries compress context while preserving decisions and constraints.

**Remember:** Compare resumed tasks with full-context constraint-heavy tasks.

## 27. What mistake should you avoid with working-memory summaries in Agents?

Omitted restrictions can change resumed behavior. Retain unresolved work, side effects, preferences, and source references.

**Remember:** Summaries compress context while preserving decisions and constraints.

## 28. How would you verify working-memory summaries in a Agents implementation?

Compare resumed tasks with full-context constraint-heavy tasks. Omitted restrictions can change resumed behavior.

**Remember:** Retain unresolved work, side effects, preferences, and source references.

## 29. Explain memory provenance in Agents.

Stored facts need source, time, and trust metadata. Separate user instructions from observations and inferred preferences.

**Remember:** Untrusted content can become a persistent instruction.

## 30. How would you apply memory provenance in a practical Agents task?

Separate user instructions from observations and inferred preferences. Stored facts need source, time, and trust metadata.

**Remember:** Test memory poisoning and authority confusion in later runs.

## 31. What mistake should you avoid with memory provenance in Agents?

Untrusted content can become a persistent instruction. Separate user instructions from observations and inferred preferences.

**Remember:** Stored facts need source, time, and trust metadata.

## 32. How would you verify memory provenance in a Agents implementation?

Test memory poisoning and authority confusion in later runs. Untrusted content can become a persistent instruction.

**Remember:** Separate user instructions from observations and inferred preferences.

## 33. Explain memory expiry in Agents.

Stored information can become stale or unnecessary. Apply retention and refresh time-sensitive facts.

**Remember:** Old preferences do not establish current action authorization.

## 34. How would you apply memory expiry in a practical Agents task?

Apply retention and refresh time-sensitive facts. Stored information can become stale or unnecessary.

**Remember:** Test expiry, deletion, and preference changes across sessions.

## 35. What mistake should you avoid with memory expiry in Agents?

Old preferences do not establish current action authorization. Apply retention and refresh time-sensitive facts.

**Remember:** Stored information can become stale or unnecessary.

## 36. How would you verify memory expiry in a Agents implementation?

Test expiry, deletion, and preference changes across sessions. Old preferences do not establish current action authorization.

**Remember:** Apply retention and refresh time-sensitive facts.

## 37. Explain tool pagination in Agents.

Large results require explicit continuation. Follow returned cursors within task limits and record completeness.

**Remember:** The first page can be mistaken for the full dataset.

## 38. How would you apply tool pagination in a practical Agents task?

Follow returned cursors within task limits and record completeness. Large results require explicit continuation.

**Remember:** Use multi-page fixtures and verify totals and continuation.

## 39. What mistake should you avoid with tool pagination in Agents?

The first page can be mistaken for the full dataset. Follow returned cursors within task limits and record completeness.

**Remember:** Large results require explicit continuation.

## 40. How would you verify tool pagination in a Agents implementation?

Use multi-page fixtures and verify totals and continuation. The first page can be mistaken for the full dataset.

**Remember:** Follow returned cursors within task limits and record completeness.

## 41. Explain tool discovery in Agents.

Discovery identifies available operations and contracts. Read metadata and expose only task-relevant tools.

**Remember:** Similar names can conceal different side effects.

## 42. How would you apply tool discovery in a practical Agents task?

Read metadata and expose only task-relevant tools. Discovery identifies available operations and contracts.

**Remember:** Test ambiguous requests and validate tool selection.

## 43. What mistake should you avoid with tool discovery in Agents?

Similar names can conceal different side effects. Read metadata and expose only task-relevant tools.

**Remember:** Discovery identifies available operations and contracts.

## 44. How would you verify tool discovery in a Agents implementation?

Test ambiguous requests and validate tool selection. Similar names can conceal different side effects.

**Remember:** Read metadata and expose only task-relevant tools.

## 45. Explain dependency scheduling in Agents.

Some steps must wait for prerequisites. Represent dependencies and schedule only ready work.

**Remember:** Early execution may use invented inputs.

## 46. How would you apply dependency scheduling in a practical Agents task?

Represent dependencies and schedule only ready work. Some steps must wait for prerequisites.

**Remember:** Test failed prerequisites and downstream cancellation.

## 47. What mistake should you avoid with dependency scheduling in Agents?

Early execution may use invented inputs. Represent dependencies and schedule only ready work.

**Remember:** Some steps must wait for prerequisites.

## 48. How would you verify dependency scheduling in a Agents implementation?

Test failed prerequisites and downstream cancellation. Early execution may use invented inputs.

**Remember:** Represent dependencies and schedule only ready work.

## 49. Explain artifact ownership in Agents.

Shared output needs clear edit responsibility. Assign files or sections and integrate controlled changes.

**Remember:** Concurrent edits may silently discard another worker's work.

## 50. How would you apply artifact ownership in a practical Agents task?

Assign files or sections and integrate controlled changes. Shared output needs clear edit responsibility.

**Remember:** Verify diffs include all expected contributions.

## 51. What mistake should you avoid with artifact ownership in Agents?

Concurrent edits may silently discard another worker's work. Assign files or sections and integrate controlled changes.

**Remember:** Shared output needs clear edit responsibility.

## 52. How would you verify artifact ownership in a Agents implementation?

Verify diffs include all expected contributions. Concurrent edits may silently discard another worker's work.

**Remember:** Assign files or sections and integrate controlled changes.

## 53. Explain message contracts in Agents.

Structured messages distinguish tasks, results, and errors. Define IDs, schemas, provenance, and terminal statuses.

**Remember:** Tentative suggestions can be confused with completed work.

## 54. How would you apply message contracts in a practical Agents task?

Define IDs, schemas, provenance, and terminal statuses. Structured messages distinguish tasks, results, and errors.

**Remember:** Reject missing fields, mismatched IDs, and duplicate results.

## 55. What mistake should you avoid with message contracts in Agents?

Tentative suggestions can be confused with completed work. Define IDs, schemas, provenance, and terminal statuses.

**Remember:** Structured messages distinguish tasks, results, and errors.

## 56. How would you verify message contracts in a Agents implementation?

Reject missing fields, mismatched IDs, and duplicate results. Tentative suggestions can be confused with completed work.

**Remember:** Define IDs, schemas, provenance, and terminal statuses.

## 57. Explain task leases in Agents.

A lease grants time-limited ownership of work. Use atomic claims, expiry, and idempotent completion.

**Remember:** A stale worker may act after losing its lease.

## 58. How would you apply task leases in a practical Agents task?

Use atomic claims, expiry, and idempotent completion. A lease grants time-limited ownership of work.

**Remember:** Simulate delayed workers and reject stale commits.

## 59. What mistake should you avoid with task leases in Agents?

A stale worker may act after losing its lease. Use atomic claims, expiry, and idempotent completion.

**Remember:** A lease grants time-limited ownership of work.

## 60. How would you verify task leases in a Agents implementation?

Simulate delayed workers and reject stale commits. A stale worker may act after losing its lease.

**Remember:** Use atomic claims, expiry, and idempotent completion.

## 61. Explain tool timeouts in Agents.

Deadlines bound waiting time for tools. Use operation-specific timeouts and status queries.

**Remember:** A timed-out write may still succeed remotely.

## 62. How would you apply tool timeouts in a practical Agents task?

Use operation-specific timeouts and status queries. Deadlines bound waiting time for tools.

**Remember:** Test uncertain outcomes before allowing retries.

## 63. What mistake should you avoid with tool timeouts in Agents?

A timed-out write may still succeed remotely. Use operation-specific timeouts and status queries.

**Remember:** Deadlines bound waiting time for tools.

## 64. How would you verify tool timeouts in a Agents implementation?

Test uncertain outcomes before allowing retries. A timed-out write may still succeed remotely.

**Remember:** Use operation-specific timeouts and status queries.

## 65. Explain compensating actions in Agents.

Compensation corrects completed effects after partial failure. Define domain-specific inverse or corrective actions.

**Remember:** Some effects cannot be fully reversed.

## 66. How would you apply compensating actions in a practical Agents task?

Define domain-specific inverse or corrective actions. Compensation corrects completed effects after partial failure.

**Remember:** Test partial failures and document residual effects requiring review.

## 67. What mistake should you avoid with compensating actions in Agents?

Some effects cannot be fully reversed. Define domain-specific inverse or corrective actions.

**Remember:** Compensation corrects completed effects after partial failure.

## 68. How would you verify compensating actions in a Agents implementation?

Test partial failures and document residual effects requiring review. Some effects cannot be fully reversed.

**Remember:** Define domain-specific inverse or corrective actions.

## 69. Explain identity propagation in Agents.

Downstream tools need trustworthy user and service identity. Pass scoped identity through authenticated server channels.

**Remember:** Model-supplied user IDs can enable impersonation.

## 70. How would you apply identity propagation in a practical Agents task?

Pass scoped identity through authenticated server channels. Downstream tools need trustworthy user and service identity.

**Remember:** Attempt spoofing and verify backend ownership checks.

## 71. What mistake should you avoid with identity propagation in Agents?

Model-supplied user IDs can enable impersonation. Pass scoped identity through authenticated server channels.

**Remember:** Downstream tools need trustworthy user and service identity.

## 72. How would you verify identity propagation in a Agents implementation?

Attempt spoofing and verify backend ownership checks. Model-supplied user IDs can enable impersonation.

**Remember:** Pass scoped identity through authenticated server channels.

## 73. Explain notification policies in Agents.

Notifications require authorized recipients and useful triggers. Enforce channel, recipient, and deduplication rules outside generation.

**Remember:** Retries can send duplicate or speculative messages.

## 74. How would you apply notification policies in a practical Agents task?

Enforce channel, recipient, and deduplication rules outside generation. Notifications require authorized recipients and useful triggers.

**Remember:** Test recipient binding and unauthorized-send prevention.

## 75. What mistake should you avoid with notification policies in Agents?

Retries can send duplicate or speculative messages. Enforce channel, recipient, and deduplication rules outside generation.

**Remember:** Notifications require authorized recipients and useful triggers.

## 76. How would you verify notification policies in a Agents implementation?

Test recipient binding and unauthorized-send prevention. Retries can send duplicate or speculative messages.

**Remember:** Enforce channel, recipient, and deduplication rules outside generation.

## 77. Explain browser reliability in Agents.

Browser actions depend on current observed state. Use semantic targets and verify meaningful results.

**Remember:** Stale controls can trigger the wrong action.

## 78. How would you apply browser reliability in a practical Agents task?

Use semantic targets and verify meaningful results. Browser actions depend on current observed state.

**Remember:** Test delays, navigation changes, and confirmation dialogs.

## 79. What mistake should you avoid with browser reliability in Agents?

Stale controls can trigger the wrong action. Use semantic targets and verify meaningful results.

**Remember:** Browser actions depend on current observed state.

## 80. How would you verify browser reliability in a Agents implementation?

Test delays, navigation changes, and confirmation dialogs. Stale controls can trigger the wrong action.

**Remember:** Use semantic targets and verify meaningful results.

## 81. Explain repository boundaries in Agents.

Coding tasks require a defined workspace and write scope. Resolve paths and restrict filesystem access.

**Remember:** Traversal or incorrect roots can affect unrelated files.

## 82. How would you apply repository boundaries in a practical Agents task?

Resolve paths and restrict filesystem access. Coding tasks require a defined workspace and write scope.

**Remember:** Verify modified paths and test traversal rejection.

## 83. What mistake should you avoid with repository boundaries in Agents?

Traversal or incorrect roots can affect unrelated files. Resolve paths and restrict filesystem access.

**Remember:** Coding tasks require a defined workspace and write scope.

## 84. How would you verify repository boundaries in a Agents implementation?

Verify modified paths and test traversal rejection. Traversal or incorrect roots can affect unrelated files.

**Remember:** Resolve paths and restrict filesystem access.

## 85. Explain reproducibility in Agents.

Replay needs inputs, configuration, and relevant execution metadata. Version tools, models, prompts, and data fixtures.

**Remember:** External services may prevent exact token-for-token replay.

## 86. How would you apply reproducibility in a practical Agents task?

Version tools, models, prompts, and data fixtures. Replay needs inputs, configuration, and relevant execution metadata.

**Remember:** Use deterministic fixtures and compare semantic outcomes in live trials.

## 87. What mistake should you avoid with reproducibility in Agents?

External services may prevent exact token-for-token replay. Version tools, models, prompts, and data fixtures.

**Remember:** Replay needs inputs, configuration, and relevant execution metadata.

## 88. How would you verify reproducibility in a Agents implementation?

Use deterministic fixtures and compare semantic outcomes in live trials. External services may prevent exact token-for-token replay.

**Remember:** Version tools, models, prompts, and data fixtures.

## 89. Explain benchmark contamination in Agents.

A holdout loses value when used during tuning. Track test provenance and maintain independent cases.

**Remember:** Fixing only known examples may not improve general tasks.

## 90. How would you apply benchmark contamination in a practical Agents task?

Track test provenance and maintain independent cases. A holdout loses value when used during tuning.

**Remember:** Evaluate fresh tasks after freezing configuration.

## 91. What mistake should you avoid with benchmark contamination in Agents?

Fixing only known examples may not improve general tasks. Track test provenance and maintain independent cases.

**Remember:** A holdout loses value when used during tuning.

## 92. How would you verify benchmark contamination in a Agents implementation?

Evaluate fresh tasks after freezing configuration. Fixing only known examples may not improve general tasks.

**Remember:** Track test provenance and maintain independent cases.

## 93. Explain accessible interaction in Agents.

Agent status and controls must support diverse users. Provide keyboard access, readable errors, and concise status updates.

**Remember:** Announcing every streamed token can overwhelm assistive technology.

## 94. How would you apply accessible interaction in a practical Agents task?

Provide keyboard access, readable errors, and concise status updates. Agent status and controls must support diverse users.

**Remember:** Test focus, announcements, and action review controls.

## 95. What mistake should you avoid with accessible interaction in Agents?

Announcing every streamed token can overwhelm assistive technology. Provide keyboard access, readable errors, and concise status updates.

**Remember:** Agent status and controls must support diverse users.

## 96. How would you verify accessible interaction in a Agents implementation?

Test focus, announcements, and action review controls. Announcing every streamed token can overwhelm assistive technology.

**Remember:** Provide keyboard access, readable errors, and concise status updates.

## 97. Explain decommissioning in Agents.

Retirement includes credentials, workers, schedules, and retained state. Revoke access, stop jobs, and apply retention policies.

**Remember:** Removing the UI leaves background capabilities active.

## 98. How would you apply decommissioning in a practical Agents task?

Revoke access, stop jobs, and apply retention policies. Retirement includes credentials, workers, schedules, and retained state.

**Remember:** Verify no scheduled or tool action succeeds after shutdown.

## 99. What mistake should you avoid with decommissioning in Agents?

Removing the UI leaves background capabilities active. Revoke access, stop jobs, and apply retention policies.

**Remember:** Retirement includes credentials, workers, schedules, and retained state.

## 100. How would you verify decommissioning in a Agents implementation?

Verify no scheduled or tool action succeeds after shutdown. Removing the UI leaves background capabilities active.

**Remember:** Revoke access, stop jobs, and apply retention policies.

## Further reading

- [Agent patterns](https://www.anthropic.com/research/building-effective-agents)


# Forward Deployed Engineering — Interview Questions

100 interview practice questions and concise answers. Product and runtime behavior can vary; check current documentation.

## 1. What does a forward deployed engineer do?

An FDE works closely with customers to turn operational problems into deployed software. The role often combines discovery, integration, engineering, delivery, and feedback to the product team; responsibilities vary by employer.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 2. How is an FDE different from a solutions engineer?

The boundary varies by company. Explain whether the role owns production implementation, pre-sales evaluation, ongoing operations, or all three rather than assuming a universal title definition.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 3. How do you start an ambiguous customer engagement?

Identify users, the operational decision, current workflow, constraints, and a measurable outcome. Validate the problem with concrete examples before selecting a technical solution.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 4. How do you run a discovery session?

Ask stakeholders to walk through a recent real case, inspect the data and handoffs, and record pain points and success criteria. Confirm your understanding and distinguish stated requests from the underlying problem.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 5. How do you scope a first pilot?

Choose one valuable workflow with accessible data, a named owner, and a measurable baseline. Agree on acceptance criteria, exclusions, rollout conditions, and the decision that follows the pilot.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 6. How do you translate business goals into metrics?

Connect the goal to an observable workflow measure such as resolution time, error rate, or throughput. Add quality and risk guardrails so improving one metric does not hide worse outcomes elsewhere.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 7. How do you handle poor customer data?

Profile completeness, consistency, lineage, and update frequency with the customer. Fix critical defects or narrow scope, and make data limitations visible rather than masking them with model outputs.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 8. How would you integrate a legacy system?

Clarify supported interfaces, authentication, data ownership, and operational limits. Start with a small end-to-end integration, add monitoring and recovery, and avoid undocumented dependencies where possible.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 9. How do you choose build versus buy?

Compare requirements, integration effort, security, reliability, cost, and ownership over time. Validate the hardest requirement with a small proof of concept and consider exit or migration costs.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 10. How do you explain technical tradeoffs to a customer?

Present options in terms of user outcomes, delivery time, recurring cost, and risk. Recommend one option with assumptions and a clear way to revisit the decision as evidence changes.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 11. How do you respond to scope creep?

Acknowledge the new need and assess its impact on the agreed outcome. Offer an explicit tradeoff, phased delivery, or revised timeline rather than silently expanding commitments.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 12. How do you handle conflicting stakeholders?

Identify the decision owner and document each stakeholder's goals and constraints. Use shared evidence and acceptance criteria to surface tradeoffs, then record the agreed decision.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 13. What makes a good technical demo?

Show a realistic user journey tied to the customer's success criteria. Explain limitations, use safe representative data, and have a fallback without presenting a staged result as a live capability.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 14. How do you move from prototype to production?

Add authentication, authorization, monitoring, recovery, capacity planning, and deployment controls. Confirm support ownership and acceptance tests; a successful demo alone does not establish readiness.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 15. How would you handle a production outage?

Prioritize containment and service restoration, assign clear ownership, and communicate verified facts and updates. Afterward, document causes and implement actions that reduce recurrence and improve detection.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 16. How do you protect customer data during delivery?

Use least-privilege access, approved environments, encryption, and limited retention. Keep production data out of demos and logs unless specifically approved and necessary.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 17. How do you measure adoption after launch?

Measure repeated use in the target workflow and the agreed operational outcome. Combine telemetry with user feedback to distinguish low awareness, usability problems, and a solution that misses the real need.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 18. How do you hand a solution over?

Provide runbooks, architecture and integration documentation, known limitations, and named operational owners. Walk through recovery and common changes, and verify that the receiving team can operate it.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 19. How should you answer behavioral interview questions?

Use a real situation, explain your responsibility and actions, and report the actual outcome and lesson. Do not invent metrics or experience; if the scenario is hypothetical, label it clearly.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 20. Design a document assistant for an enterprise customer.

Begin with users, permitted documents, freshness needs, and success metrics. Propose authorized ingestion and retrieval, grounded answers, evaluation, monitoring, and phased rollout; discuss cost and latency with a fallback for unsupported questions.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 21. Explain stakeholder mapping in Forward Deployed Engineer.

Delivery requires users, decision owners, approvers, and maintainers. Document roles and decision rights before committing scope.

**Remember:** The loudest stakeholder may not own adoption decisions.

## 22. How would you apply stakeholder mapping in a practical Forward Deployed Engineer task?

Document roles and decision rights before committing scope. Delivery requires users, decision owners, approvers, and maintainers.

**Remember:** Verify sign-off paths and representative user involvement.

## 23. What mistake should you avoid with stakeholder mapping in Forward Deployed Engineer?

The loudest stakeholder may not own adoption decisions. Document roles and decision rights before committing scope.

**Remember:** Delivery requires users, decision owners, approvers, and maintainers.

## 24. How would you verify stakeholder mapping in a Forward Deployed Engineer implementation?

Verify sign-off paths and representative user involvement. The loudest stakeholder may not own adoption decisions.

**Remember:** Document roles and decision rights before committing scope.

## 25. Explain workflow observation in Forward Deployed Engineer.

Observing work reveals exceptions absent from interviews. Follow representative cases through data and handoffs.

**Remember:** A polished demo can hide difficult daily cases.

## 26. How would you apply workflow observation in a practical Forward Deployed Engineer task?

Follow representative cases through data and handoffs. Observing work reveals exceptions absent from interviews.

**Remember:** Compare multiple users and confirm findings with examples.

## 27. What mistake should you avoid with workflow observation in Forward Deployed Engineer?

A polished demo can hide difficult daily cases. Follow representative cases through data and handoffs.

**Remember:** Observing work reveals exceptions absent from interviews.

## 28. How would you verify workflow observation in a Forward Deployed Engineer implementation?

Compare multiple users and confirm findings with examples. A polished demo can hide difficult daily cases.

**Remember:** Follow representative cases through data and handoffs.

## 29. Explain problem reframing in Forward Deployed Engineer.

A requested feature may be one solution to a deeper need. Restate the outcome and compare simpler alternatives.

**Remember:** Reframing without listening can dismiss valid experience.

## 30. How would you apply problem reframing in a practical Forward Deployed Engineer task?

Restate the outcome and compare simpler alternatives. A requested feature may be one solution to a deeper need.

**Remember:** Confirm the problem statement and measurable success criteria.

## 31. What mistake should you avoid with problem reframing in Forward Deployed Engineer?

Reframing without listening can dismiss valid experience. Restate the outcome and compare simpler alternatives.

**Remember:** A requested feature may be one solution to a deeper need.

## 32. How would you verify problem reframing in a Forward Deployed Engineer implementation?

Confirm the problem statement and measurable success criteria. Reframing without listening can dismiss valid experience.

**Remember:** Restate the outcome and compare simpler alternatives.

## 33. Explain assumption registers in Forward Deployed Engineer.

Plans depend on assumptions about data, access, and people. Record assumptions with owners and validation deadlines.

**Remember:** Hidden assumptions become late delivery blockers.

## 34. How would you apply assumption registers in a practical Forward Deployed Engineer task?

Record assumptions with owners and validation deadlines. Plans depend on assumptions about data, access, and people.

**Remember:** Validate high-impact assumptions before dependent work.

## 35. What mistake should you avoid with assumption registers in Forward Deployed Engineer?

Hidden assumptions become late delivery blockers. Record assumptions with owners and validation deadlines.

**Remember:** Plans depend on assumptions about data, access, and people.

## 36. How would you verify assumption registers in a Forward Deployed Engineer implementation?

Validate high-impact assumptions before dependent work. Hidden assumptions become late delivery blockers.

**Remember:** Record assumptions with owners and validation deadlines.

## 37. Explain acceptance criteria in Forward Deployed Engineer.

Acceptance criteria describe observable delivery success. Write testable examples and operational constraints.

**Remember:** Vague expectations allow incompatible interpretations.

## 38. How would you apply acceptance criteria in a practical Forward Deployed Engineer task?

Write testable examples and operational constraints. Acceptance criteria describe observable delivery success.

**Remember:** Run joint tests and document agreed exceptions.

## 39. What mistake should you avoid with acceptance criteria in Forward Deployed Engineer?

Vague expectations allow incompatible interpretations. Write testable examples and operational constraints.

**Remember:** Acceptance criteria describe observable delivery success.

## 40. How would you verify acceptance criteria in a Forward Deployed Engineer implementation?

Run joint tests and document agreed exceptions. Vague expectations allow incompatible interpretations.

**Remember:** Write testable examples and operational constraints.

## 41. Explain integration contracts in Forward Deployed Engineer.

Contracts specify behavior at system boundaries. Document schemas, errors, authentication, limits, and versioning.

**Remember:** Undocumented field changes can break delivery.

## 42. How would you apply integration contracts in a practical Forward Deployed Engineer task?

Document schemas, errors, authentication, limits, and versioning. Contracts specify behavior at system boundaries.

**Remember:** Use compatibility fixtures and consumer contract tests.

## 43. What mistake should you avoid with integration contracts in Forward Deployed Engineer?

Undocumented field changes can break delivery. Document schemas, errors, authentication, limits, and versioning.

**Remember:** Contracts specify behavior at system boundaries.

## 44. How would you verify integration contracts in a Forward Deployed Engineer implementation?

Use compatibility fixtures and consumer contract tests. Undocumented field changes can break delivery.

**Remember:** Document schemas, errors, authentication, limits, and versioning.

## 45. Explain data reconciliation in Forward Deployed Engineer.

Reconciliation compares integrated data with authoritative sources. Check stable IDs, aggregates, counts, and sampled fields.

**Remember:** Matching counts can conceal missing and duplicate records.

## 46. How would you apply data reconciliation in a practical Forward Deployed Engineer task?

Check stable IDs, aggregates, counts, and sampled fields. Reconciliation compares integrated data with authoritative sources.

**Remember:** Test corrections, deletions, and late-arriving changes.

## 47. What mistake should you avoid with data reconciliation in Forward Deployed Engineer?

Matching counts can conceal missing and duplicate records. Check stable IDs, aggregates, counts, and sampled fields.

**Remember:** Reconciliation compares integrated data with authoritative sources.

## 48. How would you verify data reconciliation in a Forward Deployed Engineer implementation?

Test corrections, deletions, and late-arriving changes. Matching counts can conceal missing and duplicate records.

**Remember:** Check stable IDs, aggregates, counts, and sampled fields.

## 49. Explain migration planning in Forward Deployed Engineer.

Migration protects continuity while changing systems. Plan mapping, rehearsal, validation, cutover, and rollback.

**Remember:** A correct backend migration can still disrupt user workflows.

## 50. How would you apply migration planning in a practical Forward Deployed Engineer task?

Plan mapping, rehearsal, validation, cutover, and rollback. Migration protects continuity while changing systems.

**Remember:** Measure downtime and reconciliation in a realistic rehearsal.

## 51. What mistake should you avoid with migration planning in Forward Deployed Engineer?

A correct backend migration can still disrupt user workflows. Plan mapping, rehearsal, validation, cutover, and rollback.

**Remember:** Migration protects continuity while changing systems.

## 52. How would you verify migration planning in a Forward Deployed Engineer implementation?

Measure downtime and reconciliation in a realistic rehearsal. A correct backend migration can still disrupt user workflows.

**Remember:** Plan mapping, rehearsal, validation, cutover, and rollback.

## 53. Explain delivery prioritization in Forward Deployed Engineer.

Priorities balance value, risk, dependencies, and effort. Choose the smallest increment solving a meaningful problem.

**Remember:** Visible features can crowd out reliability work.

## 54. How would you apply delivery prioritization in a practical Forward Deployed Engineer task?

Choose the smallest increment solving a meaningful problem. Priorities balance value, risk, dependencies, and effort.

**Remember:** Compare delivered outcomes with expected value.

## 55. What mistake should you avoid with delivery prioritization in Forward Deployed Engineer?

Visible features can crowd out reliability work. Choose the smallest increment solving a meaningful problem.

**Remember:** Priorities balance value, risk, dependencies, and effort.

## 56. How would you verify delivery prioritization in a Forward Deployed Engineer implementation?

Compare delivered outcomes with expected value. Visible features can crowd out reliability work.

**Remember:** Choose the smallest increment solving a meaningful problem.

## 57. Explain technical debt in Forward Deployed Engineer.

Shortcuts trade current speed against future cost. Record deliberate debt with owner and repayment trigger.

**Remember:** Unrecorded debt becomes an accidental permanent dependency.

## 58. How would you apply technical debt in a practical Forward Deployed Engineer task?

Record deliberate debt with owner and repayment trigger. Shortcuts trade current speed against future cost.

**Remember:** Use incident and change-cost evidence to prioritize repayment.

## 59. What mistake should you avoid with technical debt in Forward Deployed Engineer?

Unrecorded debt becomes an accidental permanent dependency. Record deliberate debt with owner and repayment trigger.

**Remember:** Shortcuts trade current speed against future cost.

## 60. How would you verify technical debt in a Forward Deployed Engineer implementation?

Use incident and change-cost evidence to prioritize repayment. Unrecorded debt becomes an accidental permanent dependency.

**Remember:** Record deliberate debt with owner and repayment trigger.

## 61. Explain customer updates in Forward Deployed Engineer.

Useful updates explain outcomes, uncertainty, and decisions. Distinguish verified facts from estimates using concrete examples.

**Remember:** Overpromising certainty weakens trust when dependencies change.

## 62. How would you apply customer updates in a practical Forward Deployed Engineer task?

Distinguish verified facts from estimates using concrete examples. Useful updates explain outcomes, uncertainty, and decisions.

**Remember:** Confirm stakeholder understanding and track unresolved questions.

## 63. What mistake should you avoid with customer updates in Forward Deployed Engineer?

Overpromising certainty weakens trust when dependencies change. Distinguish verified facts from estimates using concrete examples.

**Remember:** Useful updates explain outcomes, uncertainty, and decisions.

## 64. How would you verify customer updates in a Forward Deployed Engineer implementation?

Confirm stakeholder understanding and track unresolved questions. Overpromising certainty weakens trust when dependencies change.

**Remember:** Distinguish verified facts from estimates using concrete examples.

## 65. Explain security review in Forward Deployed Engineer.

Review examines threats, trust boundaries, and actual controls. Map privileges and data flows with responsible owners.

**Remember:** A generic checklist can miss the architecture's primary risk.

## 66. How would you apply security review in a practical Forward Deployed Engineer task?

Map privileges and data flows with responsible owners. Review examines threats, trust boundaries, and actual controls.

**Remember:** Validate controls through tests and close findings by severity.

## 67. What mistake should you avoid with security review in Forward Deployed Engineer?

A generic checklist can miss the architecture's primary risk. Map privileges and data flows with responsible owners.

**Remember:** Review examines threats, trust boundaries, and actual controls.

## 68. How would you verify security review in a Forward Deployed Engineer implementation?

Validate controls through tests and close findings by severity. A generic checklist can miss the architecture's primary risk.

**Remember:** Map privileges and data flows with responsible owners.

## 69. Explain performance budgets in Forward Deployed Engineer.

Budgets allocate latency and resource limits to workflows. Measure baseline behavior and assign stage-level limits.

**Remember:** Optimizing non-bottlenecks may not improve user outcomes.

## 70. How would you apply performance budgets in a practical Forward Deployed Engineer task?

Measure baseline behavior and assign stage-level limits. Budgets allocate latency and resource limits to workflows.

**Remember:** Load-test realistic concurrency and tail latency.

## 71. What mistake should you avoid with performance budgets in Forward Deployed Engineer?

Optimizing non-bottlenecks may not improve user outcomes. Measure baseline behavior and assign stage-level limits.

**Remember:** Budgets allocate latency and resource limits to workflows.

## 72. How would you verify performance budgets in a Forward Deployed Engineer implementation?

Load-test realistic concurrency and tail latency. Optimizing non-bottlenecks may not improve user outcomes.

**Remember:** Measure baseline behavior and assign stage-level limits.

## 73. Explain operational runbooks in Forward Deployed Engineer.

Runbooks explain diagnosis, recovery, and escalation. Include symptoms, safe steps, permissions, and verification.

**Remember:** Outdated commands make incident guidance unreliable.

## 74. How would you apply operational runbooks in a practical Forward Deployed Engineer task?

Include symptoms, safe steps, permissions, and verification. Runbooks explain diagnosis, recovery, and escalation.

**Remember:** Have another operator rehearse recovery from the document.

## 75. What mistake should you avoid with operational runbooks in Forward Deployed Engineer?

Outdated commands make incident guidance unreliable. Include symptoms, safe steps, permissions, and verification.

**Remember:** Runbooks explain diagnosis, recovery, and escalation.

## 76. How would you verify operational runbooks in a Forward Deployed Engineer implementation?

Have another operator rehearse recovery from the document. Outdated commands make incident guidance unreliable.

**Remember:** Include symptoms, safe steps, permissions, and verification.

## 77. Explain user enablement in Forward Deployed Engineer.

Adoption requires users to operate the delivered workflow independently. Provide role-specific practice and feedback.

**Remember:** One presentation rarely proves successful behavior change.

## 78. How would you apply user enablement in a practical Forward Deployed Engineer task?

Provide role-specific practice and feedback. Adoption requires users to operate the delivered workflow independently.

**Remember:** Measure independent task success and recurring support needs.

## 79. What mistake should you avoid with user enablement in Forward Deployed Engineer?

One presentation rarely proves successful behavior change. Provide role-specific practice and feedback.

**Remember:** Adoption requires users to operate the delivered workflow independently.

## 80. How would you verify user enablement in a Forward Deployed Engineer implementation?

Measure independent task success and recurring support needs. One presentation rarely proves successful behavior change.

**Remember:** Provide role-specific practice and feedback.

## 81. Explain product feedback in Forward Deployed Engineer.

Customer work can reveal reusable product requirements. Separate recurring patterns from engagement-specific constraints.

**Remember:** Every bespoke request should not become a core feature.

## 82. How would you apply product feedback in a practical Forward Deployed Engineer task?

Separate recurring patterns from engagement-specific constraints. Customer work can reveal reusable product requirements.

**Remember:** Validate patterns across engagements with product owners.

## 83. What mistake should you avoid with product feedback in Forward Deployed Engineer?

Every bespoke request should not become a core feature. Separate recurring patterns from engagement-specific constraints.

**Remember:** Customer work can reveal reusable product requirements.

## 84. How would you verify product feedback in a Forward Deployed Engineer implementation?

Validate patterns across engagements with product owners. Every bespoke request should not become a core feature.

**Remember:** Separate recurring patterns from engagement-specific constraints.

## 85. Explain ROI analysis in Forward Deployed Engineer.

ROI compares benefits with implementation and ongoing cost. Use explicit baseline assumptions and sensitivity ranges.

**Remember:** Ignoring maintenance and adoption overstates value.

## 86. How would you apply ROI analysis in a practical Forward Deployed Engineer task?

Use explicit baseline assumptions and sensitivity ranges. ROI compares benefits with implementation and ongoing cost.

**Remember:** Recalculate using observed usage and operational outcomes.

## 87. What mistake should you avoid with ROI analysis in Forward Deployed Engineer?

Ignoring maintenance and adoption overstates value. Use explicit baseline assumptions and sensitivity ranges.

**Remember:** ROI compares benefits with implementation and ongoing cost.

## 88. How would you verify ROI analysis in a Forward Deployed Engineer implementation?

Recalculate using observed usage and operational outcomes. Ignoring maintenance and adoption overstates value.

**Remember:** Use explicit baseline assumptions and sensitivity ranges.

## 89. Explain procurement dependencies in Forward Deployed Engineer.

Legal, vendor, and hosting approvals constrain deployment. Identify required evidence and actual approval owners early.

**Remember:** Late discovery can delay an otherwise ready system.

## 90. How would you apply procurement dependencies in a practical Forward Deployed Engineer task?

Identify required evidence and actual approval owners early. Legal, vendor, and hosting approvals constrain deployment.

**Remember:** Track approvals as delivery dependencies.

## 91. What mistake should you avoid with procurement dependencies in Forward Deployed Engineer?

Late discovery can delay an otherwise ready system. Identify required evidence and actual approval owners early.

**Remember:** Legal, vendor, and hosting approvals constrain deployment.

## 92. How would you verify procurement dependencies in a Forward Deployed Engineer implementation?

Track approvals as delivery dependencies. Late discovery can delay an otherwise ready system.

**Remember:** Identify required evidence and actual approval owners early.

## 93. Explain ethical AI delivery in Forward Deployed Engineer.

Delivery must consider affected users and foreseeable misuse. Agree acceptable use, review needs, and limitations.

**Remember:** Accuracy alone does not establish fairness or appropriateness.

## 94. How would you apply ethical AI delivery in a practical Forward Deployed Engineer task?

Agree acceptable use, review needs, and limitations. Delivery must consider affected users and foreseeable misuse.

**Remember:** Evaluate relevant groups and monitor harmful outcomes.

## 95. What mistake should you avoid with ethical AI delivery in Forward Deployed Engineer?

Accuracy alone does not establish fairness or appropriateness. Agree acceptable use, review needs, and limitations.

**Remember:** Delivery must consider affected users and foreseeable misuse.

## 96. How would you verify ethical AI delivery in a Forward Deployed Engineer implementation?

Evaluate relevant groups and monitor harmful outcomes. Accuracy alone does not establish fairness or appropriateness.

**Remember:** Agree acceptable use, review needs, and limitations.

## 97. Explain post-launch reviews in Forward Deployed Engineer.

Reviews compare actual adoption and outcomes with the plan. Collect quality, cost, incidents, and user feedback.

**Remember:** Launch success can hide ongoing manual work or low usage.

## 98. How would you apply post-launch reviews in a practical Forward Deployed Engineer task?

Collect quality, cost, incidents, and user feedback. Reviews compare actual adoption and outcomes with the plan.

**Remember:** Assign follow-up owners and measure resulting improvements.

## 99. What mistake should you avoid with post-launch reviews in Forward Deployed Engineer?

Launch success can hide ongoing manual work or low usage. Collect quality, cost, incidents, and user feedback.

**Remember:** Reviews compare actual adoption and outcomes with the plan.

## 100. How would you verify post-launch reviews in a Forward Deployed Engineer implementation?

Assign follow-up owners and measure resulting improvements. Launch success can hide ongoing manual work or low usage.

**Remember:** Collect quality, cost, incidents, and user feedback.

## Further reading

- [Forward-deployed role context](https://www.palantir.com/careers/students-and-early-talent)


# Java — Interview Questions

100 interview practice questions and concise answers. Product and runtime behavior can vary; check current documentation.

## 1. Explain reference and value equality in Java.

Object == compares identity; equals defines logical equality. Use Objects.equals for nullable value comparisons.

**Remember:** String interning can make incorrect identity comparisons appear reliable.

## 2. How would you apply reference and value equality in a practical Java task?

Use Objects.equals for nullable value comparisons. Object == compares identity; equals defines logical equality.

**Remember:** Compare separately allocated equal objects, aliases, and nulls.

## 3. What mistake should you avoid with reference and value equality in Java?

String interning can make incorrect identity comparisons appear reliable. Use Objects.equals for nullable value comparisons.

**Remember:** Object == compares identity; equals defines logical equality.

## 4. How would you verify reference and value equality in a Java implementation?

Compare separately allocated equal objects, aliases, and nulls. String interning can make incorrect identity comparisons appear reliable.

**Remember:** Use Objects.equals for nullable value comparisons.

## 5. Explain equals and hashCode in Java.

Equal objects must have equal hashes, but collisions are allowed. Override both consistently for value-based map keys.

**Remember:** Mutating equality fields after insertion can break lookup.

## 6. How would you apply equals and hashCode in a practical Java task?

Override both consistently for value-based map keys. Equal objects must have equal hashes, but collisions are allowed.

**Remember:** Test symmetry, transitivity, and HashSet membership.

## 7. What mistake should you avoid with equals and hashCode in Java?

Mutating equality fields after insertion can break lookup. Override both consistently for value-based map keys.

**Remember:** Equal objects must have equal hashes, but collisions are allowed.

## 8. How would you verify equals and hashCode in a Java implementation?

Test symmetry, transitivity, and HashSet membership. Mutating equality fields after insertion can break lookup.

**Remember:** Override both consistently for value-based map keys.

## 9. Explain String immutability in Java.

Strings cannot change after construction. Use StringBuilder for substantial repeated concatenation.

**Remember:** A final reference is not the same as a deeply immutable object.

## 10. How would you apply String immutability in a practical Java task?

Use StringBuilder for substantial repeated concatenation. Strings cannot change after construction.

**Remember:** Verify original values and benchmark allocation-sensitive loops.

## 11. What mistake should you avoid with String immutability in Java?

A final reference is not the same as a deeply immutable object. Use StringBuilder for substantial repeated concatenation.

**Remember:** Strings cannot change after construction.

## 12. How would you verify String immutability in a Java implementation?

Verify original values and benchmark allocation-sensitive loops. A final reference is not the same as a deeply immutable object.

**Remember:** Use StringBuilder for substantial repeated concatenation.

## 13. Explain boxing and unboxing in Java.

Boxing wraps primitives; unboxing extracts their values. Prefer primitives where nullability and generic APIs are unnecessary.

**Remember:** Unboxing null throws NullPointerException.

## 14. How would you apply boxing and unboxing in a practical Java task?

Prefer primitives where nullability and generic APIs are unnecessary. Boxing wraps primitives; unboxing extracts their values.

**Remember:** Test nulls and wrapper values beyond common cache ranges.

## 15. What mistake should you avoid with boxing and unboxing in Java?

Unboxing null throws NullPointerException. Prefer primitives where nullability and generic APIs are unnecessary.

**Remember:** Boxing wraps primitives; unboxing extracts their values.

## 16. How would you verify boxing and unboxing in a Java implementation?

Test nulls and wrapper values beyond common cache ranges. Unboxing null throws NullPointerException.

**Remember:** Prefer primitives where nullability and generic APIs are unnecessary.

## 17. Explain generic invariance in Java.

List<Integer> is not a subtype of List<Number>. Use bounded wildcards to express safe producer and consumer APIs.

**Remember:** Raw types bypass useful compile-time checks.

## 18. How would you apply generic invariance in a practical Java task?

Use bounded wildcards to express safe producer and consumer APIs. List<Integer> is not a subtype of List<Number>.

**Remember:** Compile representative accepted and rejected usages.

## 19. What mistake should you avoid with generic invariance in Java?

Raw types bypass useful compile-time checks. Use bounded wildcards to express safe producer and consumer APIs.

**Remember:** List<Integer> is not a subtype of List<Number>.

## 20. How would you verify generic invariance in a Java implementation?

Compile representative accepted and rejected usages. Raw types bypass useful compile-time checks.

**Remember:** Use bounded wildcards to express safe producer and consumer APIs.

## 21. Explain PECS wildcards in Java.

Producers commonly use extends and consumers use super. Read from List<? extends Number> and add integers to List<? super Integer>.

**Remember:** An extends list cannot generally accept arbitrary non-null values.

## 22. How would you apply PECS wildcards in a practical Java task?

Read from List<? extends Number> and add integers to List<? super Integer>. Producers commonly use extends and consumers use super.

**Remember:** Demonstrate permitted reads and writes with compilation tests.

## 23. What mistake should you avoid with PECS wildcards in Java?

An extends list cannot generally accept arbitrary non-null values. Read from List<? extends Number> and add integers to List<? super Integer>.

**Remember:** Producers commonly use extends and consumers use super.

## 24. How would you verify PECS wildcards in a Java implementation?

Demonstrate permitted reads and writes with compilation tests. An extends list cannot generally accept arbitrary non-null values.

**Remember:** Read from List<? extends Number> and add integers to List<? super Integer>.

## 25. Explain ArrayList versus LinkedList in Java.

ArrayList supports indexed access; LinkedList must traverse nodes. Use ArrayList for typical lists and consider ArrayDeque for queues.

**Remember:** LinkedList insertion is not constant time if locating the position is included.

## 26. How would you apply ArrayList versus LinkedList in a practical Java task?

Use ArrayList for typical lists and consider ArrayDeque for queues. ArrayList supports indexed access; LinkedList must traverse nodes.

**Remember:** Benchmark realistic traversal and mutation patterns.

## 27. What mistake should you avoid with ArrayList versus LinkedList in Java?

LinkedList insertion is not constant time if locating the position is included. Use ArrayList for typical lists and consider ArrayDeque for queues.

**Remember:** ArrayList supports indexed access; LinkedList must traverse nodes.

## 28. How would you verify ArrayList versus LinkedList in a Java implementation?

Benchmark realistic traversal and mutation patterns. LinkedList insertion is not constant time if locating the position is included.

**Remember:** Use ArrayList for typical lists and consider ArrayDeque for queues.

## 29. Explain HashMap semantics in Java.

HashMap uses hashing and equality without a general iteration-order guarantee. Choose immutable well-defined keys and appropriate capacity.

**Remember:** HashMap is not a thread-safe shared mutable map.

## 30. How would you apply HashMap semantics in a practical Java task?

Choose immutable well-defined keys and appropriate capacity. HashMap uses hashing and equality without a general iteration-order guarantee.

**Remember:** Test equal keys, collisions, replacement, and missing values.

## 31. What mistake should you avoid with HashMap semantics in Java?

HashMap is not a thread-safe shared mutable map. Choose immutable well-defined keys and appropriate capacity.

**Remember:** HashMap uses hashing and equality without a general iteration-order guarantee.

## 32. How would you verify HashMap semantics in a Java implementation?

Test equal keys, collisions, replacement, and missing values. HashMap is not a thread-safe shared mutable map.

**Remember:** Choose immutable well-defined keys and appropriate capacity.

## 33. Explain ConcurrentHashMap in Java.

ConcurrentHashMap supports concurrent mapping operations. Use compute or merge for atomic per-key updates.

**Remember:** Get-then-put is not atomic, and null keys or values are rejected.

## 34. How would you apply ConcurrentHashMap in a practical Java task?

Use compute or merge for atomic per-key updates. ConcurrentHashMap supports concurrent mapping operations.

**Remember:** Run concurrent updates and verify final counts.

## 35. What mistake should you avoid with ConcurrentHashMap in Java?

Get-then-put is not atomic, and null keys or values are rejected. Use compute or merge for atomic per-key updates.

**Remember:** ConcurrentHashMap supports concurrent mapping operations.

## 36. How would you verify ConcurrentHashMap in a Java implementation?

Run concurrent updates and verify final counts. Get-then-put is not atomic, and null keys or values are rejected.

**Remember:** Use compute or merge for atomic per-key updates.

## 37. Explain exception categories in Java.

Checked exceptions must be caught or declared; unchecked exceptions need not be. Preserve causes when translating meaningful failures.

**Remember:** Catching Exception and continuing can hide broken invariants.

## 38. How would you apply exception categories in a practical Java task?

Preserve causes when translating meaningful failures. Checked exceptions must be caught or declared; unchecked exceptions need not be.

**Remember:** Assert exception types, causes, and recovery behavior.

## 39. What mistake should you avoid with exception categories in Java?

Catching Exception and continuing can hide broken invariants. Preserve causes when translating meaningful failures.

**Remember:** Checked exceptions must be caught or declared; unchecked exceptions need not be.

## 40. How would you verify exception categories in a Java implementation?

Assert exception types, causes, and recovery behavior. Catching Exception and continuing can hide broken invariants.

**Remember:** Preserve causes when translating meaningful failures.

## 41. Explain try-with-resources in Java.

AutoCloseable resources close when the block exits. Use it for owned files, streams, and database resources.

**Remember:** Close failures may be suppressed by a primary exception.

## 42. How would you apply try-with-resources in a practical Java task?

Use it for owned files, streams, and database resources. AutoCloseable resources close when the block exits.

**Remember:** Test normal completion, body failure, and suppressed exceptions.

## 43. What mistake should you avoid with try-with-resources in Java?

Close failures may be suppressed by a primary exception. Use it for owned files, streams, and database resources.

**Remember:** AutoCloseable resources close when the block exits.

## 44. How would you verify try-with-resources in a Java implementation?

Test normal completion, body failure, and suppressed exceptions. Close failures may be suppressed by a primary exception.

**Remember:** Use it for owned files, streams, and database resources.

## 45. Explain interfaces versus abstract classes in Java.

Interfaces express contracts; abstract classes can share instance state. Prefer composition unless shared inheritance genuinely fits the contract.

**Remember:** Implementation inheritance can violate substitutability.

## 46. How would you apply interfaces versus abstract classes in a practical Java task?

Prefer composition unless shared inheritance genuinely fits the contract. Interfaces express contracts; abstract classes can share instance state.

**Remember:** Test each implementation through its public contract.

## 47. What mistake should you avoid with interfaces versus abstract classes in Java?

Implementation inheritance can violate substitutability. Prefer composition unless shared inheritance genuinely fits the contract.

**Remember:** Interfaces express contracts; abstract classes can share instance state.

## 48. How would you verify interfaces versus abstract classes in a Java implementation?

Test each implementation through its public contract. Implementation inheritance can violate substitutability.

**Remember:** Prefer composition unless shared inheritance genuinely fits the contract.

## 49. Explain records in Java.

Records generate data-carrier accessors and value methods. Validate components in constructors and copy mutable inputs when needed.

**Remember:** Records are shallowly immutable.

## 50. How would you apply records in a practical Java task?

Validate components in constructors and copy mutable inputs when needed. Records generate data-carrier accessors and value methods.

**Remember:** Attempt mutation through constructor inputs and returned components.

## 51. What mistake should you avoid with records in Java?

Records are shallowly immutable. Validate components in constructors and copy mutable inputs when needed.

**Remember:** Records generate data-carrier accessors and value methods.

## 52. How would you verify records in a Java implementation?

Attempt mutation through constructor inputs and returned components. Records are shallowly immutable.

**Remember:** Validate components in constructors and copy mutable inputs when needed.

## 53. Explain immutable object design in Java.

Immutable objects expose no observable state changes after construction. Use final fields, validation, and defensive copies.

**Remember:** Returning mutable internals breaks immutability.

## 54. How would you apply immutable object design in a practical Java task?

Use final fields, validation, and defensive copies. Immutable objects expose no observable state changes after construction.

**Remember:** Test mutation through all exposed references.

## 55. What mistake should you avoid with immutable object design in Java?

Returning mutable internals breaks immutability. Use final fields, validation, and defensive copies.

**Remember:** Immutable objects expose no observable state changes after construction.

## 56. How would you verify immutable object design in a Java implementation?

Test mutation through all exposed references. Returning mutable internals breaks immutability.

**Remember:** Use final fields, validation, and defensive copies.

## 57. Explain stream laziness in Java.

Intermediate operations run as demanded by a terminal operation. Use clear map-filter-reduce pipelines.

**Remember:** Streams are generally single-use; side effects complicate parallel processing.

## 58. How would you apply stream laziness in a practical Java task?

Use clear map-filter-reduce pipelines. Intermediate operations run as demanded by a terminal operation.

**Remember:** Test results without relying on undocumented execution details.

## 59. What mistake should you avoid with stream laziness in Java?

Streams are generally single-use; side effects complicate parallel processing. Use clear map-filter-reduce pipelines.

**Remember:** Intermediate operations run as demanded by a terminal operation.

## 60. How would you verify stream laziness in a Java implementation?

Test results without relying on undocumented execution details. Streams are generally single-use; side effects complicate parallel processing.

**Remember:** Use clear map-filter-reduce pipelines.

## 61. Explain stream collectors in Java.

Collectors combine elements into collections or summaries. Use groupingBy and explicit duplicate-key merge policies.

**Remember:** toMap can fail on duplicate keys without a merge function.

## 62. How would you apply stream collectors in a practical Java task?

Use groupingBy and explicit duplicate-key merge policies. Collectors combine elements into collections or summaries.

**Remember:** Test empty input, duplicates, and ordering requirements.

## 63. What mistake should you avoid with stream collectors in Java?

toMap can fail on duplicate keys without a merge function. Use groupingBy and explicit duplicate-key merge policies.

**Remember:** Collectors combine elements into collections or summaries.

## 64. How would you verify stream collectors in a Java implementation?

Test empty input, duplicates, and ordering requirements. toMap can fail on duplicate keys without a merge function.

**Remember:** Use groupingBy and explicit duplicate-key merge policies.

## 65. Explain Optional in Java.

Optional represents presence or absence, often in return values. Compose map and flatMap and use lazy orElseGet when appropriate.

**Remember:** orElse evaluates its fallback argument eagerly.

## 66. How would you apply Optional in a practical Java task?

Compose map and flatMap and use lazy orElseGet when appropriate. Optional represents presence or absence, often in return values.

**Remember:** Test present and empty values and fallback execution counts.

## 67. What mistake should you avoid with Optional in Java?

orElse evaluates its fallback argument eagerly. Compose map and flatMap and use lazy orElseGet when appropriate.

**Remember:** Optional represents presence or absence, often in return values.

## 68. How would you verify Optional in a Java implementation?

Test present and empty values and fallback execution counts. orElse evaluates its fallback argument eagerly.

**Remember:** Compose map and flatMap and use lazy orElseGet when appropriate.

## 69. Explain memory visibility in Java.

Thread visibility requires defined happens-before relationships. Use locks, volatile, atomics, or concurrent abstractions.

**Remember:** volatile does not make count++ atomic.

## 70. How would you apply memory visibility in a practical Java task?

Use locks, volatile, atomics, or concurrent abstractions. Thread visibility requires defined happens-before relationships.

**Remember:** Reason about synchronization and use concurrency stress tests.

## 71. What mistake should you avoid with memory visibility in Java?

volatile does not make count++ atomic. Use locks, volatile, atomics, or concurrent abstractions.

**Remember:** Thread visibility requires defined happens-before relationships.

## 72. How would you verify memory visibility in a Java implementation?

Reason about synchronization and use concurrency stress tests. volatile does not make count++ atomic.

**Remember:** Use locks, volatile, atomics, or concurrent abstractions.

## 73. Explain synchronized monitors in Java.

A monitor provides mutual exclusion and visibility. Protect each invariant with a consistent lock.

**Remember:** Different locks do not protect the same shared invariant.

## 74. How would you apply synchronized monitors in a practical Java task?

Protect each invariant with a consistent lock. A monitor provides mutual exclusion and visibility.

**Remember:** Test concurrent operations and inspect lock ordering.

## 75. What mistake should you avoid with synchronized monitors in Java?

Different locks do not protect the same shared invariant. Protect each invariant with a consistent lock.

**Remember:** A monitor provides mutual exclusion and visibility.

## 76. How would you verify synchronized monitors in a Java implementation?

Test concurrent operations and inspect lock ordering. Different locks do not protect the same shared invariant.

**Remember:** Protect each invariant with a consistent lock.

## 77. Explain atomic variables in Java.

Atomic classes provide specified atomic operations. Use atomic increments for independent counters.

**Remember:** Separate atomics do not make multi-field invariants atomic.

## 78. How would you apply atomic variables in a practical Java task?

Use atomic increments for independent counters. Atomic classes provide specified atomic operations.

**Remember:** Test counts and use locks for related state transitions.

## 79. What mistake should you avoid with atomic variables in Java?

Separate atomics do not make multi-field invariants atomic. Use atomic increments for independent counters.

**Remember:** Atomic classes provide specified atomic operations.

## 80. How would you verify atomic variables in a Java implementation?

Test counts and use locks for related state transitions. Separate atomics do not make multi-field invariants atomic.

**Remember:** Use atomic increments for independent counters.

## 81. Explain executor services in Java.

Executors separate task submission from execution management. Bound concurrency and reliably shut down owned executors.

**Remember:** Unbounded queues can turn overload into memory growth.

## 82. How would you apply executor services in a practical Java task?

Bound concurrency and reliably shut down owned executors. Executors separate task submission from execution management.

**Remember:** Test rejection, cancellation, shutdown, and task failures.

## 83. What mistake should you avoid with executor services in Java?

Unbounded queues can turn overload into memory growth. Bound concurrency and reliably shut down owned executors.

**Remember:** Executors separate task submission from execution management.

## 84. How would you verify executor services in a Java implementation?

Test rejection, cancellation, shutdown, and task failures. Unbounded queues can turn overload into memory growth.

**Remember:** Bound concurrency and reliably shut down owned executors.

## 85. Explain virtual threads in Java.

Virtual threads support many blocking-style concurrent tasks. Use supported APIs for suitable I/O-heavy workloads.

**Remember:** They do not accelerate CPU work or remove downstream resource limits.

## 86. How would you apply virtual threads in a practical Java task?

Use supported APIs for suitable I/O-heavy workloads. Virtual threads support many blocking-style concurrent tasks.

**Remember:** Load-test actual JDK behavior and downstream saturation.

## 87. What mistake should you avoid with virtual threads in Java?

They do not accelerate CPU work or remove downstream resource limits. Use supported APIs for suitable I/O-heavy workloads.

**Remember:** Virtual threads support many blocking-style concurrent tasks.

## 88. How would you verify virtual threads in a Java implementation?

Load-test actual JDK behavior and downstream saturation. They do not accelerate CPU work or remove downstream resource limits.

**Remember:** Use supported APIs for suitable I/O-heavy workloads.

## 89. Explain CompletableFuture in Java.

CompletableFuture composes asynchronous results and failures. Use thenCompose for dependent asynchronous work and thenCombine for independent results.

**Remember:** Blocking joins on limited executors can exhaust workers.

## 90. How would you apply CompletableFuture in a practical Java task?

Use thenCompose for dependent asynchronous work and thenCombine for independent results. CompletableFuture composes asynchronous results and failures.

**Remember:** Test failures, cancellation semantics, and executor selection.

## 91. What mistake should you avoid with CompletableFuture in Java?

Blocking joins on limited executors can exhaust workers. Use thenCompose for dependent asynchronous work and thenCombine for independent results.

**Remember:** CompletableFuture composes asynchronous results and failures.

## 92. How would you verify CompletableFuture in a Java implementation?

Test failures, cancellation semantics, and executor selection. Blocking joins on limited executors can exhaust workers.

**Remember:** Use thenCompose for dependent asynchronous work and thenCombine for independent results.

## 93. Explain garbage collection and retained objects in Java.

GC reclaims unreachable objects, not all unused application data. Bound caches and remove unnecessary long-lived references.

**Remember:** Static collections can retain objects indefinitely.

## 94. How would you apply garbage collection and retained objects in a practical Java task?

Bound caches and remove unnecessary long-lived references. GC reclaims unreachable objects, not all unused application data.

**Remember:** Inspect heap snapshots and retained paths under load.

## 95. What mistake should you avoid with garbage collection and retained objects in Java?

Static collections can retain objects indefinitely. Bound caches and remove unnecessary long-lived references.

**Remember:** GC reclaims unreachable objects, not all unused application data.

## 96. How would you verify garbage collection and retained objects in a Java implementation?

Inspect heap snapshots and retained paths under load. Static collections can retain objects indefinitely.

**Remember:** Bound caches and remove unnecessary long-lived references.

## 97. Explain JVM benchmarking in Java.

JIT warmup, GC, and optimization affect timing. Use JMH for microbenchmarks and load tests for service outcomes.

**Remember:** Single loops can suffer dead-code elimination and warmup distortion.

## 98. How would you apply JVM benchmarking in a practical Java task?

Use JMH for microbenchmarks and load tests for service outcomes. JIT warmup, GC, and optimization affect timing.

**Remember:** Measure multiple runs and verify the benchmark work remains observable.

## 99. What mistake should you avoid with JVM benchmarking in Java?

Single loops can suffer dead-code elimination and warmup distortion. Use JMH for microbenchmarks and load tests for service outcomes.

**Remember:** JIT warmup, GC, and optimization affect timing.

## 100. How would you verify JVM benchmarking in a Java implementation?

Measure multiple runs and verify the benchmark work remains observable. Single loops can suffer dead-code elimination and warmup distortion.

**Remember:** Use JMH for microbenchmarks and load tests for service outcomes.

## Further reading

- [Java learning documentation](https://dev.java/learn/)


# Python — Interview Questions

100 interview practice questions and concise answers. Product and runtime behavior can vary; check current documentation.

## 1. Explain identity and equality in Python.

is compares identity while == compares values through equality behavior. Use is None for None and == for values.

**Remember:** Small-object caching can make incorrect identity comparisons appear valid.

## 2. How would you apply identity and equality in a practical Python task?

Use is None for None and == for values. is compares identity while == compares values through equality behavior.

**Remember:** Compare aliases and separately allocated equal containers.

## 3. What mistake should you avoid with identity and equality in Python?

Small-object caching can make incorrect identity comparisons appear valid. Use is None for None and == for values.

**Remember:** is compares identity while == compares values through equality behavior.

## 4. How would you verify identity and equality in a Python implementation?

Compare aliases and separately allocated equal containers. Small-object caching can make incorrect identity comparisons appear valid.

**Remember:** Use is None for None and == for values.

## 5. Explain aliasing in Python.

Several names can reference one mutable object. Copy when independent mutation is required.

**Remember:** Assignment alone does not copy an object.

## 6. How would you apply aliasing in a practical Python task?

Copy when independent mutation is required. Several names can reference one mutable object.

**Remember:** Mutate one alias and inspect all references.

## 7. What mistake should you avoid with aliasing in Python?

Assignment alone does not copy an object. Copy when independent mutation is required.

**Remember:** Several names can reference one mutable object.

## 8. How would you verify aliasing in a Python implementation?

Mutate one alias and inspect all references. Assignment alone does not copy an object.

**Remember:** Copy when independent mutation is required.

## 9. Explain shallow and deep copies in Python.

Shallow copies preserve nested references; deep copies recursively copy supported objects. Choose copying based on intended shared structure.

**Remember:** Deepcopy may be expensive or unsuitable for external resources.

## 10. How would you apply shallow and deep copies in a practical Python task?

Choose copying based on intended shared structure. Shallow copies preserve nested references; deep copies recursively copy supported objects.

**Remember:** Test nested mutation and required identity relationships.

## 11. What mistake should you avoid with shallow and deep copies in Python?

Deepcopy may be expensive or unsuitable for external resources. Choose copying based on intended shared structure.

**Remember:** Shallow copies preserve nested references; deep copies recursively copy supported objects.

## 12. How would you verify shallow and deep copies in a Python implementation?

Test nested mutation and required identity relationships. Deepcopy may be expensive or unsuitable for external resources.

**Remember:** Choose copying based on intended shared structure.

## 13. Explain mutable default arguments in Python.

Default expressions run when the function is defined. Use a None sentinel and allocate mutable defaults inside the function.

**Remember:** A default list can retain values across calls.

## 14. How would you apply mutable default arguments in a practical Python task?

Use a None sentinel and allocate mutable defaults inside the function. Default expressions run when the function is defined.

**Remember:** Call repeatedly and check independent returned state.

## 15. What mistake should you avoid with mutable default arguments in Python?

A default list can retain values across calls. Use a None sentinel and allocate mutable defaults inside the function.

**Remember:** Default expressions run when the function is defined.

## 16. How would you verify mutable default arguments in a Python implementation?

Call repeatedly and check independent returned state. A default list can retain values across calls.

**Remember:** Use a None sentinel and allocate mutable defaults inside the function.

## 17. Explain argument passing in Python.

Parameters are names bound to supplied objects. Document whether a function mutates or returns a new value.

**Remember:** Rebinding a parameter does not rebind the caller's name.

## 18. How would you apply argument passing in a practical Python task?

Document whether a function mutates or returns a new value. Parameters are names bound to supplied objects.

**Remember:** Test caller-visible mutation separately from local assignment.

## 19. What mistake should you avoid with argument passing in Python?

Rebinding a parameter does not rebind the caller's name. Document whether a function mutates or returns a new value.

**Remember:** Parameters are names bound to supplied objects.

## 20. How would you verify argument passing in a Python implementation?

Test caller-visible mutation separately from local assignment. Rebinding a parameter does not rebind the caller's name.

**Remember:** Document whether a function mutates or returns a new value.

## 21. Explain LEGB scope in Python.

Lookup generally searches local, enclosing, global, then built-in names. Use nonlocal for an enclosing function binding.

**Remember:** Assignment can make a name local and cause UnboundLocalError.

## 22. How would you apply LEGB scope in a practical Python task?

Use nonlocal for an enclosing function binding. Lookup generally searches local, enclosing, global, then built-in names.

**Remember:** Test nested reads and explicit rebinding.

## 23. What mistake should you avoid with LEGB scope in Python?

Assignment can make a name local and cause UnboundLocalError. Use nonlocal for an enclosing function binding.

**Remember:** Lookup generally searches local, enclosing, global, then built-in names.

## 24. How would you verify LEGB scope in a Python implementation?

Test nested reads and explicit rebinding. Assignment can make a name local and cause UnboundLocalError.

**Remember:** Use nonlocal for an enclosing function binding.

## 25. Explain closure late binding in Python.

Closures look up captured variables when invoked. Bind loop values explicitly for callbacks when needed.

**Remember:** Loop callbacks may all observe the final loop value.

## 26. How would you apply closure late binding in a practical Python task?

Bind loop values explicitly for callbacks when needed. Closures look up captured variables when invoked.

**Remember:** Run callbacks after the loop and check distinct expected results.

## 27. What mistake should you avoid with closure late binding in Python?

Loop callbacks may all observe the final loop value. Bind loop values explicitly for callbacks when needed.

**Remember:** Closures look up captured variables when invoked.

## 28. How would you verify closure late binding in a Python implementation?

Run callbacks after the loop and check distinct expected results. Loop callbacks may all observe the final loop value.

**Remember:** Bind loop values explicitly for callbacks when needed.

## 29. Explain iterator protocol in Python.

Iterables produce iterators; iterators yield successive values. Use iter, next, and normal for loops.

**Remember:** Consumed iterators are not automatically reset.

## 30. How would you apply iterator protocol in a practical Python task?

Use iter, next, and normal for loops. Iterables produce iterators; iterators yield successive values.

**Remember:** Test partial consumption, exhaustion, and fresh iteration.

## 31. What mistake should you avoid with iterator protocol in Python?

Consumed iterators are not automatically reset. Use iter, next, and normal for loops.

**Remember:** Iterables produce iterators; iterators yield successive values.

## 32. How would you verify iterator protocol in a Python implementation?

Test partial consumption, exhaustion, and fresh iteration. Consumed iterators are not automatically reset.

**Remember:** Use iter, next, and normal for loops.

## 33. Explain generators in Python.

Generators yield lazily and preserve execution state. Use them for streaming transformations.

**Remember:** A generator can still retain large referenced objects.

## 34. How would you apply generators in a practical Python task?

Use them for streaming transformations. Generators yield lazily and preserve execution state.

**Remember:** Compare eager outputs and memory on large inputs.

## 35. What mistake should you avoid with generators in Python?

A generator can still retain large referenced objects. Use them for streaming transformations.

**Remember:** Generators yield lazily and preserve execution state.

## 36. How would you verify generators in a Python implementation?

Compare eager outputs and memory on large inputs. A generator can still retain large referenced objects.

**Remember:** Use them for streaming transformations.

## 37. Explain comprehensions in Python.

Comprehensions construct collections with concise transformation and filtering. Choose list comprehensions for eager results and generator expressions for lazy work.

**Remember:** Deeply nested expressions can obscure behavior.

## 38. How would you apply comprehensions in a practical Python task?

Choose list comprehensions for eager results and generator expressions for lazy work. Comprehensions construct collections with concise transformation and filtering.

**Remember:** Test empty input, ordering, and filter boundaries.

## 39. What mistake should you avoid with comprehensions in Python?

Deeply nested expressions can obscure behavior. Choose list comprehensions for eager results and generator expressions for lazy work.

**Remember:** Comprehensions construct collections with concise transformation and filtering.

## 40. How would you verify comprehensions in a Python implementation?

Test empty input, ordering, and filter boundaries. Deeply nested expressions can obscure behavior.

**Remember:** Choose list comprehensions for eager results and generator expressions for lazy work.

## 41. Explain dictionary keys in Python.

Keys must be hashable with consistent equality and hashing. Use tuples of hashable components for composite keys.

**Remember:** A tuple containing a list is unhashable.

## 42. How would you apply dictionary keys in a practical Python task?

Use tuples of hashable components for composite keys. Keys must be hashable with consistent equality and hashing.

**Remember:** Test equal keys, collisions, and unsupported mutable keys.

## 43. What mistake should you avoid with dictionary keys in Python?

A tuple containing a list is unhashable. Use tuples of hashable components for composite keys.

**Remember:** Keys must be hashable with consistent equality and hashing.

## 44. How would you verify dictionary keys in a Python implementation?

Test equal keys, collisions, and unsupported mutable keys. A tuple containing a list is unhashable.

**Remember:** Use tuples of hashable components for composite keys.

## 45. Explain sets in Python.

Sets store unique hashable elements and support set operations. Use membership and set algebra when output order is not required.

**Remember:** Do not rely on stable set iteration order.

## 46. How would you apply sets in a practical Python task?

Use membership and set algebra when output order is not required. Sets store unique hashable elements and support set operations.

**Remember:** Test duplicates, empty sets, unions, and intersections.

## 47. What mistake should you avoid with sets in Python?

Do not rely on stable set iteration order. Use membership and set algebra when output order is not required.

**Remember:** Sets store unique hashable elements and support set operations.

## 48. How would you verify sets in a Python implementation?

Test duplicates, empty sets, unions, and intersections. Do not rely on stable set iteration order.

**Remember:** Use membership and set algebra when output order is not required.

## 49. Explain decorators in Python.

Decorators transform functions or classes at definition time. Use functools.wraps in wrappers to preserve useful metadata.

**Remember:** Wrappers can change argument handling or swallow errors.

## 50. How would you apply decorators in a practical Python task?

Use functools.wraps in wrappers to preserve useful metadata. Decorators transform functions or classes at definition time.

**Remember:** Test return values, exceptions, metadata, and calling behavior.

## 51. What mistake should you avoid with decorators in Python?

Wrappers can change argument handling or swallow errors. Use functools.wraps in wrappers to preserve useful metadata.

**Remember:** Decorators transform functions or classes at definition time.

## 52. How would you verify decorators in a Python implementation?

Test return values, exceptions, metadata, and calling behavior. Wrappers can change argument handling or swallow errors.

**Remember:** Use functools.wraps in wrappers to preserve useful metadata.

## 53. Explain context managers in Python.

Context managers define setup and exit handling for with blocks. Use them for resource ownership and cleanup.

**Remember:** Returning true from __exit__ suppresses an exception.

## 54. How would you apply context managers in a practical Python task?

Use them for resource ownership and cleanup. Context managers define setup and exit handling for with blocks.

**Remember:** Test normal and exceptional exits and intended propagation.

## 55. What mistake should you avoid with context managers in Python?

Returning true from __exit__ suppresses an exception. Use them for resource ownership and cleanup.

**Remember:** Context managers define setup and exit handling for with blocks.

## 56. How would you verify context managers in a Python implementation?

Test normal and exceptional exits and intended propagation. Returning true from __exit__ suppresses an exception.

**Remember:** Use them for resource ownership and cleanup.

## 57. Explain exception handling in Python.

Exceptions propagate until a matching handler catches them. Catch specific expected errors and preserve cleanup guarantees.

**Remember:** Bare except can hide interrupts and unrelated failures.

## 58. How would you apply exception handling in a practical Python task?

Catch specific expected errors and preserve cleanup guarantees. Exceptions propagate until a matching handler catches them.

**Remember:** Test expected errors, unexpected propagation, and cleanup.

## 59. What mistake should you avoid with exception handling in Python?

Bare except can hide interrupts and unrelated failures. Catch specific expected errors and preserve cleanup guarantees.

**Remember:** Exceptions propagate until a matching handler catches them.

## 60. How would you verify exception handling in a Python implementation?

Test expected errors, unexpected propagation, and cleanup. Bare except can hide interrupts and unrelated failures.

**Remember:** Catch specific expected errors and preserve cleanup guarantees.

## 61. Explain dataclasses in Python.

Dataclasses generate methods from declared fields. Use default_factory for mutable field defaults.

**Remember:** frozen does not deeply freeze contained objects.

## 62. How would you apply dataclasses in a practical Python task?

Use default_factory for mutable field defaults. Dataclasses generate methods from declared fields.

**Remember:** Test equality, defaults, and nested mutability.

## 63. What mistake should you avoid with dataclasses in Python?

frozen does not deeply freeze contained objects. Use default_factory for mutable field defaults.

**Remember:** Dataclasses generate methods from declared fields.

## 64. How would you verify dataclasses in a Python implementation?

Test equality, defaults, and nested mutability. frozen does not deeply freeze contained objects.

**Remember:** Use default_factory for mutable field defaults.

## 65. Explain type annotations in Python.

Hints support static checking but generally do not enforce runtime types. Run a type checker and validate external inputs.

**Remember:** An annotated integer argument can still receive a string.

## 66. How would you apply type annotations in a practical Python task?

Run a type checker and validate external inputs. Hints support static checking but generally do not enforce runtime types.

**Remember:** Combine static analysis with boundary validation tests.

## 67. What mistake should you avoid with type annotations in Python?

An annotated integer argument can still receive a string. Run a type checker and validate external inputs.

**Remember:** Hints support static checking but generally do not enforce runtime types.

## 68. How would you verify type annotations in a Python implementation?

Combine static analysis with boundary validation tests. An annotated integer argument can still receive a string.

**Remember:** Run a type checker and validate external inputs.

## 69. Explain method binding in Python.

Instance methods receive self; classmethods receive cls; staticmethods receive neither automatically. Use classmethods for subclass-aware alternate constructors.

**Remember:** A function's calling pattern alone does not declare its binding type.

## 70. How would you apply method binding in a practical Python task?

Use classmethods for subclass-aware alternate constructors. Instance methods receive self; classmethods receive cls; staticmethods receive neither automatically.

**Remember:** Test access through classes, instances, and subclasses.

## 71. What mistake should you avoid with method binding in Python?

A function's calling pattern alone does not declare its binding type. Use classmethods for subclass-aware alternate constructors.

**Remember:** Instance methods receive self; classmethods receive cls; staticmethods receive neither automatically.

## 72. How would you verify method binding in a Python implementation?

Test access through classes, instances, and subclasses. A function's calling pattern alone does not declare its binding type.

**Remember:** Use classmethods for subclass-aware alternate constructors.

## 73. Explain method resolution order in Python.

MRO determines attribute lookup under inheritance. Use cooperative super calls with compatible signatures.

**Remember:** Direct parent calls can break diamond inheritance cooperation.

## 74. How would you apply method resolution order in a practical Python task?

Use cooperative super calls with compatible signatures. MRO determines attribute lookup under inheritance.

**Remember:** Inspect __mro__ and test each intended operation once.

## 75. What mistake should you avoid with method resolution order in Python?

Direct parent calls can break diamond inheritance cooperation. Use cooperative super calls with compatible signatures.

**Remember:** MRO determines attribute lookup under inheritance.

## 76. How would you verify method resolution order in a Python implementation?

Inspect __mro__ and test each intended operation once. Direct parent calls can break diamond inheritance cooperation.

**Remember:** Use cooperative super calls with compatible signatures.

## 77. Explain asyncio in Python.

asyncio schedules cooperative tasks around await points. Use asynchronous I/O and bounded concurrency.

**Remember:** Blocking synchronous work stalls the event loop.

## 78. How would you apply asyncio in a practical Python task?

Use asynchronous I/O and bounded concurrency. asyncio schedules cooperative tasks around await points.

**Remember:** Test cancellation, deadlines, and responsiveness.

## 79. What mistake should you avoid with asyncio in Python?

Blocking synchronous work stalls the event loop. Use asynchronous I/O and bounded concurrency.

**Remember:** asyncio schedules cooperative tasks around await points.

## 80. How would you verify asyncio in a Python implementation?

Test cancellation, deadlines, and responsiveness. Blocking synchronous work stalls the event loop.

**Remember:** Use asynchronous I/O and bounded concurrency.

## 81. Explain GIL and threading in Python.

Thread execution behavior depends on implementation and build; typical GIL-enabled CPython restricts simultaneous Python bytecode execution. Use threads for suitable I/O and evaluate processes for CPU-heavy work.

**Remember:** Do not assume all Python builds share identical GIL behavior or that compound updates are safe.

## 82. How would you apply GIL and threading in a practical Python task?

Use threads for suitable I/O and evaluate processes for CPU-heavy work. Thread execution behavior depends on implementation and build; typical GIL-enabled CPython restricts simultaneous Python bytecode execution.

**Remember:** Benchmark the actual runtime and test synchronization explicitly.

## 83. What mistake should you avoid with GIL and threading in Python?

Do not assume all Python builds share identical GIL behavior or that compound updates are safe. Use threads for suitable I/O and evaluate processes for CPU-heavy work.

**Remember:** Thread execution behavior depends on implementation and build; typical GIL-enabled CPython restricts simultaneous Python bytecode execution.

## 84. How would you verify GIL and threading in a Python implementation?

Benchmark the actual runtime and test synchronization explicitly. Do not assume all Python builds share identical GIL behavior or that compound updates are safe.

**Remember:** Use threads for suitable I/O and evaluate processes for CPU-heavy work.

## 85. Explain multiprocessing in Python.

Processes have separate memory and communicate through explicit mechanisms. Use import-safe entry points and portable serializable inputs.

**Remember:** Transferring large objects can dominate computation cost.

## 86. How would you apply multiprocessing in a practical Python task?

Use import-safe entry points and portable serializable inputs. Processes have separate memory and communicate through explicit mechanisms.

**Remember:** Test startup, failure propagation, shutdown, and serialization overhead.

## 87. What mistake should you avoid with multiprocessing in Python?

Transferring large objects can dominate computation cost. Use import-safe entry points and portable serializable inputs.

**Remember:** Processes have separate memory and communicate through explicit mechanisms.

## 88. How would you verify multiprocessing in a Python implementation?

Test startup, failure propagation, shutdown, and serialization overhead. Transferring large objects can dominate computation cost.

**Remember:** Use import-safe entry points and portable serializable inputs.

## 89. Explain virtual environments in Python.

Virtual environments isolate project package installations. Record dependencies and verify interpreter paths.

**Remember:** Running a different interpreter's pip creates confusing installations.

## 90. How would you apply virtual environments in a practical Python task?

Record dependencies and verify interpreter paths. Virtual environments isolate project package installations.

**Remember:** Recreate the project in a clean environment.

## 91. What mistake should you avoid with virtual environments in Python?

Running a different interpreter's pip creates confusing installations. Record dependencies and verify interpreter paths.

**Remember:** Virtual environments isolate project package installations.

## 92. How would you verify virtual environments in a Python implementation?

Recreate the project in a clean environment. Running a different interpreter's pip creates confusing installations.

**Remember:** Record dependencies and verify interpreter paths.

## 93. Explain safe serialization in Python.

Formats differ in security and type support. Use validated JSON for simple untrusted data and only trusted pickle inputs.

**Remember:** Malicious pickle data can execute code during loading.

## 94. How would you apply safe serialization in a practical Python task?

Use validated JSON for simple untrusted data and only trusted pickle inputs. Formats differ in security and type support.

**Remember:** Test malformed inputs, size limits, and rejection of unsafe formats.

## 95. What mistake should you avoid with safe serialization in Python?

Malicious pickle data can execute code during loading. Use validated JSON for simple untrusted data and only trusted pickle inputs.

**Remember:** Formats differ in security and type support.

## 96. How would you verify safe serialization in a Python implementation?

Test malformed inputs, size limits, and rejection of unsafe formats. Malicious pickle data can execute code during loading.

**Remember:** Use validated JSON for simple untrusted data and only trusted pickle inputs.

## 97. Explain testing and profiling in Python.

Tests establish behavior while profiling finds bottlenecks. Use focused tests and profile measured slow paths.

**Remember:** Optimizing guessed hotspots may add complexity without benefit.

## 98. How would you apply testing and profiling in a practical Python task?

Use focused tests and profile measured slow paths. Tests establish behavior while profiling finds bottlenecks.

**Remember:** Check boundaries and compare representative before-after performance.

## 99. What mistake should you avoid with testing and profiling in Python?

Optimizing guessed hotspots may add complexity without benefit. Use focused tests and profile measured slow paths.

**Remember:** Tests establish behavior while profiling finds bottlenecks.

## 100. How would you verify testing and profiling in a Python implementation?

Check boundaries and compare representative before-after performance. Optimizing guessed hotspots may add complexity without benefit.

**Remember:** Use focused tests and profile measured slow paths.

## Further reading

- [Python tutorial](https://docs.python.org/3/tutorial/)


# R — Interview Questions

100 interview practice questions and concise answers. Product and runtime behavior can vary; check current documentation.

## 1. Explain atomic vectors in R.

Atomic vectors have one underlying type, with coercion for mixed values. Use c() and inspect typeof when type matters.

**Remember:** Combining numbers and text can produce a character vector.

## 2. How would you apply atomic vectors in a practical R task?

Use c() and inspect typeof when type matters. Atomic vectors have one underlying type, with coercion for mixed values.

**Remember:** Test typeof, length, and coerced values.

## 3. What mistake should you avoid with atomic vectors in R?

Combining numbers and text can produce a character vector. Use c() and inspect typeof when type matters.

**Remember:** Atomic vectors have one underlying type, with coercion for mixed values.

## 4. How would you verify atomic vectors in a R implementation?

Test typeof, length, and coerced values. Combining numbers and text can produce a character vector.

**Remember:** Use c() and inspect typeof when type matters.

## 5. Explain lists and data frames in R.

Lists hold heterogeneous objects; data frames organize equal-length columns. Use lists for mixed objects and data frames for observations.

**Remember:** Data-frame columns can themselves be lists.

## 6. How would you apply lists and data frames in a practical R task?

Use lists for mixed objects and data frames for observations. Lists hold heterogeneous objects; data frames organize equal-length columns.

**Remember:** Inspect str(), column types, and lengths.

## 7. What mistake should you avoid with lists and data frames in R?

Data-frame columns can themselves be lists. Use lists for mixed objects and data frames for observations.

**Remember:** Lists hold heterogeneous objects; data frames organize equal-length columns.

## 8. How would you verify lists and data frames in a R implementation?

Inspect str(), column types, and lengths. Data-frame columns can themselves be lists.

**Remember:** Use lists for mixed objects and data frames for observations.

## 9. Explain vector recycling in R.

Shorter vectors may be recycled in elementwise operations. Use matching lengths or justified scalar operations.

**Remember:** Recycling can silently misalign values when lengths divide evenly.

## 10. How would you apply vector recycling in a practical R task?

Use matching lengths or justified scalar operations. Shorter vectors may be recycled in elementwise operations.

**Remember:** Check operand lengths and expected elementwise results.

## 11. What mistake should you avoid with vector recycling in R?

Recycling can silently misalign values when lengths divide evenly. Use matching lengths or justified scalar operations.

**Remember:** Shorter vectors may be recycled in elementwise operations.

## 12. How would you verify vector recycling in a R implementation?

Check operand lengths and expected elementwise results. Recycling can silently misalign values when lengths divide evenly.

**Remember:** Use matching lengths or justified scalar operations.

## 13. Explain NA and NaN in R.

NA marks missingness; NaN marks undefined numeric results and is also missing to is.na. Use is.na and is.nan for their distinct checks.

**Remember:** Comparing x == NA does not identify missing values.

## 14. How would you apply NA and NaN in a practical R task?

Use is.na and is.nan for their distinct checks. NA marks missingness; NaN marks undefined numeric results and is also missing to is.na.

**Remember:** Test NA, NaN, Inf, and ordinary values.

## 15. What mistake should you avoid with NA and NaN in R?

Comparing x == NA does not identify missing values. Use is.na and is.nan for their distinct checks.

**Remember:** NA marks missingness; NaN marks undefined numeric results and is also missing to is.na.

## 16. How would you verify NA and NaN in a R implementation?

Test NA, NaN, Inf, and ordinary values. Comparing x == NA does not identify missing values.

**Remember:** Use is.na and is.nan for their distinct checks.

## 17. Explain NULL in R.

NULL represents absence and differs from a missing vector element. Use it for absent optional objects according to the API.

**Remember:** Assigning NULL to a list component can remove it.

## 18. How would you apply NULL in a practical R task?

Use it for absent optional objects according to the API. NULL represents absence and differs from a missing vector element.

**Remember:** Verify names, length, and presence after assignment.

## 19. What mistake should you avoid with NULL in R?

Assigning NULL to a list component can remove it. Use it for absent optional objects according to the API.

**Remember:** NULL represents absence and differs from a missing vector element.

## 20. How would you verify NULL in a R implementation?

Verify names, length, and presence after assignment. Assigning NULL to a list component can remove it.

**Remember:** Use it for absent optional objects according to the API.

## 21. Explain indexing rules in R.

R commonly uses one-based positive, negative, logical, or named indices. Use explicit masks aligned to the input.

**Remember:** Mixing positive and negative indices, apart from zero, is invalid.

## 22. How would you apply indexing rules in a practical R task?

Use explicit masks aligned to the input. R commonly uses one-based positive, negative, logical, or named indices.

**Remember:** Test zero, boundaries, missing masks, and out-of-range positions.

## 23. What mistake should you avoid with indexing rules in R?

Mixing positive and negative indices, apart from zero, is invalid. Use explicit masks aligned to the input.

**Remember:** R commonly uses one-based positive, negative, logical, or named indices.

## 24. How would you verify indexing rules in a R implementation?

Test zero, boundaries, missing masks, and out-of-range positions. Mixing positive and negative indices, apart from zero, is invalid.

**Remember:** Use explicit masks aligned to the input.

## 25. Explain bracket extraction in R.

For lists, [ returns a sublist and [[ extracts one element. Choose extraction based on required result structure.

**Remember:** Confusing the two changes downstream object types.

## 26. How would you apply bracket extraction in a practical R task?

Choose extraction based on required result structure. For lists, [ returns a sublist and [[ extracts one element.

**Remember:** Compare class and str() after each operation.

## 27. What mistake should you avoid with bracket extraction in R?

Confusing the two changes downstream object types. Choose extraction based on required result structure.

**Remember:** For lists, [ returns a sublist and [[ extracts one element.

## 28. How would you verify bracket extraction in a R implementation?

Compare class and str() after each operation. Confusing the two changes downstream object types.

**Remember:** Choose extraction based on required result structure.

## 29. Explain factors in R.

Factors represent categories through levels and integer codes. Set reference and ordered levels intentionally.

**Remember:** as.numeric on a factor returns codes rather than numeric labels.

## 30. How would you apply factors in a practical R task?

Set reference and ordered levels intentionally. Factors represent categories through levels and integer codes.

**Remember:** Test levels and convert through character when appropriate.

## 31. What mistake should you avoid with factors in R?

as.numeric on a factor returns codes rather than numeric labels. Set reference and ordered levels intentionally.

**Remember:** Factors represent categories through levels and integer codes.

## 32. How would you verify factors in a R implementation?

Test levels and convert through character when appropriate. as.numeric on a factor returns codes rather than numeric labels.

**Remember:** Set reference and ordered levels intentionally.

## 33. Explain matrix coercion in R.

Matrices generally share one atomic type; data frames preserve column types. Use matrices for homogeneous numerical work.

**Remember:** A mixed data frame converted to a matrix may become character data.

## 34. How would you apply matrix coercion in a practical R task?

Use matrices for homogeneous numerical work. Matrices generally share one atomic type; data frames preserve column types.

**Remember:** Check types before conversion and subsequent arithmetic.

## 35. What mistake should you avoid with matrix coercion in R?

A mixed data frame converted to a matrix may become character data. Use matrices for homogeneous numerical work.

**Remember:** Matrices generally share one atomic type; data frames preserve column types.

## 36. How would you verify matrix coercion in a R implementation?

Check types before conversion and subsequent arithmetic. A mixed data frame converted to a matrix may become character data.

**Remember:** Use matrices for homogeneous numerical work.

## 37. Explain dimension dropping in R.

Selecting a single matrix row or column can simplify the result. Use drop = FALSE when dimensions must remain.

**Remember:** Unexpected simplification can break generic matrix code.

## 38. How would you apply dimension dropping in a practical R task?

Use drop = FALSE when dimensions must remain. Selecting a single matrix row or column can simplify the result.

**Remember:** Test one-row, one-column, empty, and larger subsets.

## 39. What mistake should you avoid with dimension dropping in R?

Unexpected simplification can break generic matrix code. Use drop = FALSE when dimensions must remain.

**Remember:** Selecting a single matrix row or column can simplify the result.

## 40. How would you verify dimension dropping in a R implementation?

Test one-row, one-column, empty, and larger subsets. Unexpected simplification can break generic matrix code.

**Remember:** Use drop = FALSE when dimensions must remain.

## 41. Explain function environments in R.

Functions resolve names through associated environments. Pass important inputs explicitly and use lexical scope deliberately.

**Remember:** External mutable bindings can become hidden dependencies.

## 42. How would you apply function environments in a practical R task?

Pass important inputs explicitly and use lexical scope deliberately. Functions resolve names through associated environments.

**Remember:** Test with changed enclosing values and isolated environments.

## 43. What mistake should you avoid with function environments in R?

External mutable bindings can become hidden dependencies. Pass important inputs explicitly and use lexical scope deliberately.

**Remember:** Functions resolve names through associated environments.

## 44. How would you verify function environments in a R implementation?

Test with changed enclosing values and isolated environments. External mutable bindings can become hidden dependencies.

**Remember:** Pass important inputs explicitly and use lexical scope deliberately.

## 45. Explain lazy arguments in R.

Arguments are promises evaluated when needed. Avoid side effects whose timing depends on evaluation order.

**Remember:** Unused arguments may never execute.

## 46. How would you apply lazy arguments in a practical R task?

Avoid side effects whose timing depends on evaluation order. Arguments are promises evaluated when needed.

**Remember:** Instrument small functions to observe when arguments are forced.

## 47. What mistake should you avoid with lazy arguments in R?

Unused arguments may never execute. Avoid side effects whose timing depends on evaluation order.

**Remember:** Arguments are promises evaluated when needed.

## 48. How would you verify lazy arguments in a R implementation?

Instrument small functions to observe when arguments are forced. Unused arguments may never execute.

**Remember:** Avoid side effects whose timing depends on evaluation order.

## 49. Explain copy-on-modify in R.

R generally offers value-like behavior with copying when modification requires it. Write clear code and profile actual allocation.

**Remember:** Reference-like objects and package-specific operations can differ.

## 50. How would you apply copy-on-modify in a practical R task?

Write clear code and profile actual allocation. R generally offers value-like behavior with copying when modification requires it.

**Remember:** Test alias behavior and inspect memory with appropriate tools.

## 51. What mistake should you avoid with copy-on-modify in R?

Reference-like objects and package-specific operations can differ. Write clear code and profile actual allocation.

**Remember:** R generally offers value-like behavior with copying when modification requires it.

## 52. How would you verify copy-on-modify in a R implementation?

Test alias behavior and inspect memory with appropriate tools. Reference-like objects and package-specific operations can differ.

**Remember:** Write clear code and profile actual allocation.

## 53. Explain apply-family functions in R.

lapply returns lists; vapply checks a specified result shape and type. Use vapply when stable output types matter.

**Remember:** sapply simplification can vary with returned values.

## 54. How would you apply apply-family functions in a practical R task?

Use vapply when stable output types matter. lapply returns lists; vapply checks a specified result shape and type.

**Remember:** Test empty inputs and mismatched result lengths or types.

## 55. What mistake should you avoid with apply-family functions in R?

sapply simplification can vary with returned values. Use vapply when stable output types matter.

**Remember:** lapply returns lists; vapply checks a specified result shape and type.

## 56. How would you verify apply-family functions in a R implementation?

Test empty inputs and mismatched result lengths or types. sapply simplification can vary with returned values.

**Remember:** Use vapply when stable output types matter.

## 57. Explain vectorization in R.

Vectorized operations express work over collections. Use sum, rowSums, and direct arithmetic when clear.

**Remember:** Large intermediate allocations can offset speed gains.

## 58. How would you apply vectorization in a practical R task?

Use sum, rowSums, and direct arithmetic when clear. Vectorized operations express work over collections.

**Remember:** Benchmark runtime and memory with representative sizes.

## 59. What mistake should you avoid with vectorization in R?

Large intermediate allocations can offset speed gains. Use sum, rowSums, and direct arithmetic when clear.

**Remember:** Vectorized operations express work over collections.

## 60. How would you verify vectorization in a R implementation?

Benchmark runtime and memory with representative sizes. Large intermediate allocations can offset speed gains.

**Remember:** Use sum, rowSums, and direct arithmetic when clear.

## 61. Explain joins in R.

Joins combine rows according to keys and inclusion rules. Verify key uniqueness and intended join direction.

**Remember:** Duplicate keys can multiply rows and inflate totals.

## 62. How would you apply joins in a practical R task?

Verify key uniqueness and intended join direction. Joins combine rows according to keys and inclusion rules.

**Remember:** Test missing keys, duplicates, and expected counts.

## 63. What mistake should you avoid with joins in R?

Duplicate keys can multiply rows and inflate totals. Verify key uniqueness and intended join direction.

**Remember:** Joins combine rows according to keys and inclusion rules.

## 64. How would you verify joins in a R implementation?

Test missing keys, duplicates, and expected counts. Duplicate keys can multiply rows and inflate totals.

**Remember:** Verify key uniqueness and intended join direction.

## 65. Explain aggregation in R.

Aggregation summarizes observations by groups. Define grouping and missing-value behavior explicitly.

**Remember:** Group averages without sizes can be misleading.

## 66. How would you apply aggregation in a practical R task?

Define grouping and missing-value behavior explicitly. Aggregation summarizes observations by groups.

**Remember:** Compare counts and totals against manually verified samples.

## 67. What mistake should you avoid with aggregation in R?

Group averages without sizes can be misleading. Define grouping and missing-value behavior explicitly.

**Remember:** Aggregation summarizes observations by groups.

## 68. How would you verify aggregation in a R implementation?

Compare counts and totals against manually verified samples. Group averages without sizes can be misleading.

**Remember:** Define grouping and missing-value behavior explicitly.

## 69. Explain dates and times in R.

Date represents calendar dates; POSIXct represents instants with time-zone interpretation. Parse explicit formats and time zones.

**Remember:** Daylight-saving ambiguity and locale assumptions can change results.

## 70. How would you apply dates and times in a practical R task?

Parse explicit formats and time zones. Date represents calendar dates; POSIXct represents instants with time-zone interpretation.

**Remember:** Test conversions and daylight-saving boundaries.

## 71. What mistake should you avoid with dates and times in R?

Daylight-saving ambiguity and locale assumptions can change results. Parse explicit formats and time zones.

**Remember:** Date represents calendar dates; POSIXct represents instants with time-zone interpretation.

## 72. How would you verify dates and times in a R implementation?

Test conversions and daylight-saving boundaries. Daylight-saving ambiguity and locale assumptions can change results.

**Remember:** Parse explicit formats and time zones.

## 73. Explain random reproducibility in R.

Random results depend on generator state and execution sequence. Use set.seed and record runtime and package versions.

**Remember:** A seed alone does not guarantee matching parallel streams.

## 74. How would you apply random reproducibility in a practical R task?

Use set.seed and record runtime and package versions. Random results depend on generator state and execution sequence.

**Remember:** Repeat clean runs and verify parallel RNG handling.

## 75. What mistake should you avoid with random reproducibility in R?

A seed alone does not guarantee matching parallel streams. Use set.seed and record runtime and package versions.

**Remember:** Random results depend on generator state and execution sequence.

## 76. How would you verify random reproducibility in a R implementation?

Repeat clean runs and verify parallel RNG handling. A seed alone does not guarantee matching parallel streams.

**Remember:** Use set.seed and record runtime and package versions.

## 77. Explain linear model formulas in R.

Formulas describe responses, predictors, transformations, and interactions. Fit lm with explicit data and inspect the model matrix.

**Remember:** Interactions change main-effect interpretation.

## 78. How would you apply linear model formulas in a practical R task?

Fit lm with explicit data and inspect the model matrix. Formulas describe responses, predictors, transformations, and interactions.

**Remember:** Check residuals, design matrices, and held-out predictions.

## 79. What mistake should you avoid with linear model formulas in R?

Interactions change main-effect interpretation. Fit lm with explicit data and inspect the model matrix.

**Remember:** Formulas describe responses, predictors, transformations, and interactions.

## 80. How would you verify linear model formulas in a R implementation?

Check residuals, design matrices, and held-out predictions. Interactions change main-effect interpretation.

**Remember:** Fit lm with explicit data and inspect the model matrix.

## 81. Explain generalized linear models in R.

GLMs connect response distributions to predictors through a link. Choose a suitable family such as binomial for appropriate binary outcomes.

**Remember:** Link-scale coefficients are not direct probability changes.

## 82. How would you apply generalized linear models in a practical R task?

Choose a suitable family such as binomial for appropriate binary outcomes. GLMs connect response distributions to predictors through a link.

**Remember:** Check outcome coding, convergence, and calibration.

## 83. What mistake should you avoid with generalized linear models in R?

Link-scale coefficients are not direct probability changes. Choose a suitable family such as binomial for appropriate binary outcomes.

**Remember:** GLMs connect response distributions to predictors through a link.

## 84. How would you verify generalized linear models in a R implementation?

Check outcome coding, convergence, and calibration. Link-scale coefficients are not direct probability changes.

**Remember:** Choose a suitable family such as binomial for appropriate binary outcomes.

## 85. Explain missing-data preprocessing in R.

Missingness can alter estimates and model row selection. Inspect patterns and justify imputation or deletion assumptions.

**Remember:** Imputing before data splitting leaks information.

## 86. How would you apply missing-data preprocessing in a practical R task?

Inspect patterns and justify imputation or deletion assumptions. Missingness can alter estimates and model row selection.

**Remember:** Fit preprocessing on training data and test held-out missing cases.

## 87. What mistake should you avoid with missing-data preprocessing in R?

Imputing before data splitting leaks information. Inspect patterns and justify imputation or deletion assumptions.

**Remember:** Missingness can alter estimates and model row selection.

## 88. How would you verify missing-data preprocessing in a R implementation?

Fit preprocessing on training data and test held-out missing cases. Imputing before data splitting leaks information.

**Remember:** Inspect patterns and justify imputation or deletion assumptions.

## 89. Explain inference interpretation in R.

P-values and confidence intervals depend on statistical assumptions. Report effect sizes and uncertainty in design context.

**Remember:** A p-value is not the probability the null hypothesis is true.

## 90. How would you apply inference interpretation in a practical R task?

Report effect sizes and uncertainty in design context. P-values and confidence intervals depend on statistical assumptions.

**Remember:** Check assumptions, multiplicity, and sensitivity.

## 91. What mistake should you avoid with inference interpretation in R?

A p-value is not the probability the null hypothesis is true. Report effect sizes and uncertainty in design context.

**Remember:** P-values and confidence intervals depend on statistical assumptions.

## 92. How would you verify inference interpretation in a R implementation?

Check assumptions, multiplicity, and sensitivity. A p-value is not the probability the null hypothesis is true.

**Remember:** Report effect sizes and uncertainty in design context.

## 93. Explain package reproducibility in R.

Package versions can change analysis behavior. Record dependencies with a suitable environment or lockfile.

**Remember:** Installing current packages may not reproduce an old analysis.

## 94. How would you apply package reproducibility in a practical R task?

Record dependencies with a suitable environment or lockfile. Package versions can change analysis behavior.

**Remember:** Rebuild and run the analysis in a clean environment.

## 95. What mistake should you avoid with package reproducibility in R?

Installing current packages may not reproduce an old analysis. Record dependencies with a suitable environment or lockfile.

**Remember:** Package versions can change analysis behavior.

## 96. How would you verify package reproducibility in a R implementation?

Rebuild and run the analysis in a clean environment. Installing current packages may not reproduce an old analysis.

**Remember:** Record dependencies with a suitable environment or lockfile.

## 97. Explain performance profiling in R.

Repeated allocation and inefficient algorithms can dominate runtime. Profile first and preallocate when justified.

**Remember:** Repeatedly growing a vector can cause excessive copying.

## 98. How would you apply performance profiling in a practical R task?

Profile first and preallocate when justified. Repeated allocation and inefficient algorithms can dominate runtime.

**Remember:** Compare realistic runtime and memory before and after changes.

## 99. What mistake should you avoid with performance profiling in R?

Repeatedly growing a vector can cause excessive copying. Profile first and preallocate when justified.

**Remember:** Repeated allocation and inefficient algorithms can dominate runtime.

## 100. How would you verify performance profiling in a R implementation?

Compare realistic runtime and memory before and after changes. Repeatedly growing a vector can cause excessive copying.

**Remember:** Profile first and preallocate when justified.

## Further reading

- [An Introduction to R](https://stat.ethz.ch/CRAN/doc/manuals/R-intro.html)


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

