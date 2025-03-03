---
title: "CA1813: Avoid unsealed attributes"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
  - "CA1813"
  - "AvoidUnsealedAttributes"
helpviewer_keywords:
  - "CA1813"
  - "AvoidUnsealedAttributes"
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
 - CSharp
 - VB
ms.workload:
  - "multiple"
---
# CA1813: Avoid unsealed attributes

|||
|-|-|
|TypeName|AvoidUnsealedAttributes|
|CheckId|CA1813|
|Category|Microsoft.Performance|
|Breaking change|Breaking|

## Cause

A public type inherits from <xref:System.Attribute?displayProperty=fullName>, is not abstract, and is not sealed (`NotInheritable` in Visual Basic).

## Rule description

.NET provides methods for retrieving custom attributes. By default, these methods search the attribute inheritance hierarchy. For example, <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> searches for the specified attribute type or any attribute type that extends the specified attribute type. Sealing the attribute eliminates the search through the inheritance hierarchy, and can improve performance.

## How to fix violations

To fix a violation of this rule, seal the attribute type or make it abstract.

## When to suppress warnings

It is safe to suppress a warning from this rule. Suppress only if you are defining an attribute hierarchy and cannot seal the attribute or make it abstract.

## Example

The following example shows a custom attribute that satisfies this rule.

[!code-csharp[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/CSharp/ca1813-avoid-unsealed-attributes_1.cs)]
[!code-vb[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/VisualBasic/ca1813-avoid-unsealed-attributes_1.vb)]

## Related rules

- [CA1019: Define accessors for attribute arguments](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)
- [CA1018: Mark attributes with AttributeUsageAttribute](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)

## See also

- [Attributes](/dotnet/standard/design-guidelines/attributes)