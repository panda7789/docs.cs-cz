---
title: "Tabulka celočíselných typů (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- integral types, C#
- Visual C#, integral types
- types [C#], integral types
- ranges of integral types [C#]
ms.assetid: 62e86126-46ff-40b0-9028-e61d7558268c
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 663ea9a64284c25999564eca9ea5ccec861e9662
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="integral-types-table-c-reference"></a><span data-ttu-id="c5715-102">Tabulka celočíselných typů (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="c5715-102">Integral Types Table (C# Reference)</span></span>
<span data-ttu-id="c5715-103">V následující tabulce jsou uvedeny velikosti a rozsah celočíselných typů, které tvoří podmnožinu jednoduchých typů.</span><span class="sxs-lookup"><span data-stu-id="c5715-103">The following table shows the sizes and ranges of the integral types, which constitute a subset of simple types.</span></span>  
  
|<span data-ttu-id="c5715-104">Typ</span><span class="sxs-lookup"><span data-stu-id="c5715-104">Type</span></span>|<span data-ttu-id="c5715-105">Rozsah</span><span class="sxs-lookup"><span data-stu-id="c5715-105">Range</span></span>|<span data-ttu-id="c5715-106">Velikost</span><span class="sxs-lookup"><span data-stu-id="c5715-106">Size</span></span>|  
|----------|-----------|----------|  
|[<span data-ttu-id="c5715-107">SByte –</span><span class="sxs-lookup"><span data-stu-id="c5715-107">sbyte</span></span>](../../../csharp/language-reference/keywords/sbyte.md)|<span data-ttu-id="c5715-108">-128 až 127</span><span class="sxs-lookup"><span data-stu-id="c5715-108">-128 to 127</span></span>|<span data-ttu-id="c5715-109">8bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="c5715-109">Signed 8-bit integer</span></span>|  
|[<span data-ttu-id="c5715-110">bajtů</span><span class="sxs-lookup"><span data-stu-id="c5715-110">byte</span></span>](../../../csharp/language-reference/keywords/byte.md)|<span data-ttu-id="c5715-111">0 až 255</span><span class="sxs-lookup"><span data-stu-id="c5715-111">0 to 255</span></span>|<span data-ttu-id="c5715-112">Nepodepsané 8bitové celé číslo</span><span class="sxs-lookup"><span data-stu-id="c5715-112">Unsigned 8-bit integer</span></span>|  
|[<span data-ttu-id="c5715-113">Char</span><span class="sxs-lookup"><span data-stu-id="c5715-113">char</span></span>](../../../csharp/language-reference/keywords/char.md)|<span data-ttu-id="c5715-114">U + 0000 U + ffff</span><span class="sxs-lookup"><span data-stu-id="c5715-114">U+0000 to U+ffff</span></span>|<span data-ttu-id="c5715-115">16bitové znak Unicode</span><span class="sxs-lookup"><span data-stu-id="c5715-115">Unicode 16-bit character</span></span>|  
|[<span data-ttu-id="c5715-116">krátký</span><span class="sxs-lookup"><span data-stu-id="c5715-116">short</span></span>](../../../csharp/language-reference/keywords/short.md)|<span data-ttu-id="c5715-117">-32 768 do 32 767</span><span class="sxs-lookup"><span data-stu-id="c5715-117">-32,768 to 32,767</span></span>|<span data-ttu-id="c5715-118">16bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="c5715-118">Signed 16-bit integer</span></span>|  
|[<span data-ttu-id="c5715-119">ushort –</span><span class="sxs-lookup"><span data-stu-id="c5715-119">ushort</span></span>](../../../csharp/language-reference/keywords/ushort.md)|<span data-ttu-id="c5715-120">0 až 65 535</span><span class="sxs-lookup"><span data-stu-id="c5715-120">0 to 65,535</span></span>|<span data-ttu-id="c5715-121">Nepodepsané 16bitové celé číslo</span><span class="sxs-lookup"><span data-stu-id="c5715-121">Unsigned 16-bit integer</span></span>|  
|[<span data-ttu-id="c5715-122">celá čísla</span><span class="sxs-lookup"><span data-stu-id="c5715-122">int</span></span>](../../../csharp/language-reference/keywords/int.md)|<span data-ttu-id="c5715-123">-2 147 483 648 na 2 147 483 647</span><span class="sxs-lookup"><span data-stu-id="c5715-123">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="c5715-124">32bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="c5715-124">Signed 32-bit integer</span></span>|  
|[<span data-ttu-id="c5715-125">uint</span><span class="sxs-lookup"><span data-stu-id="c5715-125">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)|<span data-ttu-id="c5715-126">0 do 4 294 967 295</span><span class="sxs-lookup"><span data-stu-id="c5715-126">0 to 4,294,967,295</span></span>|<span data-ttu-id="c5715-127">Celé číslo bez znaménka 32-bit</span><span class="sxs-lookup"><span data-stu-id="c5715-127">Unsigned 32-bit integer</span></span>|  
|[<span data-ttu-id="c5715-128">dlouhá</span><span class="sxs-lookup"><span data-stu-id="c5715-128">long</span></span>](../../../csharp/language-reference/keywords/long.md)|<span data-ttu-id="c5715-129">-9,223,372,036,854,775,808 k 9,223,372,036,854,775,807</span><span class="sxs-lookup"><span data-stu-id="c5715-129">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="c5715-130">64bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="c5715-130">Signed 64-bit integer</span></span>|  
|[<span data-ttu-id="c5715-131">ulong –</span><span class="sxs-lookup"><span data-stu-id="c5715-131">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md)|<span data-ttu-id="c5715-132">0 – 18,446,744,073,709,551,615</span><span class="sxs-lookup"><span data-stu-id="c5715-132">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="c5715-133">Celé číslo bez znaménka 64-bit</span><span class="sxs-lookup"><span data-stu-id="c5715-133">Unsigned 64-bit integer</span></span>|  
  
 <span data-ttu-id="c5715-134">Pokud hodnota reprezentována celé literálu překračuje rozsah `ulong`, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="c5715-134">If the value represented by an integer literal exceeds the range of `ulong`, a compilation error will occur.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5715-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="c5715-135">See Also</span></span>  
 [<span data-ttu-id="c5715-136">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c5715-136">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c5715-137">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="c5715-137">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c5715-138">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c5715-138">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="c5715-139">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="c5715-139">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="c5715-140">Tabulka typů s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="c5715-140">Floating-Point Types Table</span></span>](../../../csharp/language-reference/keywords/floating-point-types-table.md)  
 [<span data-ttu-id="c5715-141">Tabulka výchozích hodnot</span><span class="sxs-lookup"><span data-stu-id="c5715-141">Default Values Table</span></span>](../../../csharp/language-reference/keywords/default-values-table.md)  
 [<span data-ttu-id="c5715-142">Tabulka formátování číselných výsledků</span><span class="sxs-lookup"><span data-stu-id="c5715-142">Formatting Numeric Results Table</span></span>](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)  
 [<span data-ttu-id="c5715-143">Referenční tabulky pro typy</span><span class="sxs-lookup"><span data-stu-id="c5715-143">Reference Tables for Types</span></span>](../../../csharp/language-reference/keywords/reference-tables-for-types.md)
