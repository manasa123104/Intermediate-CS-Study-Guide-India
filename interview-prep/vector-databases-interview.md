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
