---
title: Předdefinované typy – C# referenční informace
description: Seznamte C# se s předdefinovanými typy hodnot a odkazů.
ms.date: 02/04/2020
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: 4f748373350ed0596a5f1d595c273243ae3227c3
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095307"
---
# <a name="built-in-types-c-reference"></a><span data-ttu-id="ed7fa-103">Předdefinované typy (C# Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="ed7fa-103">Built-in types (C# reference)</span></span>

<span data-ttu-id="ed7fa-104">Následující tabulka uvádí C# předdefinované typy [hodnot](value-types.md) :</span><span class="sxs-lookup"><span data-stu-id="ed7fa-104">The following table lists the C# built-in [value](value-types.md) types:</span></span>

|<span data-ttu-id="ed7fa-105">C#klíčové slovo Type</span><span class="sxs-lookup"><span data-stu-id="ed7fa-105">C# type keyword</span></span>|<span data-ttu-id="ed7fa-106">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="ed7fa-106">.NET type</span></span>|
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

<span data-ttu-id="ed7fa-107">V následující tabulce jsou uvedeny C# typy integrovaných [odkazů](../keywords/reference-types.md) :</span><span class="sxs-lookup"><span data-stu-id="ed7fa-107">The following table lists the C# built-in [reference](../keywords/reference-types.md) types:</span></span>

|<span data-ttu-id="ed7fa-108">C#klíčové slovo Type</span><span class="sxs-lookup"><span data-stu-id="ed7fa-108">C# type keyword</span></span>|<span data-ttu-id="ed7fa-109">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="ed7fa-109">.NET type</span></span>|
|--------------|-------------------------|
|[`object`](reference-types.md#the-object-type)|<xref:System.Object?displayProperty=nameWithType>|
|[`string`](reference-types.md#the-string-type)|<xref:System.String?displayProperty=nameWithType>|

<span data-ttu-id="ed7fa-110">V předchozích tabulkách je každé C# klíčové slovo Type z levého sloupce alias pro odpovídající typ rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="ed7fa-110">In the preceding tables, each C# type keyword from the left column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="ed7fa-111">Jsou zaměnitelné.</span><span class="sxs-lookup"><span data-stu-id="ed7fa-111">They are interchangeable.</span></span> <span data-ttu-id="ed7fa-112">Například následující deklarace deklaruje proměnné stejného typu:</span><span class="sxs-lookup"><span data-stu-id="ed7fa-112">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

## <a name="see-also"></a><span data-ttu-id="ed7fa-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="ed7fa-113">See also</span></span>

- [<span data-ttu-id="ed7fa-114">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="ed7fa-114">C# reference</span></span>](../index.md)
- [<span data-ttu-id="ed7fa-115">Výchozí hodnoty C# typů</span><span class="sxs-lookup"><span data-stu-id="ed7fa-115">Default values of C# types</span></span>](default-values.md)
- [<span data-ttu-id="ed7fa-116">`dynamic` – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="ed7fa-116">`dynamic` keyword</span></span>](reference-types.md#the-dynamic-type)
