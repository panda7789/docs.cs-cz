---
title: Formátování číselných výsledků tabulky C# – referenční informace
ms.custom: seodec18
description: Informace o C# standardních řetězcích číselného formátu
ms.date: 09/20/2018
helpviewer_keywords:
- formatting [C#]
- numeric formatting [C#]
- String.Format method
ms.assetid: 120ba537-4448-4c62-8676-7a8fdd98f496
ms.openlocfilehash: 853faf481e546f2980d799d5daf50a14c608c052
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345474"
---
# <a name="formatting-numeric-results-table-c-reference"></a><span data-ttu-id="041bb-103">Tabulka formátování číselných výsledkůC# (referenční)</span><span class="sxs-lookup"><span data-stu-id="041bb-103">Formatting numeric results table (C# Reference)</span></span>

<span data-ttu-id="041bb-104">V následující tabulce jsou uvedeny podporované specifikátory formátu pro formátování číselných výsledků.</span><span class="sxs-lookup"><span data-stu-id="041bb-104">The following table shows supported format specifiers for formatting numeric results.</span></span> <span data-ttu-id="041bb-105">Formátovaný výsledek v posledním sloupci odpovídá <xref:System.Globalization.CultureInfo>"en-US".</span><span class="sxs-lookup"><span data-stu-id="041bb-105">The formatted result in the last column corresponds to the "en-US" <xref:System.Globalization.CultureInfo>.</span></span>

|<span data-ttu-id="041bb-106">Specifikátor formátu</span><span class="sxs-lookup"><span data-stu-id="041bb-106">Format specifier</span></span>|<span data-ttu-id="041bb-107">Popis</span><span class="sxs-lookup"><span data-stu-id="041bb-107">Description</span></span>|<span data-ttu-id="041bb-108">Příklady</span><span class="sxs-lookup"><span data-stu-id="041bb-108">Examples</span></span>|<span data-ttu-id="041bb-109">Výsledek</span><span class="sxs-lookup"><span data-stu-id="041bb-109">Result</span></span>|  
|----------------------|-----------------|--------------|------------|  
|<span data-ttu-id="041bb-110">C nebo c</span><span class="sxs-lookup"><span data-stu-id="041bb-110">C or c</span></span>|<span data-ttu-id="041bb-111">Měna</span><span class="sxs-lookup"><span data-stu-id="041bb-111">Currency</span></span>|`string s = $"{2.5:C}";`<br /><br /> `string s = $"{-2.5:C}";`|<span data-ttu-id="041bb-112">\\$2,50</span><span class="sxs-lookup"><span data-stu-id="041bb-112">\\$2.50</span></span><br /><br /> <span data-ttu-id="041bb-113">(\\$2,50)</span><span class="sxs-lookup"><span data-stu-id="041bb-113">(\\$2.50)</span></span>|  
|<span data-ttu-id="041bb-114">D nebo d</span><span class="sxs-lookup"><span data-stu-id="041bb-114">D or d</span></span>|<span data-ttu-id="041bb-115">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="041bb-115">Decimal</span></span>|`string s = $"{25:D5}";`|<span data-ttu-id="041bb-116">00025</span><span class="sxs-lookup"><span data-stu-id="041bb-116">00025</span></span>|  
|<span data-ttu-id="041bb-117">E nebo e</span><span class="sxs-lookup"><span data-stu-id="041bb-117">E or e</span></span>|<span data-ttu-id="041bb-118">Exponenciální</span><span class="sxs-lookup"><span data-stu-id="041bb-118">Exponential</span></span>|`string s = $"{250000:E2}";`|<span data-ttu-id="041bb-119">2.50 e + 005</span><span class="sxs-lookup"><span data-stu-id="041bb-119">2.50E+005</span></span>|  
|<span data-ttu-id="041bb-120">F nebo f</span><span class="sxs-lookup"><span data-stu-id="041bb-120">F or f</span></span>|<span data-ttu-id="041bb-121">Pevná desetinná čárka</span><span class="sxs-lookup"><span data-stu-id="041bb-121">Fixed-point</span></span>|`string s = $"{2.5:F2}";`<br /><br /> `string s = $"{2.5:F0}";`|<span data-ttu-id="041bb-122">2,50</span><span class="sxs-lookup"><span data-stu-id="041bb-122">2.50</span></span><br /><br /> <span data-ttu-id="041bb-123">3</span><span class="sxs-lookup"><span data-stu-id="041bb-123">3</span></span>|  
|<span data-ttu-id="041bb-124">G nebo g</span><span class="sxs-lookup"><span data-stu-id="041bb-124">G or g</span></span>|<span data-ttu-id="041bb-125">Obecné</span><span class="sxs-lookup"><span data-stu-id="041bb-125">General</span></span>|`string s = $"{2.5:G}";`|<span data-ttu-id="041bb-126">2,5</span><span class="sxs-lookup"><span data-stu-id="041bb-126">2.5</span></span>|  
|<span data-ttu-id="041bb-127">N nebo n</span><span class="sxs-lookup"><span data-stu-id="041bb-127">N or n</span></span>|<span data-ttu-id="041bb-128">Čísla</span><span class="sxs-lookup"><span data-stu-id="041bb-128">Numeric</span></span>|`string s = $"{2500000:N}";`|<span data-ttu-id="041bb-129">2,500,000.00</span><span class="sxs-lookup"><span data-stu-id="041bb-129">2,500,000.00</span></span>|  
|<span data-ttu-id="041bb-130">P nebo p</span><span class="sxs-lookup"><span data-stu-id="041bb-130">P or p</span></span>|<span data-ttu-id="041bb-131">Procento</span><span class="sxs-lookup"><span data-stu-id="041bb-131">Percent</span></span>|`string s = $"{0.25:P}";`|<span data-ttu-id="041bb-132">25,00 %</span><span class="sxs-lookup"><span data-stu-id="041bb-132">25.00%</span></span>|  
|<span data-ttu-id="041bb-133">R nebo r</span><span class="sxs-lookup"><span data-stu-id="041bb-133">R or r</span></span>|<span data-ttu-id="041bb-134">Zpáteční převod</span><span class="sxs-lookup"><span data-stu-id="041bb-134">Round-trip</span></span>|`string s = $"{2.5:R}";`|<span data-ttu-id="041bb-135">2,5</span><span class="sxs-lookup"><span data-stu-id="041bb-135">2.5</span></span>|  
|<span data-ttu-id="041bb-136">X nebo x</span><span class="sxs-lookup"><span data-stu-id="041bb-136">X or x</span></span>|<span data-ttu-id="041bb-137">Šestnáctková hodnota</span><span class="sxs-lookup"><span data-stu-id="041bb-137">Hexadecimal</span></span>|`string s = $"{250:X}";`<br /><br /> `string s = $"{0xffff:X}";`|<span data-ttu-id="041bb-138">FA</span><span class="sxs-lookup"><span data-stu-id="041bb-138">FA</span></span><br /><br /> <span data-ttu-id="041bb-139">FFFF</span><span class="sxs-lookup"><span data-stu-id="041bb-139">FFFF</span></span>|  

## <a name="remarks"></a><span data-ttu-id="041bb-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="041bb-140">Remarks</span></span>

<span data-ttu-id="041bb-141">Použijete specifikátor formátu pro vytvoření formátovacího řetězce.</span><span class="sxs-lookup"><span data-stu-id="041bb-141">You use a format specifier to create a format string.</span></span> <span data-ttu-id="041bb-142">Formátovací řetězec má následující tvar: `Axx`, kde</span><span class="sxs-lookup"><span data-stu-id="041bb-142">The format string is of the following form: `Axx`, where</span></span>

- <span data-ttu-id="041bb-143">`A` je specifikátor formátu, který řídí typ formátování použité pro číselnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="041bb-143">`A` is the format specifier, which controls the type of formatting applied to the numeric value.</span></span>
- <span data-ttu-id="041bb-144">`xx` je specifikátor přesnosti, který má vliv na počet číslic ve formátovaných výstupech.</span><span class="sxs-lookup"><span data-stu-id="041bb-144">`xx` is the precision specifier, which affects the number of digits in the formatted output.</span></span> <span data-ttu-id="041bb-145">Hodnota specifikátoru přesnosti rozsahu od 0 do 99.</span><span class="sxs-lookup"><span data-stu-id="041bb-145">The value of the precision specifier ranges from 0 to 99.</span></span>

<span data-ttu-id="041bb-146">Specifikátory desítkového formátu ("D" nebo "d") a šestnáctkové hodnoty ("X" nebo "x") jsou podporovány pouze pro integrální typy.</span><span class="sxs-lookup"><span data-stu-id="041bb-146">The decimal ("D" or "d") and hexadecimal ("X" or "x") format specifiers are supported only for integral types.</span></span> <span data-ttu-id="041bb-147">Specifikátor formátu Round-Trip ("R" nebo "r") je podporován pouze pro typy <xref:System.Single>, <xref:System.Double>a <xref:System.Numerics.BigInteger>.</span><span class="sxs-lookup"><span data-stu-id="041bb-147">The round-trip ("R" or "r") format specifier is supported only for <xref:System.Single>, <xref:System.Double>, and <xref:System.Numerics.BigInteger> types.</span></span>

<span data-ttu-id="041bb-148">Standardní řetězce číselného formátu jsou podporovány v:</span><span class="sxs-lookup"><span data-stu-id="041bb-148">Standard numeric format strings are supported by:</span></span>

- <span data-ttu-id="041bb-149">Některá přetížení metody `ToString` pro všechny číselné typy.</span><span class="sxs-lookup"><span data-stu-id="041bb-149">Some overloads of the `ToString` method of all numeric types.</span></span> <span data-ttu-id="041bb-150">Můžete například zadejte řetězec číselného formátu do <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> a <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="041bb-150">For example, you can supply a numeric format string to the <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> and <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> methods.</span></span>

- <span data-ttu-id="041bb-151">[Funkce složeného formátování](../../../standard/base-types/composite-formatting.md).NET, která je podporována metodou <xref:System.String.Format%2A?displayProperty=nameWithType>, například.</span><span class="sxs-lookup"><span data-stu-id="041bb-151">The .NET [composite formatting feature](../../../standard/base-types/composite-formatting.md), which is supported by the <xref:System.String.Format%2A?displayProperty=nameWithType> method, for example.</span></span>

- <span data-ttu-id="041bb-152">[Interpolované řetězce](../tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="041bb-152">[Interpolated strings](../tokens/interpolated.md).</span></span>

<span data-ttu-id="041bb-153">Další informace naleznete v tématu [Standardní číselné formátovací řetězce](../../../standard/base-types/standard-numeric-format-strings.md).</span><span class="sxs-lookup"><span data-stu-id="041bb-153">For more information, see [Standard Numeric Format Strings](../../../standard/base-types/standard-numeric-format-strings.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="041bb-154">Viz také:</span><span class="sxs-lookup"><span data-stu-id="041bb-154">See also</span></span>

- [<span data-ttu-id="041bb-155">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="041bb-155">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="041bb-156">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="041bb-156">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="041bb-157">Typy formátování</span><span class="sxs-lookup"><span data-stu-id="041bb-157">Formatting types</span></span>](../../../standard/base-types/formatting-types.md)
- [<span data-ttu-id="041bb-158">Složené formátování</span><span class="sxs-lookup"><span data-stu-id="041bb-158">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)
- [<span data-ttu-id="041bb-159">Interpolace řetězců</span><span class="sxs-lookup"><span data-stu-id="041bb-159">String interpolation</span></span>](../tokens/interpolated.md)
- [<span data-ttu-id="041bb-160">string</span><span class="sxs-lookup"><span data-stu-id="041bb-160">string</span></span>](../builtin-types/reference-types.md)
