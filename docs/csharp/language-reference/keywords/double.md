---
title: Double – klíčové slovo (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- double
- double_CSharpKeyword
helpviewer_keywords:
- double data type [C#]
ms.assetid: 0980e11b-6004-4102-abcf-cfc280fc6991
ms.openlocfilehash: 8e3a94bb79d46f2815e46b86f1aca92acc73e5c2
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027847"
---
# <a name="double-c-reference"></a><span data-ttu-id="01bfa-102">double (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="01bfa-102">double (C# Reference)</span></span>

<span data-ttu-id="01bfa-103">`double` – Klíčové slovo označuje jednoduchý typ, který ukládá 64bitové hodnoty s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="01bfa-103">The `double` keyword signifies a simple type that stores 64-bit floating-point values.</span></span> <span data-ttu-id="01bfa-104">Následující tabulka uvádí přesnost a přibližnou rozsah `double` typu.</span><span class="sxs-lookup"><span data-stu-id="01bfa-104">The following table shows the precision and approximate range for the `double` type.</span></span>

|<span data-ttu-id="01bfa-105">Typ</span><span class="sxs-lookup"><span data-stu-id="01bfa-105">Type</span></span>|<span data-ttu-id="01bfa-106">Přibližná rozsahu</span><span class="sxs-lookup"><span data-stu-id="01bfa-106">Approximate range</span></span>|<span data-ttu-id="01bfa-107">Přesnost</span><span class="sxs-lookup"><span data-stu-id="01bfa-107">Precision</span></span>|<span data-ttu-id="01bfa-108">Typ formátu .NET</span><span class="sxs-lookup"><span data-stu-id="01bfa-108">.NET type</span></span>|
|----------|-----------------------|---------------|-------------------------|
|`double`|<span data-ttu-id="01bfa-109">±5.0 × 10<sup>−324</sup> k ±1.7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="01bfa-109">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="01bfa-110">15 až 16 číslic</span><span class="sxs-lookup"><span data-stu-id="01bfa-110">15-16 digits</span></span>|<xref:System.Double?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="01bfa-111">Literály</span><span class="sxs-lookup"><span data-stu-id="01bfa-111">Literals</span></span>

<span data-ttu-id="01bfa-112">Ve výchozím nastavení, je skutečně číselný literál na pravé straně operátoru přiřazení považován za `double`.</span><span class="sxs-lookup"><span data-stu-id="01bfa-112">By default, a real numeric literal on the right side of the assignment operator is treated as `double`.</span></span> <span data-ttu-id="01bfa-113">Ale pokud budete chtít celé číslo považován za `double`, použít přípona d nebo D, například:</span><span class="sxs-lookup"><span data-stu-id="01bfa-113">However, if you want an integer number to be treated as `double`, use the suffix d or D, for example:</span></span>

```csharp
double x = 3D;
```

## <a name="conversions"></a><span data-ttu-id="01bfa-114">Převody</span><span class="sxs-lookup"><span data-stu-id="01bfa-114">Conversions</span></span>

<span data-ttu-id="01bfa-115">Je možné kombinovat číselné integrální typy a typy s plovoucí desetinnou čárkou ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="01bfa-115">You can mix numeric integral types and floating-point types in an expression.</span></span> <span data-ttu-id="01bfa-116">Celočíselné typy v tomto případě se převedou na typy s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="01bfa-116">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="01bfa-117">Vyhodnocení výrazu se provádí podle následujících pravidel:</span><span class="sxs-lookup"><span data-stu-id="01bfa-117">The evaluation of the expression is performed according to the following rules:</span></span>

- <span data-ttu-id="01bfa-118">Pokud jeden z typů s plovoucí desetinnou čárkou je `double`, výsledkem výrazu `double`, nebo [bool](../../../csharp/language-reference/keywords/bool.md) ve výrazech relační nebo logická hodnota.</span><span class="sxs-lookup"><span data-stu-id="01bfa-118">If one of the floating-point types is `double`, the expression evaluates to `double`, or [bool](../../../csharp/language-reference/keywords/bool.md) in relational or Boolean expressions.</span></span>

- <span data-ttu-id="01bfa-119">Pokud je žádné `double` typ výrazu, vyhodnotí k [float](../../../csharp/language-reference/keywords/float.md), nebo [bool](../../../csharp/language-reference/keywords/bool.md) ve výrazech relační nebo logická hodnota.</span><span class="sxs-lookup"><span data-stu-id="01bfa-119">If there is no `double` type in the expression, it evaluates to [float](../../../csharp/language-reference/keywords/float.md), or [bool](../../../csharp/language-reference/keywords/bool.md) in relational or Boolean expressions.</span></span>

 <span data-ttu-id="01bfa-120">Výraz s plovoucí desetinnou čárkou mohou obsahovat následující sady hodnot:</span><span class="sxs-lookup"><span data-stu-id="01bfa-120">A floating-point expression can contain the following sets of values:</span></span>

- <span data-ttu-id="01bfa-121">Kladné a záporné nuly.</span><span class="sxs-lookup"><span data-stu-id="01bfa-121">Positive and negative zero.</span></span>

- <span data-ttu-id="01bfa-122">Kladné a záporné nekonečno.</span><span class="sxs-lookup"><span data-stu-id="01bfa-122">Positive and negative infinity.</span></span>

- <span data-ttu-id="01bfa-123">Hodnota not-a-Number (NaN).</span><span class="sxs-lookup"><span data-stu-id="01bfa-123">Not-a-Number value (NaN).</span></span>

- <span data-ttu-id="01bfa-124">Omezená sada nenulové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="01bfa-124">The finite set of nonzero values.</span></span>

<span data-ttu-id="01bfa-125">Další informace o těchto hodnotách naleznete v tématu Standard IEEE pro binární aritmetiku, k dispozici na [IEEE](https://www.ieee.org) webu.</span><span class="sxs-lookup"><span data-stu-id="01bfa-125">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](https://www.ieee.org) Web site.</span></span>

## <a name="example"></a><span data-ttu-id="01bfa-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="01bfa-126">Example</span></span>

<span data-ttu-id="01bfa-127">V následujícím příkladu se [int](../../../csharp/language-reference/keywords/int.md), [krátké](../../../csharp/language-reference/keywords/short.md), [float](../../../csharp/language-reference/keywords/float.md)a `double` přidají dohromady `double` výsledek.</span><span class="sxs-lookup"><span data-stu-id="01bfa-127">In the following example, an [int](../../../csharp/language-reference/keywords/int.md), a [short](../../../csharp/language-reference/keywords/short.md), a [float](../../../csharp/language-reference/keywords/float.md), and a `double` are added together giving a `double` result.</span></span>

[!code-csharp[csrefKeywordsTypes#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="01bfa-128">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="01bfa-128">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="01bfa-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="01bfa-129">See Also</span></span>

[<span data-ttu-id="01bfa-130">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="01bfa-130">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
[<span data-ttu-id="01bfa-131">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="01bfa-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
[<span data-ttu-id="01bfa-132">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="01bfa-132">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
[<span data-ttu-id="01bfa-133">Tabulka výchozích hodnot</span><span class="sxs-lookup"><span data-stu-id="01bfa-133">Default Values Table</span></span>](../../../csharp/language-reference/keywords/default-values-table.md)  
[<span data-ttu-id="01bfa-134">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="01bfa-134">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
[<span data-ttu-id="01bfa-135">Tabulka typů s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="01bfa-135">Floating-Point Types Table</span></span>](../../../csharp/language-reference/keywords/floating-point-types-table.md)  
[<span data-ttu-id="01bfa-136">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="01bfa-136">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
[<span data-ttu-id="01bfa-137">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="01bfa-137">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
