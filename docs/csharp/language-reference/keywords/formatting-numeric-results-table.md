---
title: Tabulka formátování číselných výsledků – C# odkaz
ms.custom: seodec18
description: Další informace o řetězcích standardního číselného formátu jazyka C#
ms.date: 09/20/2018
helpviewer_keywords:
- formatting [C#]
- numeric formatting [C#]
- String.Format method
ms.assetid: 120ba537-4448-4c62-8676-7a8fdd98f496
ms.openlocfilehash: 12fe89e3aa63e9d3d8c3f102fe5a01a5f2225375
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661552"
---
# <a name="formatting-numeric-results-table-c-reference"></a><span data-ttu-id="dbbd2-103">Tabulka formátování číselných výsledků (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="dbbd2-103">Formatting numeric results table (C# Reference)</span></span>

<span data-ttu-id="dbbd2-104">Následující tabulka uvádí podporované specifikátorů pro formátování číselných výsledků.</span><span class="sxs-lookup"><span data-stu-id="dbbd2-104">The following table shows supported format specifiers for formatting numeric results.</span></span> <span data-ttu-id="dbbd2-105">Formátovaný výsledek v posledním sloupci odpovídá "en US" <xref:System.Globalization.CultureInfo>.</span><span class="sxs-lookup"><span data-stu-id="dbbd2-105">The formatted result in the last column corresponds to the "en-US" <xref:System.Globalization.CultureInfo>.</span></span>

|<span data-ttu-id="dbbd2-106">Specifikátor formátu</span><span class="sxs-lookup"><span data-stu-id="dbbd2-106">Format specifier</span></span>|<span data-ttu-id="dbbd2-107">Popis</span><span class="sxs-lookup"><span data-stu-id="dbbd2-107">Description</span></span>|<span data-ttu-id="dbbd2-108">Příklady</span><span class="sxs-lookup"><span data-stu-id="dbbd2-108">Examples</span></span>|<span data-ttu-id="dbbd2-109">Výsledek</span><span class="sxs-lookup"><span data-stu-id="dbbd2-109">Result</span></span>|  
|----------------------|-----------------|--------------|------------|  
|<span data-ttu-id="dbbd2-110">C nebo c</span><span class="sxs-lookup"><span data-stu-id="dbbd2-110">C or c</span></span>|<span data-ttu-id="dbbd2-111">Měna</span><span class="sxs-lookup"><span data-stu-id="dbbd2-111">Currency</span></span>|`string s = $"{2.5:C}";`<br /><br /> `string s = $"{-2.5:C}";`|<span data-ttu-id="dbbd2-112">$2.50</span><span class="sxs-lookup"><span data-stu-id="dbbd2-112">$2.50</span></span><br /><br /> <span data-ttu-id="dbbd2-113">($2.50)</span><span class="sxs-lookup"><span data-stu-id="dbbd2-113">($2.50)</span></span>|  
|<span data-ttu-id="dbbd2-114">D nebo d</span><span class="sxs-lookup"><span data-stu-id="dbbd2-114">D or d</span></span>|<span data-ttu-id="dbbd2-115">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="dbbd2-115">Decimal</span></span>|`string s = $"{25:D5}";`|<span data-ttu-id="dbbd2-116">00025</span><span class="sxs-lookup"><span data-stu-id="dbbd2-116">00025</span></span>|  
|<span data-ttu-id="dbbd2-117">E nebo e</span><span class="sxs-lookup"><span data-stu-id="dbbd2-117">E or e</span></span>|<span data-ttu-id="dbbd2-118">Exponenciální</span><span class="sxs-lookup"><span data-stu-id="dbbd2-118">Exponential</span></span>|`string s = $"{250000:E2}";`|<span data-ttu-id="dbbd2-119">2.50E + 005</span><span class="sxs-lookup"><span data-stu-id="dbbd2-119">2.50E+005</span></span>|  
|<span data-ttu-id="dbbd2-120">F nebo f</span><span class="sxs-lookup"><span data-stu-id="dbbd2-120">F or f</span></span>|<span data-ttu-id="dbbd2-121">Pevná desetinná čárka</span><span class="sxs-lookup"><span data-stu-id="dbbd2-121">Fixed-point</span></span>|`string s = $"{2.5:F2}";`<br /><br /> `string s = $"{2.5:F0}";`|<span data-ttu-id="dbbd2-122">2.50</span><span class="sxs-lookup"><span data-stu-id="dbbd2-122">2.50</span></span><br /><br /> <span data-ttu-id="dbbd2-123">3</span><span class="sxs-lookup"><span data-stu-id="dbbd2-123">3</span></span>|  
|<span data-ttu-id="dbbd2-124">G nebo g</span><span class="sxs-lookup"><span data-stu-id="dbbd2-124">G or g</span></span>|<span data-ttu-id="dbbd2-125">Obecné</span><span class="sxs-lookup"><span data-stu-id="dbbd2-125">General</span></span>|`string s = $"{2.5:G}";`|<span data-ttu-id="dbbd2-126">2.5</span><span class="sxs-lookup"><span data-stu-id="dbbd2-126">2.5</span></span>|  
|<span data-ttu-id="dbbd2-127">N nebo n</span><span class="sxs-lookup"><span data-stu-id="dbbd2-127">N or n</span></span>|<span data-ttu-id="dbbd2-128">Numeric</span><span class="sxs-lookup"><span data-stu-id="dbbd2-128">Numeric</span></span>|`string s = $"{2500000:N}";`|<span data-ttu-id="dbbd2-129">2,500,000.00</span><span class="sxs-lookup"><span data-stu-id="dbbd2-129">2,500,000.00</span></span>|  
|<span data-ttu-id="dbbd2-130">P nebo p</span><span class="sxs-lookup"><span data-stu-id="dbbd2-130">P or p</span></span>|<span data-ttu-id="dbbd2-131">Procento</span><span class="sxs-lookup"><span data-stu-id="dbbd2-131">Percent</span></span>|`string s = $"{0.25:P}";`|<span data-ttu-id="dbbd2-132">25.00%</span><span class="sxs-lookup"><span data-stu-id="dbbd2-132">25.00%</span></span>|  
|<span data-ttu-id="dbbd2-133">R nebo r</span><span class="sxs-lookup"><span data-stu-id="dbbd2-133">R or r</span></span>|<span data-ttu-id="dbbd2-134">Zpáteční převod</span><span class="sxs-lookup"><span data-stu-id="dbbd2-134">Round-trip</span></span>|`string s = $"{2.5:R}";`|<span data-ttu-id="dbbd2-135">2.5</span><span class="sxs-lookup"><span data-stu-id="dbbd2-135">2.5</span></span>|  
|<span data-ttu-id="dbbd2-136">X or x</span><span class="sxs-lookup"><span data-stu-id="dbbd2-136">X or x</span></span>|<span data-ttu-id="dbbd2-137">Šestnáctková hodnota</span><span class="sxs-lookup"><span data-stu-id="dbbd2-137">Hexadecimal</span></span>|`string s = $"{250:X}";`<br /><br /> `string s = $"{0xffff:X}";`|<span data-ttu-id="dbbd2-138">FA</span><span class="sxs-lookup"><span data-stu-id="dbbd2-138">FA</span></span><br /><br /> <span data-ttu-id="dbbd2-139">FFFF</span><span class="sxs-lookup"><span data-stu-id="dbbd2-139">FFFF</span></span>|  

## <a name="remarks"></a><span data-ttu-id="dbbd2-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dbbd2-140">Remarks</span></span>

<span data-ttu-id="dbbd2-141">Použití specifikátoru formátu pro vytvoření řetězce formátu.</span><span class="sxs-lookup"><span data-stu-id="dbbd2-141">You use a format specifier to create a format string.</span></span> <span data-ttu-id="dbbd2-142">Formátovací řetězec má následující formát: `Axx`, kde</span><span class="sxs-lookup"><span data-stu-id="dbbd2-142">The format string is of the following form: `Axx`, where</span></span>

- <span data-ttu-id="dbbd2-143">`A` je specifikátor formátu, který určuje typ formátování použité pro číselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="dbbd2-143">`A` is the format specifier, which controls the type of formatting applied to the numeric value.</span></span>
- <span data-ttu-id="dbbd2-144">`xx` je specifikátor přesnosti, který ovlivňuje počet číslic v formátovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="dbbd2-144">`xx` is the precision specifier, which affects the number of digits in the formatted output.</span></span> <span data-ttu-id="dbbd2-145">Hodnota rozsahy specifikátor přesnosti od 0 do 99.</span><span class="sxs-lookup"><span data-stu-id="dbbd2-145">The value of the precision specifier ranges from 0 to 99.</span></span>

<span data-ttu-id="dbbd2-146">Desetinné číslo ("D" nebo "d") a šestnáctková ("X" nebo "x") formátu specifikátory jsou podporována pouze pro integrální typy.</span><span class="sxs-lookup"><span data-stu-id="dbbd2-146">The decimal ("D" or "d") and hexadecimal ("X" or "x") format specifiers are supported only for integral types.</span></span> <span data-ttu-id="dbbd2-147">Operace round-trip specifikátor formátu ("R" nebo "r") je podporován pouze pro <xref:System.Single>, <xref:System.Double>, a <xref:System.Numerics.BigInteger> typy.</span><span class="sxs-lookup"><span data-stu-id="dbbd2-147">The round-trip ("R" or "r") format specifier is supported only for <xref:System.Single>, <xref:System.Double>, and <xref:System.Numerics.BigInteger> types.</span></span>

<span data-ttu-id="dbbd2-148">Řetězce standardního číselného formátu jsou podporovány:</span><span class="sxs-lookup"><span data-stu-id="dbbd2-148">Standard numeric format strings are supported by:</span></span>

- <span data-ttu-id="dbbd2-149">Některá přetížení `ToString` metoda všechny číselné typy.</span><span class="sxs-lookup"><span data-stu-id="dbbd2-149">Some overloads of the `ToString` method of all numeric types.</span></span> <span data-ttu-id="dbbd2-150">Například můžete zadat číselný formátovací řetězec <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> a <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="dbbd2-150">For example, you can supply a numeric format string to the <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> and <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> methods.</span></span>

- <span data-ttu-id="dbbd2-151">.NET [funkci složeného formátování](../../../standard/base-types/composite-formatting.md), která je podporována <xref:System.String.Format%2A?displayProperty=nameWithType> metody, například.</span><span class="sxs-lookup"><span data-stu-id="dbbd2-151">The .NET [composite formatting feature](../../../standard/base-types/composite-formatting.md), which is supported by the <xref:System.String.Format%2A?displayProperty=nameWithType> method, for example.</span></span>

- <span data-ttu-id="dbbd2-152">[Interpolované řetězce](../tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="dbbd2-152">[Interpolated strings](../tokens/interpolated.md).</span></span>

<span data-ttu-id="dbbd2-153">Další informace najdete v tématu [Standard Numeric Format Strings](../../../standard/base-types/standard-numeric-format-strings.md).</span><span class="sxs-lookup"><span data-stu-id="dbbd2-153">For more information, see [Standard Numeric Format Strings](../../../standard/base-types/standard-numeric-format-strings.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dbbd2-154">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dbbd2-154">See also</span></span>

- [<span data-ttu-id="dbbd2-155">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="dbbd2-155">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="dbbd2-156">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="dbbd2-156">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="dbbd2-157">Referenční tabulky pro typy</span><span class="sxs-lookup"><span data-stu-id="dbbd2-157">Reference tables for types</span></span>](reference-tables-for-types.md)
- [<span data-ttu-id="dbbd2-158">Typy formátování</span><span class="sxs-lookup"><span data-stu-id="dbbd2-158">Formatting types</span></span>](../../../standard/base-types/formatting-types.md)
- [<span data-ttu-id="dbbd2-159">Složené formátování</span><span class="sxs-lookup"><span data-stu-id="dbbd2-159">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)
- [<span data-ttu-id="dbbd2-160">Interpolace řetězců</span><span class="sxs-lookup"><span data-stu-id="dbbd2-160">String interpolation</span></span>](../tokens/interpolated.md)
- [<span data-ttu-id="dbbd2-161">string</span><span class="sxs-lookup"><span data-stu-id="dbbd2-161">string</span></span>](string.md)
