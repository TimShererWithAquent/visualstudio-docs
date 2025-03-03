---
title: "CA2215: Dispose methods should call base class dispose"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
  - "CA2215"
  - "DisposeMethodsShouldCallBaseClassDispose"
  - "Dispose methods should call base class dispose"
helpviewer_keywords:
  - "DisposeMethodsShouldCallBaseClassDispose"
  - "CA2215"
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
  - "multiple"
---
# CA2215: Dispose methods should call base class dispose

|||
|-|-|
|TypeName|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|Category|Microsoft.Usage|
|Breaking change|Non-breaking|

## Cause
A type that implements <xref:System.IDisposable?displayProperty=fullName> inherits from a type that also implements <xref:System.IDisposable>. The <xref:System.IDisposable.Dispose%2A> method of the inheriting type does not call the <xref:System.IDisposable.Dispose%2A> method of the parent type.

## Rule description
If a type inherits from a disposable type, it must call the <xref:System.IDisposable.Dispose%2A> method of the base type from within its own <xref:System.IDisposable.Dispose%2A> method. Calling the base type method Dispose ensures that any resources created by the base type are released.

## How to fix violations
To fix a violation of this rule, call `base`.<xref:System.IDisposable.Dispose%2A> in your <xref:System.IDisposable.Dispose%2A> method.

## When to suppress warnings
It is safe to suppress a warning from this rule if the call to `base`.<xref:System.IDisposable.Dispose%2A> occurs at a deeper calling level than the rule checks.

## Example
The following example shows a type `TypeA` that implements <xref:System.IDisposable>.

[!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2215-dispose-methods-should-call-base-class-dispose_1.cs)]

## Example
The following example shows a type `TypeB` that inherits from type `TypeA` and correctly calls its <xref:System.IDisposable.Dispose%2A> method.

[!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2215-dispose-methods-should-call-base-class-dispose_2.vb)]

## See also

- <xref:System.IDisposable?displayProperty=fullName>
- [Dispose Pattern](/dotnet/standard/design-guidelines/dispose-pattern)