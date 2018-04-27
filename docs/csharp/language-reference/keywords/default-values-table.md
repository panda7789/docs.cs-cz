---
title: Tabulka výchozích hodnot (referenční dokumentace jazyka C#)
descripton: Learn what are the default values of value types returned by the default constructors.
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
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
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e249dd2f352fe6177f3afbfd089fc4dc9b1b7798
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="8abe4-102">Tabulka výchozích hodnot (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="8abe4-102">Default values table (C# Reference)</span></span>

<span data-ttu-id="8abe4-103">V následující tabulce jsou uvedeny výchozí hodnoty typů hodnot vrácených výchozí konstruktory.</span><span class="sxs-lookup"><span data-stu-id="8abe4-103">The following table shows the default values of value types returned by the default constructors.</span></span> <span data-ttu-id="8abe4-104">Výchozí konstruktory jsou vyvolány pomocí `new` operátor následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="8abe4-104">Default constructors are invoked by using the `new` operator, as follows:</span></span>

```csharp
int myInt = new int();
```

<span data-ttu-id="8abe4-105">Předchozí příkaz má stejný účinek jako následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="8abe4-105">The preceding statement has the same effect as the following statement:</span></span>

```csharp
int myInt = 0;
```

<span data-ttu-id="8abe4-106">Mějte na paměti, že není povolené použití neinicializovaného proměnných v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="8abe4-106">Remember that using uninitialized variables in C# is not allowed.</span></span>

|<span data-ttu-id="8abe4-107">Typ hodnoty</span><span class="sxs-lookup"><span data-stu-id="8abe4-107">Value type</span></span>|<span data-ttu-id="8abe4-108">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="8abe4-108">Default value</span></span>|
|----------------|-------------------|
|[<span data-ttu-id="8abe4-109">bool</span><span class="sxs-lookup"><span data-stu-id="8abe4-109">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="8abe4-110">byte</span><span class="sxs-lookup"><span data-stu-id="8abe4-110">byte</span></span>](byte.md)|<span data-ttu-id="8abe4-111">0</span><span class="sxs-lookup"><span data-stu-id="8abe4-111">0</span></span>|
|[<span data-ttu-id="8abe4-112">char</span><span class="sxs-lookup"><span data-stu-id="8abe4-112">char</span></span>](char.md)|<span data-ttu-id="8abe4-113">'\0'</span><span class="sxs-lookup"><span data-stu-id="8abe4-113">'\0'</span></span>|
|[<span data-ttu-id="8abe4-114">decimal</span><span class="sxs-lookup"><span data-stu-id="8abe4-114">decimal</span></span>](decimal.md)|<span data-ttu-id="8abe4-115">0M</span><span class="sxs-lookup"><span data-stu-id="8abe4-115">0M</span></span>|
|[<span data-ttu-id="8abe4-116">double</span><span class="sxs-lookup"><span data-stu-id="8abe4-116">double</span></span>](double.md)|<span data-ttu-id="8abe4-117">0,0 D</span><span class="sxs-lookup"><span data-stu-id="8abe4-117">0.0D</span></span>|
|[<span data-ttu-id="8abe4-118">enum</span><span class="sxs-lookup"><span data-stu-id="8abe4-118">enum</span></span>](enum.md)|<span data-ttu-id="8abe4-119">Hodnota vyprodukované výraz (E) 0, kde E je identifikátor výčtu.</span><span class="sxs-lookup"><span data-stu-id="8abe4-119">The value produced by the expression (E)0, where E is the enum identifier.</span></span>|
|[<span data-ttu-id="8abe4-120">float</span><span class="sxs-lookup"><span data-stu-id="8abe4-120">float</span></span>](float.md)|<span data-ttu-id="8abe4-121">0,0 F</span><span class="sxs-lookup"><span data-stu-id="8abe4-121">0.0F</span></span>|
|[<span data-ttu-id="8abe4-122">int</span><span class="sxs-lookup"><span data-stu-id="8abe4-122">int</span></span>](int.md)|<span data-ttu-id="8abe4-123">0</span><span class="sxs-lookup"><span data-stu-id="8abe4-123">0</span></span>|
|[<span data-ttu-id="8abe4-124">long</span><span class="sxs-lookup"><span data-stu-id="8abe4-124">long</span></span>](long.md)|<span data-ttu-id="8abe4-125">0L</span><span class="sxs-lookup"><span data-stu-id="8abe4-125">0L</span></span>|
|[<span data-ttu-id="8abe4-126">sbyte</span><span class="sxs-lookup"><span data-stu-id="8abe4-126">sbyte</span></span>](sbyte.md)|<span data-ttu-id="8abe4-127">0</span><span class="sxs-lookup"><span data-stu-id="8abe4-127">0</span></span>|
|[<span data-ttu-id="8abe4-128">short</span><span class="sxs-lookup"><span data-stu-id="8abe4-128">short</span></span>](short.md)|<span data-ttu-id="8abe4-129">0</span><span class="sxs-lookup"><span data-stu-id="8abe4-129">0</span></span>|
|[<span data-ttu-id="8abe4-130">struct</span><span class="sxs-lookup"><span data-stu-id="8abe4-130">struct</span></span>](struct.md)|<span data-ttu-id="8abe4-131">Hodnota vytvořeného nastavením všechna pole typu hodnoty na jejich výchozí hodnoty a všechna pole typu odkazu na `null`.</span><span class="sxs-lookup"><span data-stu-id="8abe4-131">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|[<span data-ttu-id="8abe4-132">uint</span><span class="sxs-lookup"><span data-stu-id="8abe4-132">uint</span></span>](uint.md)|<span data-ttu-id="8abe4-133">0</span><span class="sxs-lookup"><span data-stu-id="8abe4-133">0</span></span>|
|[<span data-ttu-id="8abe4-134">ulong</span><span class="sxs-lookup"><span data-stu-id="8abe4-134">ulong</span></span>](ulong.md)|<span data-ttu-id="8abe4-135">0</span><span class="sxs-lookup"><span data-stu-id="8abe4-135">0</span></span>|
|[<span data-ttu-id="8abe4-136">ushort</span><span class="sxs-lookup"><span data-stu-id="8abe4-136">ushort</span></span>](ushort.md)|<span data-ttu-id="8abe4-137">0</span><span class="sxs-lookup"><span data-stu-id="8abe4-137">0</span></span>|

## <a name="see-also"></a><span data-ttu-id="8abe4-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="8abe4-138">See also</span></span>
 [<span data-ttu-id="8abe4-139">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8abe4-139">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="8abe4-140">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="8abe4-140">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="8abe4-141">Tabulka typů hodnot</span><span class="sxs-lookup"><span data-stu-id="8abe4-141">Value Types Table</span></span>](value-types-table.md)  
 [<span data-ttu-id="8abe4-142">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="8abe4-142">Value Types</span></span>](value-types.md)  
 [<span data-ttu-id="8abe4-143">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="8abe4-143">Built-In Types Table</span></span>](built-in-types-table.md)  
 [<span data-ttu-id="8abe4-144">Referenční tabulky pro typy</span><span class="sxs-lookup"><span data-stu-id="8abe4-144">Reference Tables for Types</span></span>](reference-tables-for-types.md)
