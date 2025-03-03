---
title: "CA1715: Identifiers should have correct prefix"
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
  - "CA1715"
  - "IdentifiersShouldHaveCorrectPrefix"
helpviewer_keywords:
  - "IdentifiersShouldHaveCorrectPrefix"
  - "CA1715"
ms.assetid: cf45f8df-6855-4cb6-a4e2-7cfed714cf2f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
 - CPP
 - CSharp
 - VB
ms.workload:
  - "multiple"
---
# CA1715: Identifiers should have correct prefix

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectPrefix|
|CheckId|CA1715|
|Category|Microsoft.Naming|
|Breaking change|Breaking - when fired on interfaces.<br /><br /> Non-breaking - when raised on generic type parameters.|

## Cause

The name of an interface does not start with an uppercase 'I'.

-or-

The name of a [generic type parameter](/dotnet/csharp/programming-guide/generics/generic-type-parameters) on a type or method does not start with an uppercase 'T'.

By default, this rule only looks at externally visible interfaces, types, and methods, but this is [configurable](#configurability).

## Rule description

By convention, the names of certain programming elements start with a specific prefix.

Interface names should start with an uppercase 'I' followed by another uppercase letter. This rule reports violations for interface names such as 'MyInterface' and 'IsolatedInterface'.

Generic type parameter names should start with an uppercase 'T' and optionally may be followed by another uppercase letter. This rule reports violations for generic type parameter names such as 'V' and 'Type'.

Naming conventions provide a common look for libraries that target the common language runtime. This reduces the learning curve that is required for new software libraries, and increases customer confidence that the library was developed by someone who has expertise in developing managed code.

## Configurability

If you're running this rule from [FxCop analyzers](install-fxcop-analyzers.md) (and not with legacy analysis), you can configure which parts of your code this rule analyzes. For more information, see [Configure FxCop analyzers](configure-fxcop-analyzers.md).

### Single-character type parameters

You can configure whether or not to exclude single-character type parameters from this rule. For example, to specify that this rule *should not* analyze single-character type parameters, add one of the following key-value pairs to an .editorconfig file in your project:

```ini
# Package version 2.9.0 and later
dotnet_code_quality.CA1715.exclude_single_letter_type_parameters = true

# Package version 2.6.3 and earlier
dotnet_code_quality.CA2007.allow_single_letter_type_parameters = true
```

> [!NOTE]
> This rule never fires for a type parameter named `T`, for example, `Collection<T>`.

### API surface

You can configure which parts of your codebase to run this rule on, based on their accessibility. For example, to specify that the rule should run only against the non-public API surface, add the following key-value pair to an .editorconfig file in your project:

```ini
dotnet_code_quality.ca1715.api_surface = private, internal
```

You can configure this option for just this rule, for all rules, or for all rules in this category (Naming).

## How to fix violations

Rename the identifier so that it is correctly prefixed.

## When to suppress warnings

Do not suppress a warning from this rule.

## Interface naming example

The following code snippet shows an incorrectly named interface:

[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_1.cpp)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_1.vb)]
[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_1.cs)]

The following code snippet fixes the previous violation by prefixing the interface with 'I':

[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_2.cs)]
[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_2.cpp)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_2.vb)]

## Type parameter naming example

The following code snippet shows an incorrectly named generic type parameter:

[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_3.cpp)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_3.vb)]
[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_3.cs)]

The following code snippet fixes the previous violation by prefixing the generic type parameter with 'T':

[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_4.cpp)]
[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_4.cs)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_4.vb)]

## Related rules

- [CA1722: Identifiers should not have incorrect prefix](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)