---
title: "CA1041: Provide ObsoleteAttribute message"
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
  - "CA1041"
  - "ProvideObsoleteAttributeMessage"
helpviewer_keywords:
  - "ProvideObsoleteAttributeMessage"
  - "CA1041"
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
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
# CA1041: Provide ObsoleteAttribute message

|||
|-|-|
|TypeName|ProvideObsoleteAttributeMessage|
|CheckId|CA1041|
|Category|Microsoft.Design|
|Breaking Change|Non-breaking|

## Cause

A type or member is marked by using a <xref:System.ObsoleteAttribute?displayProperty=fullName> attribute that does not have its <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> property specified.

By default, this rule only looks at externally visible types and members, but this is [configurable](#configurability).

## Rule description

<xref:System.ObsoleteAttribute> is used to mark deprecated library types and members. Library consumers should avoid the use of any type or member that is marked obsolete. This is because it might not be supported and will eventually be removed from later versions of the library. When a type or member marked by using <xref:System.ObsoleteAttribute> is compiled, the <xref:System.ObsoleteAttribute.Message%2A> property of the attribute is displayed. This gives the user information about the obsolete type or member. This information generally includes how long the obsolete type or member will be supported by the library designers and the preferred replacement to use.

## How to fix violations

To fix a violation of this rule, add the `message` parameter to the <xref:System.ObsoleteAttribute> constructor.

## When to suppress warnings

Do not suppress a warning from this rule because the <xref:System.ObsoleteAttribute.Message%2A> property provides critical information about the obsolete type or member.

## Configurability

If you're running this rule from [FxCop analyzers](install-fxcop-analyzers.md) (and not with legacy analysis), you can configure which parts of your codebase to run this rule on, based on their accessibility. For example, to specify that the rule should run only against the non-public API surface, add the following key-value pair to an .editorconfig file in your project:

```ini
dotnet_code_quality.ca1041.api_surface = private, internal
```

You can configure this option for just this rule, for all rules, or for all rules in this category (Design). For more information, see [Configure FxCop analyzers](configure-fxcop-analyzers.md).

## Example

The following example shows an obsolete member that has a correctly declared <xref:System.ObsoleteAttribute>.

[!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CPP/ca1041-provide-obsoleteattribute-message_1.cpp)]
[!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CSharp/ca1041-provide-obsoleteattribute-message_1.cs)]
[!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/VisualBasic/ca1041-provide-obsoleteattribute-message_1.vb)]

## See also

- <xref:System.ObsoleteAttribute?displayProperty=fullName>