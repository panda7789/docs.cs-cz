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
# <a name="built-in-types-c-reference"></a><span data-ttu-id="26af0-103">Předdefinované typy (odkaz C#</span><span class="sxs-lookup"><span data-stu-id="26af0-103">Built-in types (C# reference)</span></span>

<span data-ttu-id="26af0-104">V následující tabulce jsou uvedeny předdefinované typy [hodnot](value-types.md) jazyka C#:</span><span class="sxs-lookup"><span data-stu-id="26af0-104">The following table lists the C# built-in [value](value-types.md) types:</span></span>

|<span data-ttu-id="26af0-105">Klíčové slovo typu C#</span><span class="sxs-lookup"><span data-stu-id="26af0-105">C# type keyword</span></span>|<span data-ttu-id="26af0-106">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="26af0-106">.NET type</span></span>|
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

<span data-ttu-id="26af0-107">V následující tabulce jsou uvedeny předdefinované typy [odkazů](../keywords/reference-types.md) jazyka C#:</span><span class="sxs-lookup"><span data-stu-id="26af0-107">The following table lists the C# built-in [reference](../keywords/reference-types.md) types:</span></span>

|<span data-ttu-id="26af0-108">Klíčové slovo typu C#</span><span class="sxs-lookup"><span data-stu-id="26af0-108">C# type keyword</span></span>|<span data-ttu-id="26af0-109">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="26af0-109">.NET type</span></span>|
|--------------|-------------------------|
|[`object`](reference-types.md#the-object-type)|<xref:System.Object?displayProperty=nameWithType>|
|[`string`](reference-types.md#the-string-type)|<xref:System.String?displayProperty=nameWithType>|

<span data-ttu-id="26af0-110">V předchozích tabulkách je každé klíčové slovo c# z levého sloupce aliasem odpovídajícího typu .NET.</span><span class="sxs-lookup"><span data-stu-id="26af0-110">In the preceding tables, each C# type keyword from the left column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="26af0-111">Jsou zaměnitelné.</span><span class="sxs-lookup"><span data-stu-id="26af0-111">They are interchangeable.</span></span> <span data-ttu-id="26af0-112">Například následující deklarace deklarují proměnné stejného typu:</span><span class="sxs-lookup"><span data-stu-id="26af0-112">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

<span data-ttu-id="26af0-113">Klíčové [`void`](void.md) slovo představuje nepřítomnost typu.</span><span class="sxs-lookup"><span data-stu-id="26af0-113">The [`void`](void.md) keyword represents the absence of a type.</span></span> <span data-ttu-id="26af0-114">Použijete jej jako návratový typ metody, která nevrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="26af0-114">You use it as the return type of a method that doesn't return a value.</span></span>

## <a name="see-also"></a><span data-ttu-id="26af0-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="26af0-115">See also</span></span>

- [<span data-ttu-id="26af0-116">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="26af0-116">C# reference</span></span>](../index.md)
- [<span data-ttu-id="26af0-117">Výchozí hodnoty typů jazyka C#</span><span class="sxs-lookup"><span data-stu-id="26af0-117">Default values of C# types</span></span>](default-values.md)
- [<span data-ttu-id="26af0-118">`dynamic`Klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="26af0-118">`dynamic` keyword</span></span>](reference-types.md#the-dynamic-type)
