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
