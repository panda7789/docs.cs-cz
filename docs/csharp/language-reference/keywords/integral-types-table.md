---
title: Tabulka celočíselných typů (referenční dokumentace jazyka C#)
description: Přehled integrované C# integrální typy
ms.date: 08/20/2018
helpviewer_keywords:
- integral types, C#
- Visual C#, integral types
- types [C#], integral types
- ranges of integral types [C#]
ms.assetid: 62e86126-46ff-40b0-9028-e61d7558268c
ms.openlocfilehash: 4ac16d185a52cdb03fcb22f57ebf7506f2fb2745
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467189"
---
# <a name="integral-types-table-c-reference"></a><span data-ttu-id="9e08f-103">Tabulka celočíselných typů (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="9e08f-103">Integral types table (C# Reference)</span></span>

<span data-ttu-id="9e08f-104">V následující tabulce jsou uvedeny velikosti a rozsah celočíselných typů, které představují podmnožinu jednoduchých typů.</span><span class="sxs-lookup"><span data-stu-id="9e08f-104">The following table shows the sizes and ranges of the integral types, which constitute a subset of simple types.</span></span>  
  
|<span data-ttu-id="9e08f-105">Typ</span><span class="sxs-lookup"><span data-stu-id="9e08f-105">Type</span></span>|<span data-ttu-id="9e08f-106">Rozsah</span><span class="sxs-lookup"><span data-stu-id="9e08f-106">Range</span></span>|<span data-ttu-id="9e08f-107">Velikost</span><span class="sxs-lookup"><span data-stu-id="9e08f-107">Size</span></span>|  
|----------|-----------|----------|  
|[<span data-ttu-id="9e08f-108">sbyte</span><span class="sxs-lookup"><span data-stu-id="9e08f-108">sbyte</span></span>](sbyte.md)|<span data-ttu-id="9e08f-109">-128 až 127</span><span class="sxs-lookup"><span data-stu-id="9e08f-109">-128 to 127</span></span>|<span data-ttu-id="9e08f-110">8bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="9e08f-110">Signed 8-bit integer</span></span>|  
|[<span data-ttu-id="9e08f-111">byte</span><span class="sxs-lookup"><span data-stu-id="9e08f-111">byte</span></span>](byte.md)|<span data-ttu-id="9e08f-112">0 až 255</span><span class="sxs-lookup"><span data-stu-id="9e08f-112">0 to 255</span></span>|<span data-ttu-id="9e08f-113">Celé číslo bez znaménka 8 bitů</span><span class="sxs-lookup"><span data-stu-id="9e08f-113">Unsigned 8-bit integer</span></span>|  
|[<span data-ttu-id="9e08f-114">char</span><span class="sxs-lookup"><span data-stu-id="9e08f-114">char</span></span>](char.md)|<span data-ttu-id="9e08f-115">U + 0000 U + ffff</span><span class="sxs-lookup"><span data-stu-id="9e08f-115">U+0000 to U+ffff</span></span>|<span data-ttu-id="9e08f-116">16bitový znak Unicode</span><span class="sxs-lookup"><span data-stu-id="9e08f-116">Unicode 16-bit character</span></span>|  
|[<span data-ttu-id="9e08f-117">short</span><span class="sxs-lookup"><span data-stu-id="9e08f-117">short</span></span>](short.md)|<span data-ttu-id="9e08f-118">-32 768 do 32 767</span><span class="sxs-lookup"><span data-stu-id="9e08f-118">-32,768 to 32,767</span></span>|<span data-ttu-id="9e08f-119">16bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="9e08f-119">Signed 16-bit integer</span></span>|  
|[<span data-ttu-id="9e08f-120">ushort</span><span class="sxs-lookup"><span data-stu-id="9e08f-120">ushort</span></span>](ushort.md)|<span data-ttu-id="9e08f-121">0 až 65 535</span><span class="sxs-lookup"><span data-stu-id="9e08f-121">0 to 65,535</span></span>|<span data-ttu-id="9e08f-122">Celé číslo bez znaménka 16 bitů</span><span class="sxs-lookup"><span data-stu-id="9e08f-122">Unsigned 16-bit integer</span></span>|  
|[<span data-ttu-id="9e08f-123">int</span><span class="sxs-lookup"><span data-stu-id="9e08f-123">int</span></span>](int.md)|<span data-ttu-id="9e08f-124">-2 147 483 648 do 2 147 483 647</span><span class="sxs-lookup"><span data-stu-id="9e08f-124">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="9e08f-125">32bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="9e08f-125">Signed 32-bit integer</span></span>|  
|[<span data-ttu-id="9e08f-126">uint</span><span class="sxs-lookup"><span data-stu-id="9e08f-126">uint</span></span>](uint.md)|<span data-ttu-id="9e08f-127">0 do 4 294 967 295</span><span class="sxs-lookup"><span data-stu-id="9e08f-127">0 to 4,294,967,295</span></span>|<span data-ttu-id="9e08f-128">Nepodepsané 32bitové celé číslo</span><span class="sxs-lookup"><span data-stu-id="9e08f-128">Unsigned 32-bit integer</span></span>|  
|[<span data-ttu-id="9e08f-129">long</span><span class="sxs-lookup"><span data-stu-id="9e08f-129">long</span></span>](long.md)|<span data-ttu-id="9e08f-130">-9,223,372,036,854,775,808 k 9,223,372,036,854,775,807</span><span class="sxs-lookup"><span data-stu-id="9e08f-130">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="9e08f-131">64bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="9e08f-131">Signed 64-bit integer</span></span>|  
|[<span data-ttu-id="9e08f-132">ulong</span><span class="sxs-lookup"><span data-stu-id="9e08f-132">ulong</span></span>](ulong.md)|<span data-ttu-id="9e08f-133">0 na 18,446,744,073,709,551,615</span><span class="sxs-lookup"><span data-stu-id="9e08f-133">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="9e08f-134">64-bit znaménka.</span><span class="sxs-lookup"><span data-stu-id="9e08f-134">Unsigned 64-bit integer</span></span>|  

## <a name="remarks"></a><span data-ttu-id="9e08f-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9e08f-135">Remarks</span></span>
  
<span data-ttu-id="9e08f-136">Pokud se překročí Hodnota reprezentovaná celočíselného literálu <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, chybu kompilátoru [CS1021](../../misc/cs1021.md) vyvolá.</span><span class="sxs-lookup"><span data-stu-id="9e08f-136">If the value represented by an integer literal exceeds <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compiler error [CS1021](../../misc/cs1021.md) occurs.</span></span>

<span data-ttu-id="9e08f-137">Použití <xref:System.Numerics.BigInteger?displayProperty=nameWithType> pro reprezentaci libovolně velké podepsané celé číslo.</span><span class="sxs-lookup"><span data-stu-id="9e08f-137">Use the <xref:System.Numerics.BigInteger?displayProperty=nameWithType> class to represent an arbitrarily large signed integer.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="9e08f-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9e08f-138">See also</span></span>

- [<span data-ttu-id="9e08f-139">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9e08f-139">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9e08f-140">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="9e08f-140">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9e08f-141">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9e08f-141">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="9e08f-142">Referenční tabulky pro typy</span><span class="sxs-lookup"><span data-stu-id="9e08f-142">Reference tables for types</span></span>](reference-tables-for-types.md)
- [<span data-ttu-id="9e08f-143">Tabulka typů s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="9e08f-143">Floating-point types table</span></span>](floating-point-types-table.md)
- [<span data-ttu-id="9e08f-144">Tabulka výchozích hodnot</span><span class="sxs-lookup"><span data-stu-id="9e08f-144">Default values table</span></span>](default-values-table.md)
- [<span data-ttu-id="9e08f-145">Tabulka formátování číselných výsledků</span><span class="sxs-lookup"><span data-stu-id="9e08f-145">Formatting numeric results table</span></span>](formatting-numeric-results-table.md)
- [<span data-ttu-id="9e08f-146">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="9e08f-146">Built-in types table</span></span>](built-in-types-table.md)
