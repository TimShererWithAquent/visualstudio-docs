---
title: "CA1007: Use generics where appropriate"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
  - "CA1007"
  - "UseGenericsWhereAppropriate"
helpviewer_keywords:
  - "CA1007"
  - "UseGenericsWhereAppropriate"
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
 - CSharp
 - VB
ms.workload:
  - "multiple"
---
# CA1007: Use generics where appropriate

|||
|-|-|
|TypeName|UseGenericsWhereAppropriate|
|CheckId|CA1007|
|Category|Microsoft.Design|
|Breaking change|Breaking|

## Cause
An externally visible method contains a reference parameter of type <xref:System.Object?displayProperty=fullName>, and the containing assembly targets .NET Framework 2.0.

## Rule description
A reference parameter is a parameter that is modified by using the `ref` (`ByRef` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) keyword. The argument type that is supplied for a reference parameter must exactly match the reference parameter type. To use a type that is derived from the reference parameter type, the type must first be cast and assigned to a variable of the reference parameter type. Use of a generic method allows all types, subject to constraints, to be passed to the method without first casting the type to the reference parameter type.

## How to fix violations
To fix a violation of this rule, make the method generic and replace the <xref:System.Object> parameter by using a type parameter.

## When to suppress warnings
Do not suppress a warning from this rule.

## Example
The following example shows a general-purpose swap routine that is implemented as both nongeneric and generic methods. Note how efficiently the strings are swapped by using the generic method compared to the nongeneric method.

[!code-vb[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/VisualBasic/ca1007-use-generics-where-appropriate_1.vb)]
[!code-csharp[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/CSharp/ca1007-use-generics-where-appropriate_1.cs)]

## Related rules
[CA1005: Avoid excessive parameters on generic types](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

[CA1010: Collections should implement generic interface](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000: Do not declare static members on generic types](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1002: Do not expose generic lists](../code-quality/ca1002-do-not-expose-generic-lists.md)

[CA1006: Do not nest generic types in member signatures](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

[CA1004: Generic methods should provide type parameter](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

[CA1003: Use generic event handler instances](../code-quality/ca1003-use-generic-event-handler-instances.md)

## See also
[Generics](/dotnet/csharp/programming-guide/generics/index)