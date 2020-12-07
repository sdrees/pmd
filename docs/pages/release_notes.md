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

##### CPD

* The C# module now supports the new option [`--ignore-literal-sequences`](https://pmd.github.io/latest/pmd_userdocs_cpd.html#-ignore-literal-sequences), which can be used to avoid detection of some uninteresting clones. Support for other languages may be added in the future. See [#2945](https://github.com/pmd/pmd/pull/2945)

* The Scala module now supports [suppression](https://pmd.github.io/latest/pmd_userdocs_cpd.html#suppression) through `CPD-ON`/`CPD-OFF` comment pairs. See [#2929](https://github.com/pmd/pmd/pull/2929)

### Fixed Issues

*   core
    * [#1939](https://github.com/pmd/pmd/issues/1939): \[core] XPath expressions return handling
    * [#1961](https://github.com/pmd/pmd/issues/1961): \[core] Text renderer should include name of violated rule
    * [#2874](https://github.com/pmd/pmd/pull/2874): \[core] Fix XMLRenderer with UTF-16
*   cs
    * [#2938](https://github.com/pmd/pmd/pull/2938): \[cs] CPD: ignoring using directives could not be disabled
*   java
    * [#2911](https://github.com/pmd/pmd/issues/2911): \[java] `ClassTypeResolver#searchNodeNameForClass` leaks memory
    * [#2934](https://github.com/pmd/pmd/pull/2934): \[java] CompareObjectsWithEquals / UseEqualsToCompareStrings - False negatives with fields
    * [#2940](https://github.com/pmd/pmd/pull/2940): \[java] Catch additional TypeNotPresentExceptions / LinkageErrors
*   scala
    * [#2480](https://github.com/pmd/pmd/issues/2480): \[scala] Support CPD suppressions


### API Changes

#### Deprecated API

*   {% jdoc !!java::lang.java.ast.ASTPackageDeclaration#getPackageNameImage() %},
    {% jdoc !!java::lang.java.ast.ASTTypeParameter#getParameterName() %}
    and the corresponding XPath attributes. In both cases they're replaced with a new method `getName`,
    the attribute is `@Name`.
*   {% jdoc !!java::lang.java.ast.ASTClassOrInterfaceBody#isAnonymousInnerClass() %},
    and {% jdoc !!java::lang.java.ast.ASTClassOrInterfaceBody#isEnumChild() %},
    refs [#905](https://github.com/pmd/pmd/issues/905)

#### Internal API

Those APIs are not intended to be used by clients, and will be hidden or removed with PMD 7.0.0.
You can identify them with the `@InternalApi` annotation. You'll also get a deprecation warning.

*   {% jdoc !!javascript::lang.ecmascript.Ecmascript3Handler %}
*   {% jdoc !!javascript::lang.ecmascript.Ecmascript3Parser %}
*   {% jdoc !!javascript::lang.ecmascript.ast.EcmascriptParser#parserOptions %}
*   {% jdoc !!javascript::lang.ecmascript.ast.EcmascriptParser#getSuppressMap() %}
*   {% jdoc !!core::lang.rule.ParametricRuleViolation %}
*   {% jdoc !!core::lang.ParserOptions#suppressMarker %}
*   {% jdoc !!modelica::lang.modelica.rule.ModelicaRuleViolationFactory %}


### External Contributions

*   [#2914](https://github.com/pmd/pmd/pull/2914): \[core] Include rule name in text renderer - [Gunther Schrijvers](https://github.com/GuntherSchrijvers)
*   [#2925](https://github.com/pmd/pmd/pull/2925): Cleanup: Correct annotation array initializer indents from checkstyle #8083 - [Abhishek Kumar](https://github.com/Abhishek-kumar09)
*   [#2929](https://github.com/pmd/pmd/pull/2929): \[scala] Add support for CPD-ON and CPD-OFF special comments - [Andy Robinson](https://github.com/andyrobinson)
*   [#2936](https://github.com/pmd/pmd/pull/2936): \[java] (doc) Fix typo: "an accessor" not "a" - [Igor Moreno](https://github.com/igormoreno)
*   [#2938](https://github.com/pmd/pmd/pull/2938): \[cs] CPD: fix issue where ignoring using directives could not be disabled - [Maikel Steneker](https://github.com/maikelsteneker)
*   [#2945](https://github.com/pmd/pmd/pull/2945): \[cs] Add option to ignore sequences of literals - [Maikel Steneker](https://github.com/maikelsteneker)

{% endtocmaker %}
