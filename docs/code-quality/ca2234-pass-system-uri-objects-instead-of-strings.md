---
title: "CA2234: Pass System.Uri objects instead of strings"
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
  - "PassSystemUriObjectsInsteadOfStrings"
  - "CA2234"
helpviewer_keywords:
  - "CA2234"
  - "PassSystemUriObjectsInsteadOfStrings"
ms.assetid: 14616b37-74c4-4286-b051-115d00aceb5f
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
# CA2234: Pass System.Uri objects instead of strings

|||
|-|-|
|TypeName|PassSystemUriObjectsInsteadOfStrings|
|CheckId|CA2234|
|Category|Microsoft.Usage|
|Breaking change|Non-breaking|

## Cause

A call is made to a method that has a string parameter whose name contains "uri", "Uri", "urn", "Urn", "url", or "Url" and the declaring type of the method contains a corresponding method overload that has a <xref:System.Uri?displayProperty=fullName> parameter.

By default, this rule only looks at externally visible methods and types, but this is [configurable](#configurability).

## Rule description

A parameter name is split into tokens based on the camel casing convention, and then each token is checked to see whether it equals "uri", "Uri", "urn", "Urn", "url", or "Url". If there is a match, the parameter is assumed to represent a uniform resource identifier (URI). A string representation of a URI is prone to parsing and encoding errors, and can lead to security vulnerabilities. The <xref:System.Uri> class provides these services in a safe and secure manner. When there is a choice between two overloads that differ only regarding the representation of a URI, the user should choose the overload that takes a <xref:System.Uri> argument.

## How to fix violations

To fix a violation of this rule, call the overload that takes the <xref:System.Uri> argument.

## When to suppress warnings

It is safe to suppress a warning from this rule if the string parameter does not represent a URI.

## Configurability

If you're running this rule from [FxCop analyzers](install-fxcop-analyzers.md) (and not with legacy analysis), you can configure which parts of your codebase to run this rule on, based on their accessibility. For example, to specify that the rule should run only against the non-public API surface, add the following key-value pair to an .editorconfig file in your project:

```ini
dotnet_code_quality.ca2234.api_surface = private, internal
```

You can configure this option for just this rule, for all rules, or for all rules in this category (Usage). For more information, see [Configure FxCop analyzers](configure-fxcop-analyzers.md).

## Example

The following example shows a method, `ErrorProne`, that violates the rule and a method, `SaferWay`, that correctly calls the <xref:System.Uri> overload:

[!code-vb[FxCop.Usage.PassUri#1](../code-quality/codesnippet/VisualBasic/ca2234-pass-system-uri-objects-instead-of-strings_1.vb)]
[!code-cpp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CPP/ca2234-pass-system-uri-objects-instead-of-strings_1.cpp)]
[!code-csharp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CSharp/ca2234-pass-system-uri-objects-instead-of-strings_1.cs)]

## Related rules

- [CA1057: String URI overloads call System.Uri overloads](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)
- [CA1056: URI properties should not be strings](../code-quality/ca1056-uri-properties-should-not-be-strings.md)
- [CA1054: URI parameters should not be strings](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
- [CA1055: URI return values should not be strings](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)