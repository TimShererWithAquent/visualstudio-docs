---
title: "CA2239: Provide deserialization methods for optional fields"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
  - "CA2239"
  - "ProvideDeserializationMethodsForOptionalFields"
helpviewer_keywords:
  - "ProvideDeserializationMethodsForOptionalFields"
  - "CA2239"
ms.assetid: 6480ff5e-0caa-4707-814e-2f927cdafef5
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
 - CSharp
 - VB
ms.workload:
  - "multiple"
---
# CA2239: Provide deserialization methods for optional fields

|||
|-|-|
|TypeName|ProvideDeserializationMethodsForOptionalFields|
|CheckId|CA2239|
|Category|Microsoft.Usage|
|Breaking change|Non-breaking|

## Cause
A type has a field that is marked with the <xref:System.Runtime.Serialization.OptionalFieldAttribute?displayProperty=fullName> attribute and the type does not provide de-serialization event handling methods.

## Rule description
The <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute has no effect on serialization; a field marked with the attribute is serialized. However, the field is ignored on de-serialization and retains the default value associated with its type. De-serialization event handlers should be declared to set the field during the de-serialization process.

## How to fix violations
To fix a violation of this rule, add de-serialization event handling methods to the type.

## When to suppress warnings
It is safe to suppress a warning from this rule if the field should be ignored during the de-serialization process.

## Example
The following example shows a type with an optional field and de-serialization event handling methods.

[!code-csharp[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/CSharp/ca2239-provide-deserialization-methods-for-optional-fields_1.cs)]
[!code-vb[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/VisualBasic/ca2239-provide-deserialization-methods-for-optional-fields_1.vb)]

## Related rules
[CA2236: Call base class methods on ISerializable types](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

[CA2240: Implement ISerializable correctly](../code-quality/ca2240-implement-iserializable-correctly.md)

[CA2229: Implement serialization constructors](../code-quality/ca2229-implement-serialization-constructors.md)

[CA2238: Implement serialization methods correctly](../code-quality/ca2238-implement-serialization-methods-correctly.md)

[CA2235: Mark all non-serializable fields](../code-quality/ca2235-mark-all-non-serializable-fields.md)

[CA2237: Mark ISerializable types with SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

[CA2120: Secure serialization constructors](../code-quality/ca2120-secure-serialization-constructors.md)