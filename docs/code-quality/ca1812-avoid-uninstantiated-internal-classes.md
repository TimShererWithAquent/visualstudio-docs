---
title: "CA1812: Avoid uninstantiated internal classes"
ms.date: 05/16/2019
ms.topic: reference
f1_keywords:
  - "CA1812"
  - "AvoidUninstantiatedInternalClasses"
helpviewer_keywords:
  - "AvoidUninstantiatedInternalClasses"
  - "CA1812"
ms.assetid: 1bb92a42-322a-44cc-98a8-8858212c1e1f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
  - "multiple"
---
# CA1812: Avoid uninstantiated internal classes

|||
|-|-|
|TypeName|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|Category|Microsoft.Performance|
|Breaking change|Non-breaking|

## Cause

An internal (assembly-level) type is never instantiated.

## Rule description

This rule tries to locate a call to one of the constructors of the type and reports a violation if no call is found.

The following types are not examined by this rule:

- Value types

- Abstract types

- Enumerations

- Delegates

- Compiler-emitted array types

- Types that cannot be instantiated and that only define [`static`](/dotnet/csharp/language-reference/keywords/static) ([`Shared` in Visual Basic](/dotnet/visual-basic/language-reference/modifiers/shared)) methods.

If you apply the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> to the assembly that's being analyzed, this rule will not flag types that are marked as [`internal`](/dotnet/csharp/language-reference/keywords/internal) ([`Friend` in Visual Basic](/dotnet/visual-basic/language-reference/modifiers/friend)) because a field may be used by a friend assembly.

## How to fix violations

To fix a violation of this rule, remove the type or add code that uses it. If the type contains only `static` methods, add one of the following to the type to prevent the compiler from emitting a default public instance constructor:

- The `static` modifier for C# types that target .NET Framework 2.0 or later.

- A private constructor for types that target .NET Framework versions 1.0 and 1.1.

## When to suppress warnings

It is safe to suppress a warning from this rule. We recommend that you suppress this warning in the following situations:

- The class is created through late-bound reflection methods such as <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>.

- The class is created automatically by the runtime or ASP.NET. Some examples of automatically created classes are those that implement <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> or <xref:System.Web.IHttpHandler?displayProperty=fullName>.

- The class is passed as a type parameter that has a [`new` constraint](/dotnet/csharp/language-reference/keywords/new-constraint). The following example will be flagged by rule CA1812:

    ```csharp
    internal class MyClass
    {
        public DoSomething()
        {
        }
    }
    public class MyGeneric<T> where T : new()
    {
        public T Create()
        {
            return new T();
        }
    }

    MyGeneric<MyClass> mc = new MyGeneric<MyClass>();
    mc.Create();
    ```

## Related rules

- [CA1811: Avoid uncalled private code](../code-quality/ca1811-avoid-uncalled-private-code.md)
- [CA1801: Review unused parameters](../code-quality/ca1801-review-unused-parameters.md)
- [CA1804: Remove unused locals](../code-quality/ca1804-remove-unused-locals.md)