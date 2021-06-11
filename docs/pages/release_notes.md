---
title: PMD Release Notes
permalink: pmd_release_notes.html
keywords: changelog, release notes
---

## {{ site.pmd.date }} - {{ site.pmd.version }}

The PMD team is pleased to announce PMD {{ site.pmd.version }}.

This is a {{ site.pmd.release_type }} release.

{% tocmaker is_release_notes_processor %}

### New and noteworthy

#### New rules

*   The new Apex rule {% rule "apex/errorprone/InaccessibleAuraEnabledGetter" %} checks that an `AuraEnabled`
    getter is public or global. This is necessary if it is referenced in Lightning components.
    You can try out this rule like so:

```xml
    <rule ref="category/apex/errorprone.xml/InaccessibleAuraEnabledGetter" />
```

### Renamed rules

*   The Java rule {% rule "java/errorprone/BadComparison" %} has been renamed to
    {% rule "java/errorprone/ComparisonWithNaN" %} to better reflect what the rule actually detects.
    It now considers usages of `Double.NaN` or `Float.NaN` in more cases and fixes false negatives.

### Fixed Issues

*   apex-errorprone
    *   [#3321](https://github.com/pmd/pmd/issues/3321): \[apex] New rule to detect inaccessible AuraEnabled getters (summer '21 security update)
*   core
    *   [#3323](https://github.com/pmd/pmd/pull/3323): \[core] Adds fullDescription and tags in SARIF report
*   java-codestyle
    *   [#3317](https://github.com/pmd/pmd/pull/3317): \[java] Update UnnecessaryImport to recognize usage of imported types in javadoc's `@exception` tag
*   java-errorprone
    *   [#2895](https://github.com/pmd/pmd/issues/2895): \[java] Improve BadComparison and rename to ComparisonWithNaN
    *   [#3304](https://github.com/pmd/pmd/issues/3304): \[java] NPE in MoreThanOneLoggerRule on a java 16 record

### API Changes

### External Contributions

*   [#3306](https://github.com/pmd/pmd/pull/3306): \[java] More than one logger rule test null pointer exception - [Arnaud Jeansen](https://github.com/ajeans)
*   [#3317](https://github.com/pmd/pmd/pull/3317): \[java] Update UnnecessaryImport to recognize usage of imported types in javadoc's `@exception` tag - [Piotrek Żygieło](https://github.com/pzygielo)
*   [#3320](https://github.com/pmd/pmd/pull/3320): \[java] Fix incorrect increment for "else if" branch in Cognitive Complexity docs - [Denis Borovikov](https://github.com/borovikovd)
*   [#3322](https://github.com/pmd/pmd/pull/3322): \[apex] added rule to detect inaccessible AuraEnabled getters - [Philippe Ozil](https://github.com/pozil)
*   [#3323](https://github.com/pmd/pmd/pull/3323): \[core] Adds fullDescription and tags in SARIF report - [Clint Chester](https://github.com/Clint-Chester)

{% endtocmaker %}

