---
title: "CA1043: Use integral or string argument for indexers"
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
  - "CA1043"
  - "UseIntegralOrStringArgumentForIndexers"
helpviewer_keywords:
  - "CA1043"
  - "UseIntegralOrStringArgumentForIndexers"
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
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
# CA1043: Use integral or string argument for indexers

|||
|-|-|
|TypeName|UseIntegralOrStringArgumentForIndexers|
|CheckId|CA1043|
|Category|Microsoft.Design|
|Breaking change|Breaking|

## Cause

A type contains an indexer that uses an index type other than <xref:System.Int32?displayProperty=fullName>, <xref:System.Int64?displayProperty=fullName>, <xref:System.Object?displayProperty=fullName>, or <xref:System.String?displayProperty=fullName>.

By default, this rule only looks at public and protected types, but this is [configurable](#configurability).

## Rule description

Indexers, that is, indexed properties, should use integer or string types for the index. These types are typically used for indexing data structures and increase the usability of the library. Use of the <xref:System.Object> type should be restricted to those cases where the specific integer or string type cannot be specified at design time. If the design requires other types for the index, reconsider whether the type represents a logical data store. If it does not represent a logical data store, use a method.

## How to fix violations

To fix a violation of this rule, change the index to an integer or string type or use a method instead of the indexer.

## When to suppress warnings

Suppress a warning from this rule only after carefully considering the need for the nonstandard indexer.

## Configurability

If you're running this rule from [FxCop analyzers](install-fxcop-analyzers.md) (and not with legacy analysis), you can configure which parts of your codebase to run this rule on, based on their accessibility. For example, to specify that the rule should run only against the non-public API surface, add the following key-value pair to an .editorconfig file in your project:

```ini
dotnet_code_quality.ca1043.api_surface = private, internal
```

You can configure this option for just this rule, for all rules, or for all rules in this category (Design). For more information, see [Configure FxCop analyzers](configure-fxcop-analyzers.md).

## Example

The following example shows an indexer that uses an <xref:System.Int32> index.

[!code-csharp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CSharp/ca1043-use-integral-or-string-argument-for-indexers_1.cs)]
[!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CPP/ca1043-use-integral-or-string-argument-for-indexers_1.cpp)]
[!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/VisualBasic/ca1043-use-integral-or-string-argument-for-indexers_1.vb)]

## Related rules

- [CA1023: Indexers should not be multidimensional](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)
- [CA1024: Use properties where appropriate](../code-quality/ca1024-use-properties-where-appropriate.md)