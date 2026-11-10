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
