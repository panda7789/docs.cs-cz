---
title: Tabulka výchozích hodnot (referenční dokumentace jazyka C#)
description: Zjistěte, jaké jsou výchozí hodnoty typů hodnot vrácených výchozí konstruktory.
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], return values
- keywords [C#], new
- default constructor [C#]
- defaults [C#]
- value types [C#], initializing
- variables [C#], value types
- constructors [C#], default constructor
- types [C#], default constructor return values
ms.openlocfilehash: 634a55304534b4269487f29be1fbb4930f51d8ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218787"
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="c8855-103">Tabulka výchozích hodnot (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="c8855-103">Default values table (C# Reference)</span></span>

<span data-ttu-id="c8855-104">V následující tabulce jsou uvedeny výchozí hodnoty typů hodnot vrácených výchozí konstruktory.</span><span class="sxs-lookup"><span data-stu-id="c8855-104">The following table shows the default values of value types returned by the default constructors.</span></span> <span data-ttu-id="c8855-105">Výchozí konstruktory jsou vyvolány pomocí `new` operátor následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="c8855-105">Default constructors are invoked by using the `new` operator, as follows:</span></span>

```csharp
int myInt = new int();
```

<span data-ttu-id="c8855-106">Předchozí příkaz má stejný účinek jako následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="c8855-106">The preceding statement has the same effect as the following statement:</span></span>

```csharp
int myInt = 0;
```

<span data-ttu-id="c8855-107">Mějte na paměti, že není povolené použití neinicializovaného proměnných v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="c8855-107">Remember that using uninitialized variables in C# is not allowed.</span></span>

|<span data-ttu-id="c8855-108">Typ hodnoty</span><span class="sxs-lookup"><span data-stu-id="c8855-108">Value type</span></span>|<span data-ttu-id="c8855-109">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="c8855-109">Default value</span></span>|
|----------------|-------------------|
|[<span data-ttu-id="c8855-110">bool</span><span class="sxs-lookup"><span data-stu-id="c8855-110">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="c8855-111">byte</span><span class="sxs-lookup"><span data-stu-id="c8855-111">byte</span></span>](byte.md)|<span data-ttu-id="c8855-112">0</span><span class="sxs-lookup"><span data-stu-id="c8855-112">0</span></span>|
|[<span data-ttu-id="c8855-113">char</span><span class="sxs-lookup"><span data-stu-id="c8855-113">char</span></span>](char.md)|<span data-ttu-id="c8855-114">'\0'</span><span class="sxs-lookup"><span data-stu-id="c8855-114">'\0'</span></span>|
|[<span data-ttu-id="c8855-115">decimal</span><span class="sxs-lookup"><span data-stu-id="c8855-115">decimal</span></span>](decimal.md)|<span data-ttu-id="c8855-116">0M</span><span class="sxs-lookup"><span data-stu-id="c8855-116">0M</span></span>|
|[<span data-ttu-id="c8855-117">double</span><span class="sxs-lookup"><span data-stu-id="c8855-117">double</span></span>](double.md)|<span data-ttu-id="c8855-118">0,0 D</span><span class="sxs-lookup"><span data-stu-id="c8855-118">0.0D</span></span>|
|[<span data-ttu-id="c8855-119">enum</span><span class="sxs-lookup"><span data-stu-id="c8855-119">enum</span></span>](enum.md)|<span data-ttu-id="c8855-120">Hodnota vyprodukované výraz (E) 0, kde E je identifikátor výčtu.</span><span class="sxs-lookup"><span data-stu-id="c8855-120">The value produced by the expression (E)0, where E is the enum identifier.</span></span>|
|[<span data-ttu-id="c8855-121">float</span><span class="sxs-lookup"><span data-stu-id="c8855-121">float</span></span>](float.md)|<span data-ttu-id="c8855-122">0,0 F</span><span class="sxs-lookup"><span data-stu-id="c8855-122">0.0F</span></span>|
|[<span data-ttu-id="c8855-123">int</span><span class="sxs-lookup"><span data-stu-id="c8855-123">int</span></span>](int.md)|<span data-ttu-id="c8855-124">0</span><span class="sxs-lookup"><span data-stu-id="c8855-124">0</span></span>|
|[<span data-ttu-id="c8855-125">long</span><span class="sxs-lookup"><span data-stu-id="c8855-125">long</span></span>](long.md)|<span data-ttu-id="c8855-126">0L</span><span class="sxs-lookup"><span data-stu-id="c8855-126">0L</span></span>|
|[<span data-ttu-id="c8855-127">sbyte</span><span class="sxs-lookup"><span data-stu-id="c8855-127">sbyte</span></span>](sbyte.md)|<span data-ttu-id="c8855-128">0</span><span class="sxs-lookup"><span data-stu-id="c8855-128">0</span></span>|
|[<span data-ttu-id="c8855-129">short</span><span class="sxs-lookup"><span data-stu-id="c8855-129">short</span></span>](short.md)|<span data-ttu-id="c8855-130">0</span><span class="sxs-lookup"><span data-stu-id="c8855-130">0</span></span>|
|[<span data-ttu-id="c8855-131">struct</span><span class="sxs-lookup"><span data-stu-id="c8855-131">struct</span></span>](struct.md)|<span data-ttu-id="c8855-132">Hodnota vytvořeného nastavením všechna pole typu hodnoty na jejich výchozí hodnoty a všechna pole typu odkazu na `null`.</span><span class="sxs-lookup"><span data-stu-id="c8855-132">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|[<span data-ttu-id="c8855-133">uint</span><span class="sxs-lookup"><span data-stu-id="c8855-133">uint</span></span>](uint.md)|<span data-ttu-id="c8855-134">0</span><span class="sxs-lookup"><span data-stu-id="c8855-134">0</span></span>|
|[<span data-ttu-id="c8855-135">ulong</span><span class="sxs-lookup"><span data-stu-id="c8855-135">ulong</span></span>](ulong.md)|<span data-ttu-id="c8855-136">0</span><span class="sxs-lookup"><span data-stu-id="c8855-136">0</span></span>|
|[<span data-ttu-id="c8855-137">ushort</span><span class="sxs-lookup"><span data-stu-id="c8855-137">ushort</span></span>](ushort.md)|<span data-ttu-id="c8855-138">0</span><span class="sxs-lookup"><span data-stu-id="c8855-138">0</span></span>|

## <a name="see-also"></a><span data-ttu-id="c8855-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="c8855-139">See also</span></span>
 [<span data-ttu-id="c8855-140">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c8855-140">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="c8855-141">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="c8855-141">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="c8855-142">Tabulka typů hodnot</span><span class="sxs-lookup"><span data-stu-id="c8855-142">Value Types Table</span></span>](value-types-table.md)  
 [<span data-ttu-id="c8855-143">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="c8855-143">Value Types</span></span>](value-types.md)  
 [<span data-ttu-id="c8855-144">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="c8855-144">Built-In Types Table</span></span>](built-in-types-table.md)  
 [<span data-ttu-id="c8855-145">Referenční tabulky pro typy</span><span class="sxs-lookup"><span data-stu-id="c8855-145">Reference Tables for Types</span></span>](reference-tables-for-types.md)
