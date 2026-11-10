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
