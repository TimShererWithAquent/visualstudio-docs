---
title: "CA1305: Specify IFormatProvider"
ms.date: 06/30/2018
ms.topic: reference
f1_keywords:
  - "SpecifyIFormatProvider"
  - "CA1305"
helpviewer_keywords:
  - "CA1305"
  - "SpecifyIFormatProvider"
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
 - CSharp
ms.workload:
  - "multiple"
---
# CA1305: Specify IFormatProvider

|||
|-|-|
|TypeName|SpecifyIFormatProvider|
|CheckId|CA1305|
|Category|Microsoft.Globalization|
|Breaking change|Non-breaking|

## Cause

A method or constructor calls one or more members that have overloads that accept a <xref:System.IFormatProvider?displayProperty=fullName> parameter, and the method or constructor does not call the overload that takes the <xref:System.IFormatProvider> parameter.

This rule ignores calls to .NET methods that are documented as ignoring the <xref:System.IFormatProvider> parameter. The rule also ignores the following methods:

- <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>

## Rule description

When a <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> or <xref:System.IFormatProvider> object is not supplied, the default value that is supplied by the overloaded member might not have the effect that you want in all locales. Also, .NET members choose default culture and formatting based on assumptions that might not be correct for your code. To make sure that the code works as expected for your scenarios, you should supply culture-specific information according to the following guidelines:

- If the value will be displayed to the user, use the current culture. See <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.

- If the value will be stored and accessed by software (persisted to a file or database), use the invariant culture. See <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.

- If you do not know the destination of the value, have the data consumer or provider specify the culture.

Even if the default behavior of the overloaded member is appropriate for your needs, it is better to explicitly call the culture-specific overload so that your code is self-documenting and more easily maintained.

## How to fix violations

To fix a violation of this rule, use the overload that takes an <xref:System.IFormatProvider> argument. Or, use a [C# interpolated string](/dotnet/csharp/tutorials/string-interpolation) and pass it to the <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> method.

## When to suppress warnings

It is safe to suppress a warning from this rule when it is certain that the default format is the correct choice, and where code maintainability is not an important development priority.

## Example

In the following code, the `example1` string violates rule CA1305. The `example2` string satisfies rule CA1305 by passing <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>, which implements <xref:System.IFormatProvider>, to <xref:System.String.Format(System.IFormatProvider,System.String,System.Object)?displayProperty=nameWithType>. The `example3` string satisfies rule CA1305 by passing an interpolated string to <xref:System.FormattableString.Invariant%2A?displayProperty=fullName]>.

```csharp
string name = "Georgette";

// Violates CA1305
string example1 = String.Format("Hello {0}", name);

// Satisfies CA1305
string example2 = String.Format(CultureInfo.CurrentCulture, "Hello {0}", name);

// Satisfies CA1305
string example3 = FormattableString.Invariant($"Hello {name}");
```

## Related rules

- [CA1304: Specify CultureInfo](../code-quality/ca1304-specify-cultureinfo.md)

## See also

- [Using the CultureInfo Class](/dotnet/standard/globalization-localization/globalization#work-with-culture-specific-settings)