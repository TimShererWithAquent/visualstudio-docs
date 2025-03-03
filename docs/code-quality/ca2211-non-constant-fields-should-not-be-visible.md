---
title: "CA2211: Non-constant fields should not be visible"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
  - "CA2211"
  - "NonConstantFieldsShouldNotBeVisible"
helpviewer_keywords:
  - "NonConstantFieldsShouldNotBeVisible"
  - "CA2211"
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
 - CSharp
 - VB
ms.workload:
  - "multiple"
---
# CA2211: Non-constant fields should not be visible

|||
|-|-|
|TypeName|NonConstantFieldsShouldNotBeVisible|
|CheckId|CA2211|
|Category|Microsoft.Usage|
|Breaking change|Breaking|

## Cause
A public or protected static field is not constant nor is it read-only.

## Rule description
Static fields that are neither constants nor read-only are not thread-safe. Access to such a field must be carefully controlled and requires advanced programming techniques for synchronizing access to the class object. Because these are difficult skills to learn and master, and testing such an object poses its own challenges, static fields are best used to store data that does not change. This rule applies to libraries; applications should not expose any fields.

## How to fix violations
To fix a violation of this rule, make the static field constant or read-only. If this is not possible, redesign the type to use an alternative mechanism such as a thread-safe property that manages thread-safe access to the underlying field. Realize that issues such as lock contention and deadlocks might affect the performance and behavior of the library.

## When to suppress warnings
It is safe to suppress a warning from this rule if you are developing an application and therefore have full control over access to the type that contains the static field. Library designers should not suppress a warning from this rule; using non-constant static fields can make using the library difficult for developers to use correctly.

## Example
The following example shows a type that violates this rule.

[!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/VisualBasic/ca2211-non-constant-fields-should-not-be-visible_1.vb)]
[!code-csharp[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/CSharp/ca2211-non-constant-fields-should-not-be-visible_1.cs)]