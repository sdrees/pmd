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

#### Java 16 Support

This release of PMD brings support for Java 16. PMD supports [JEP 394: Pattern Matching for instanceof](https://openjdk.java.net/jeps/394) and [JEP 395: Records](https://openjdk.java.net/jeps/395). Both have been promoted
to be a standard language feature of Java 16.

PMD also supports [JEP 397: Sealed Classes (Second Preview)](https://openjdk.java.net/jeps/397) as a preview
language feature. In order to analyze a project with PMD that uses these language features, you'll need to enable
it via the environment variable `PMD_JAVA_OPTS` and select the new language version `16-preview`:

    export PMD_JAVA_OPTS=--enable-preview
    ./run.sh pmd -language java -version 16-preview ...

Note: Support for Java 14 preview language features have been removed. The version "14-preview" is no longer available.

#### Modified Rules

*   The Apex rule {% rule "apex/documentation/ApexDoc" %} has two new properties: `reportPrivate` and
    `reportProtected`. Previously the rule only considered public and global classes, methods, and
    properties. With these properties, you can verify the existence of ApexDoc comments for private
    and protected methods as well. By default, these properties are disabled to preserve backwards
    compatible behavior.

### Fixed Issues

*   apex-documentation
    *   [#3075](https://github.com/pmd/pmd/issues/3075): \[apex] ApexDoc should support private access modifier
*   plsql
    *   [#3106](https://github.com/pmd/pmd/issues/3106): \[plsql] ParseException while parsing EXECUTE IMMEDIATE 'drop database link ' \|\| linkname;

### API Changes

#### pmd-java

*   The experimental class `ASTTypeTestPattern` has been renamed to {% jdoc java::lang.java.ast.ASTTypePattern %}
    in order to align the naming to the JLS.
*   The experimental class `ASTRecordConstructorDeclaration` has been renamed to {% jdoc java::lang.java.ast.ASTCompactConstructorDeclaration %}
    in order to align the naming to the JLS.
*   The AST types and APIs around Pattern Matching and Records are not experimental anymore:
    *   {% jdoc !!java::lang.java.ast.ASTVariableDeclaratorId#isPatternBinding() %}
    *   {% jdoc java::lang.java.ast.ASTPattern %}
    *   {% jdoc java::lang.java.ast.ASTTypePattern %}
    *   {% jdoc java::lang.java.ast.ASTRecordDeclaration %}
    *   {% jdoc java::lang.java.ast.ASTRecordComponentList %}
    *   {% jdoc java::lang.java.ast.ASTRecordComponent %}
    *   {% jdoc java::lang.java.ast.ASTRecordBody %}
    *   {% jdoc java::lang.java.ast.ASTCompactConstructorDeclaration %}

### External Contributions

*   [#3098](https://github.com/pmd/pmd/pull/3098): \[apex] ApexDoc optionally report private and protected - [Jonathan Wiesel](https://github.com/jonathanwiesel)
*   [#3107](https://github.com/pmd/pmd/pull/3107): \[plsql] Fix ParseException for EXECUTE IMMEDIATE str1\|\|str2; - [hvbtup](https://github.com/hvbtup)
*   [#3125](https://github.com/pmd/pmd/pull/3125): \[doc] Fix sample code indentation in documentation - [Artur Dryomov](https://github.com/arturdryomov)

{% endtocmaker %}

