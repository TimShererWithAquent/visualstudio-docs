---
title: "CA2109: Review visible event handlers"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
  - "CA2109"
  - "ReviewVisibleEventHandlers"
helpviewer_keywords:
  - "ReviewVisibleEventHandlers"
  - "CA2109"
ms.assetid: 8f8fa0ee-e94e-400e-b516-24d8727725d7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
  - "multiple"
---
# CA2109: Review visible event handlers

|||
|-|-|
|TypeName|ReviewVisibleEventHandlers|
|CheckId|CA2109|
|Category|Microsoft.Security|
|Breaking change|Breaking|

## Cause
A public or protected event-handling method was detected.

## Rule description
An externally visible event-handling method presents a security issue that requires review.

Do not expose event-handling methods unless absolutely necessary. An event handler, a delegate type, that invokes the exposed method can be added to any event as long as the handler and event signatures match. Events can potentially be raised by any code, and are frequently raised by highly trusted system code in response to user actions such as clicking a button. Adding a security check to an event-handling method does not prevent code from registering an event handler that invokes the method.

A demand cannot reliably protect a method invoked by an event handler. Security demands help protect code from untrusted callers by examining the callers on the call stack. Code that adds an event handler to an event is not necessarily present on the call stack when the event handler's methods run. Therefore, the call stack might have only highly trusted callers when the event handler method is invoked. This causes demands made by the event handler method to succeed. Also, the demanded permission might be asserted when the method is invoked. For these reasons, the risk of not fixing a violation of this rule can only be assessed after reviewing the event-handling method. When you review your code, consider the following issues:

- Does your event handler perform any operations that are dangerous or exploitable, such as asserting permissions or suppressing unmanaged code permission?

- What are the security threats to and from your code because it can run at any time with only highly trusted callers on the stack?

## How to fix violations
To fix a violation of this rule, review the method and evaluate the following:

- Can you make the event-handling method non-public?

- Can you move all dangerous functionality out of the event handler?

- If a security demand is imposed, can this be accomplished in some other manner?

## When to suppress warnings
Suppress a warning from this rule only after a careful security review to make sure that your code does not pose a security threat.

## Example
The following code shows an event-handling method that can be misused by malicious code.

[!code-csharp[FxCop.Security.EventSecLib#1](../code-quality/codesnippet/CSharp/ca2109-review-visible-event-handlers_1.cs)]

## See also

- <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName>
- <xref:System.EventArgs?displayProperty=fullName>