---
title: "CA2220: Finalizers should call base class finalizer"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
  - "CA2220"
  - "FinalizersShouldCallBaseClassFinalizer"
helpviewer_keywords:
  - "CA2220"
  - "FinalizersShouldCallBaseClassFinalizer"
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
  - "multiple"
---
# CA2220: Finalizers should call base class finalizer

|||
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|Category|Microsoft.Usage|
|Breaking change|Non-breaking|

## Cause

A type that overrides <xref:System.Object.Finalize%2A?displayProperty=fullName> does not call the <xref:System.Object.Finalize%2A> method in its base class.

## Rule description

Finalization must be propagated through the inheritance hierarchy. To ensure this, types must call their base class <xref:System.Object.Finalize%2A> method from within their own <xref:System.Object.Finalize%2A> method. The C# compiler adds the call to the base class finalizer automatically.

## How to fix violations

To fix a violation of this rule, call the base type's <xref:System.Object.Finalize%2A> method from your <xref:System.Object.Finalize%2A> method.

## When to suppress warnings

Do not suppress a warning from this rule. Some compilers that target the common language runtime insert a call to the base type's finalizer into the Microsoft intermediate language (MSIL). If a warning from this rule is reported, your compiler does not insert the call, and you must add it to your code.

## Example

The following Visual Basic example shows a type `TypeB` that correctly calls the <xref:System.Object.Finalize%2A> method in its base class.

[!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]

## See also

- [Dispose Pattern](/dotnet/standard/design-guidelines/dispose-pattern)