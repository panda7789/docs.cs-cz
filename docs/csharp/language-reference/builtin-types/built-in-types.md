---
title: Předdefinované typy – odkaz jazyka C#
description: Naučte se c# předdefinované hodnoty a typy odkazů
ms.date: 02/04/2020
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: bf8823c6674b1ff3f0028a50df8ce8d0f803cfc1
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389496"
---
# <a name="built-in-types-c-reference"></a>Předdefinované typy (odkaz C#

V následující tabulce jsou uvedeny předdefinované typy [hodnot](value-types.md) jazyka C#:

|Klíčové slovo typu C#|Typ .NET|
|--------------|-------------------------|
|[`bool`](bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|
|[`byte`](integral-numeric-types.md)|<xref:System.Byte?displayProperty=nameWithType>|
|[`sbyte`](integral-numeric-types.md)|<xref:System.SByte?displayProperty=nameWithType>|
|[`char`](char.md)|<xref:System.Char?displayProperty=nameWithType>|
|[`decimal`](floating-point-numeric-types.md)|<xref:System.Decimal?displayProperty=nameWithType>|
|[`double`](floating-point-numeric-types.md)|<xref:System.Double?displayProperty=nameWithType>|
|[`float`](floating-point-numeric-types.md)|<xref:System.Single?displayProperty=nameWithType>|
|[`int`](integral-numeric-types.md)|<xref:System.Int32?displayProperty=nameWithType>|
|[`uint`](integral-numeric-types.md)|<xref:System.UInt32?displayProperty=nameWithType>|
|[`long`](integral-numeric-types.md)|<xref:System.Int64?displayProperty=nameWithType>|
|[`ulong`](integral-numeric-types.md)|<xref:System.UInt64?displayProperty=nameWithType>|
|[`short`](integral-numeric-types.md)|<xref:System.Int16?displayProperty=nameWithType>|
|[`ushort`](integral-numeric-types.md)|<xref:System.UInt16?displayProperty=nameWithType>|

V následující tabulce jsou uvedeny předdefinované typy [odkazů](../keywords/reference-types.md) jazyka C#:

|Klíčové slovo typu C#|Typ .NET|
|--------------|-------------------------|
|[`object`](reference-types.md#the-object-type)|<xref:System.Object?displayProperty=nameWithType>|
|[`string`](reference-types.md#the-string-type)|<xref:System.String?displayProperty=nameWithType>|

V předchozích tabulkách je každé klíčové slovo c# z levého sloupce aliasem odpovídajícího typu .NET. Jsou zaměnitelné. Například následující deklarace deklarují proměnné stejného typu:

```csharp
int a = 123;
System.Int32 b = 123;
```

Klíčové [`void`](void.md) slovo představuje nepřítomnost typu. Použijete jej jako návratový typ metody, která nevrací hodnotu.

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Výchozí hodnoty typů jazyka C#](default-values.md)
- [`dynamic`Klíčové slovo](reference-types.md#the-dynamic-type)
