---
title: "CA1804: Remove unused locals"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
  - "CA1804"
  - "RemoveUnusedLocals"
helpviewer_keywords:
  - "RemoveUnusedLocals"
  - "CA1804"
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
 - CSharp
 - VB
ms.workload:
  - "multiple"
---
# CA1804: Remove unused locals

|||
|-|-|
|TypeName|RemoveUnusedLocals|
|CheckId|CA1804|
|Category|Microsoft.Performance|
|Breaking change|Non-breaking|

## Cause
A method declares a local variable but does not use the variable except possibly as the recipient of an assignment statement. For analysis by this rule, the tested assembly must be built with debugging information and the associated program database (.pdb) file must be available.

## Rule description
Unused local variables and unnecessary assignments increase the size of an assembly and decrease performance.

## How to fix violations

To fix a violation of this rule, remove or use the local variable.

> [!NOTE]
> The C# compiler removes unused local variables when the `optimize` option is enabled.

## When to suppress warnings
Suppress a warning from this rule if the variable was compiler emitted. It is also safe to suppress a warning from this rule, or to disable the rule, if performance and code maintenance are not primary concerns.

## Example
The following example shows several unused local variables.

[!code-vb[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/VisualBasic/ca1804-remove-unused-locals_1.vb)]
[!code-csharp[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/CSharp/ca1804-remove-unused-locals_1.cs)]

## Related rules
[CA1809: Avoid excessive locals](../code-quality/ca1809-avoid-excessive-locals.md)

[CA1811: Avoid uncalled private code](../code-quality/ca1811-avoid-uncalled-private-code.md)

[CA1812: Avoid uninstantiated internal classes](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1801: Review unused parameters](../code-quality/ca1801-review-unused-parameters.md)