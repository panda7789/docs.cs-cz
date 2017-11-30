---
title: "Tabulka výchozích hodnot (referenční dokumentace jazyka C#)"
descripton: Learn what are the default values of value types returned by the default constructors.
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- constructors [C#], return values
- keywords [C#], new
- default constructor [C#]
- defaults [C#]
- value types [C#], initializing
- variables [C#], value types
- constructors [C#], default constructor
- types [C#], default constructor return values
ms.assetid: 4af2c1df-9e3a-48c1-83ac-b192986fc5bc
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7f692ee1242af88dc6bd3938f7a00f3d11ed8ca7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="b321f-102">Tabulka výchozích hodnot (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b321f-102">Default values table (C# Reference)</span></span>
<span data-ttu-id="b321f-103">V následující tabulce jsou uvedeny výchozí hodnoty typů hodnot vrácených výchozí konstruktory.</span><span class="sxs-lookup"><span data-stu-id="b321f-103">The following table shows the default values of value types returned by the default constructors.</span></span> <span data-ttu-id="b321f-104">Výchozí konstruktory jsou vyvolány pomocí `new` operátor následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="b321f-104">Default constructors are invoked by using the `new` operator, as follows:</span></span>

```csharp
int myInt = new int();
```

<span data-ttu-id="b321f-105">Předchozí příkaz má stejný účinek jako následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="b321f-105">The preceding statement has the same effect as the following statement:</span></span>

```csharp
int myInt = 0;
```

<span data-ttu-id="b321f-106">Mějte na paměti, že není povolené použití neinicializovaného proměnných v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="b321f-106">Remember that using uninitialized variables in C# is not allowed.</span></span>

|<span data-ttu-id="b321f-107">Typ hodnoty</span><span class="sxs-lookup"><span data-stu-id="b321f-107">Value type</span></span>|<span data-ttu-id="b321f-108">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="b321f-108">Default value</span></span>|
|----------------|-------------------|
|[<span data-ttu-id="b321f-109">BOOL</span><span class="sxs-lookup"><span data-stu-id="b321f-109">bool</span></span>](../../../csharp/language-reference/keywords/bool.md)|`false`|
|[<span data-ttu-id="b321f-110">bajtů</span><span class="sxs-lookup"><span data-stu-id="b321f-110">byte</span></span>](../../../csharp/language-reference/keywords/byte.md)|<span data-ttu-id="b321f-111">0</span><span class="sxs-lookup"><span data-stu-id="b321f-111">0</span></span>|
|[<span data-ttu-id="b321f-112">Char</span><span class="sxs-lookup"><span data-stu-id="b321f-112">char</span></span>](../../../csharp/language-reference/keywords/char.md)|<span data-ttu-id="b321f-113">'\0'</span><span class="sxs-lookup"><span data-stu-id="b321f-113">'\0'</span></span>|
|[<span data-ttu-id="b321f-114">Decimal</span><span class="sxs-lookup"><span data-stu-id="b321f-114">decimal</span></span>](../../../csharp/language-reference/keywords/decimal.md)|<span data-ttu-id="b321f-115">0,0 M</span><span class="sxs-lookup"><span data-stu-id="b321f-115">0.0M</span></span>|
|[<span data-ttu-id="b321f-116">Double</span><span class="sxs-lookup"><span data-stu-id="b321f-116">double</span></span>](../../../csharp/language-reference/keywords/double.md)|<span data-ttu-id="b321f-117">0,0 D</span><span class="sxs-lookup"><span data-stu-id="b321f-117">0.0D</span></span>|
|[<span data-ttu-id="b321f-118">výčet</span><span class="sxs-lookup"><span data-stu-id="b321f-118">enum</span></span>](../../../csharp/language-reference/keywords/enum.md)|<span data-ttu-id="b321f-119">Hodnota vyprodukované výraz (E) 0, kde E je identifikátor výčtu.</span><span class="sxs-lookup"><span data-stu-id="b321f-119">The value produced by the expression (E)0, where E is the enum identifier.</span></span>|
|[<span data-ttu-id="b321f-120">plovoucí desetinná čárka</span><span class="sxs-lookup"><span data-stu-id="b321f-120">float</span></span>](../../../csharp/language-reference/keywords/float.md)|<span data-ttu-id="b321f-121">0,0 F</span><span class="sxs-lookup"><span data-stu-id="b321f-121">0.0F</span></span>|
|[<span data-ttu-id="b321f-122">celá čísla</span><span class="sxs-lookup"><span data-stu-id="b321f-122">int</span></span>](../../../csharp/language-reference/keywords/int.md)|<span data-ttu-id="b321f-123">0</span><span class="sxs-lookup"><span data-stu-id="b321f-123">0</span></span>|
|[<span data-ttu-id="b321f-124">dlouhá</span><span class="sxs-lookup"><span data-stu-id="b321f-124">long</span></span>](../../../csharp/language-reference/keywords/long.md)|<span data-ttu-id="b321f-125">0L</span><span class="sxs-lookup"><span data-stu-id="b321f-125">0L</span></span>|
|[<span data-ttu-id="b321f-126">SByte –</span><span class="sxs-lookup"><span data-stu-id="b321f-126">sbyte</span></span>](../../../csharp/language-reference/keywords/sbyte.md)|<span data-ttu-id="b321f-127">0</span><span class="sxs-lookup"><span data-stu-id="b321f-127">0</span></span>|
|[<span data-ttu-id="b321f-128">krátký</span><span class="sxs-lookup"><span data-stu-id="b321f-128">short</span></span>](../../../csharp/language-reference/keywords/short.md)|<span data-ttu-id="b321f-129">0</span><span class="sxs-lookup"><span data-stu-id="b321f-129">0</span></span>|
|[<span data-ttu-id="b321f-130">Struktura</span><span class="sxs-lookup"><span data-stu-id="b321f-130">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)|<span data-ttu-id="b321f-131">Hodnota vytvořeného nastavením všechna pole typu hodnoty na jejich výchozí hodnoty a všechna pole typu odkazu na `null`.</span><span class="sxs-lookup"><span data-stu-id="b321f-131">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|[<span data-ttu-id="b321f-132">uint</span><span class="sxs-lookup"><span data-stu-id="b321f-132">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)|<span data-ttu-id="b321f-133">0</span><span class="sxs-lookup"><span data-stu-id="b321f-133">0</span></span>|
|[<span data-ttu-id="b321f-134">ulong –</span><span class="sxs-lookup"><span data-stu-id="b321f-134">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md)|<span data-ttu-id="b321f-135">0</span><span class="sxs-lookup"><span data-stu-id="b321f-135">0</span></span>|
|[<span data-ttu-id="b321f-136">ushort –</span><span class="sxs-lookup"><span data-stu-id="b321f-136">ushort</span></span>](../../../csharp/language-reference/keywords/ushort.md)|<span data-ttu-id="b321f-137">0</span><span class="sxs-lookup"><span data-stu-id="b321f-137">0</span></span>|

## <a name="see-also"></a><span data-ttu-id="b321f-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="b321f-138">See also</span></span>
 [<span data-ttu-id="b321f-139">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b321f-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="b321f-140">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="b321f-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b321f-141">Tabulka typů hodnot</span><span class="sxs-lookup"><span data-stu-id="b321f-141">Value Types Table</span></span>](../../../csharp/language-reference/keywords/value-types-table.md)  
 [<span data-ttu-id="b321f-142">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="b321f-142">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
 [<span data-ttu-id="b321f-143">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="b321f-143">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="b321f-144">Referenční tabulky pro typy</span><span class="sxs-lookup"><span data-stu-id="b321f-144">Reference Tables for Types</span></span>](../../../csharp/language-reference/keywords/reference-tables-for-types.md)
