---
title: "CA1049: Types that own native resources should be disposable"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
  - "CA1049"
  - "TypesThatOwnNativeResourcesShouldBeDisposable"
helpviewer_keywords:
  - "TypesThatOwnNativeResourcesShouldBeDisposable"
  - "CA1049"
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
 - CSharp
 - VB
ms.workload:
  - "cplusplus"
---
# CA1049: Types that own native resources should be disposable

|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|Category|Microsoft.Design|
|Breaking change|Non-breaking|

## Cause

A type references a <xref:System.IntPtr?displayProperty=fullName> field, a <xref:System.UIntPtr?displayProperty=fullName> field, or a <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName> field, but does not implement <xref:System.IDisposable?displayProperty=fullName>.

## Rule description

This rule assumes that <xref:System.IntPtr>, <xref:System.UIntPtr>, and <xref:System.Runtime.InteropServices.HandleRef> fields store pointers to unmanaged resources. Types that allocate unmanaged resources should implement <xref:System.IDisposable> to let callers to release those resources on demand and shorten the lifetimes of the objects that hold the resources.

The recommended design pattern to clean up unmanaged resources is to provide both an implicit and an explicit means to free those resources by using the <xref:System.Object.Finalize%2A?displayProperty=fullName> method and the <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> method, respectively. The garbage collector calls the <xref:System.Object.Finalize%2A> method of an object at some indeterminate time after the object is determined to be no longer reachable. After <xref:System.Object.Finalize%2A> is called, an additional garbage collection is required to free the object. The <xref:System.IDisposable.Dispose%2A> method allows the caller to explicitly release resources on demand, earlier than the resources would be released if left to the garbage collector. After it cleans up the unmanaged resources, <xref:System.IDisposable.Dispose%2A> should call the <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> method to let the garbage collector know that <xref:System.Object.Finalize%2A> no longer has to be called; this eliminates the need for the additional garbage collection and shortens the lifetime of the object.

## How to fix violations
To fix a violation of this rule, implement <xref:System.IDisposable>.

## When to suppress warnings
It is safe to suppress a warning from this rule if the type does not reference an unmanaged resource. Otherwise, do not suppress a warning from this rule because failure to implement <xref:System.IDisposable> can cause unmanaged resources to become unavailable or underused.

## Example
The following example shows a type that implements <xref:System.IDisposable> to clean up an unmanaged resource.

[!code-csharp[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/CSharp/ca1049-types-that-own-native-resources-should-be-disposable_1.cs)]
[!code-vb[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/VisualBasic/ca1049-types-that-own-native-resources-should-be-disposable_1.vb)]

## Related rules
[CA2115: Call GC.KeepAlive when using native resources](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

[CA1816: Call GC.SuppressFinalize correctly](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

[CA2216: Disposable types should declare finalizer](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

[CA1001: Types that own disposable fields should be disposable](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## See also

- [Cleaning Up Unmanaged Resources](/dotnet/standard/garbage-collection/unmanaged)
- [Dispose Pattern](/dotnet/standard/design-guidelines/dispose-pattern)