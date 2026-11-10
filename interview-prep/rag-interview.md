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
