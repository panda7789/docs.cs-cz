---
title: "float (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- float
- float_CSharpKeyword
helpviewer_keywords:
- float keyword [C#]
- floating-point numbers [C#], float keyword
ms.assetid: 1e77db7b-dedb-48b7-8dd1-b055e96a9258
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 846f132812fe90a285c81a020d440fc846f88b5b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="float-c-reference"></a><span data-ttu-id="390a6-102">float (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="390a6-102">float (C# Reference)</span></span>
<span data-ttu-id="390a6-103">`float` – Klíčové slovo označuje jednoduchý typ, který ukládá 32bitové hodnoty s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="390a6-103">The `float` keyword signifies a simple type that stores 32-bit floating-point values.</span></span> <span data-ttu-id="390a6-104">Následující tabulka uvádí přesnost a přibližnou rozsah `float` typu.</span><span class="sxs-lookup"><span data-stu-id="390a6-104">The following table shows the precision and approximate range for the `float` type.</span></span>  
  
|<span data-ttu-id="390a6-105">Typ</span><span class="sxs-lookup"><span data-stu-id="390a6-105">Type</span></span>|<span data-ttu-id="390a6-106">Přibližná rozsahu</span><span class="sxs-lookup"><span data-stu-id="390a6-106">Approximate range</span></span>|<span data-ttu-id="390a6-107">Přesnost</span><span class="sxs-lookup"><span data-stu-id="390a6-107">Precision</span></span>|<span data-ttu-id="390a6-108">Typ rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="390a6-108">.NET Framework type</span></span>|  
|----------|-----------------------|---------------|-------------------------|  
|`float`|<span data-ttu-id="390a6-109">-3.4 × 10<sup>38</sup>+ 3,4 × 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="390a6-109">-3.4 × 10<sup>38</sup>to +3.4 × 10<sup>38</sup></span></span>|<span data-ttu-id="390a6-110">7 míst</span><span class="sxs-lookup"><span data-stu-id="390a6-110">7 digits</span></span>|<xref:System.Single?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="390a6-111">Literály</span><span class="sxs-lookup"><span data-stu-id="390a6-111">Literals</span></span>  
 <span data-ttu-id="390a6-112">Ve výchozím nastavení, je skutečně číselný literál na pravé straně operátoru přiřazení považován za [dvojité](double.md).</span><span class="sxs-lookup"><span data-stu-id="390a6-112">By default, a real numeric literal on the right side of the assignment operator is treated as [double](double.md).</span></span> <span data-ttu-id="390a6-113">Proto k chybě při inicializaci float proměnné, použijte příponu `f` nebo `F`, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="390a6-113">Therefore, to initialize a float variable, use the suffix `f` or `F`, as in the following example:</span></span>  
  
```csharp
float x = 3.5F;  
```
  
 <span data-ttu-id="390a6-114">Pokud nepoužijete příponou v předchozí deklaraci, zobrazí se chyba kompilace vzhledem k tomu, že se pokoušíte uložit [dvojité](double.md) hodnotu do `float` proměnné.</span><span class="sxs-lookup"><span data-stu-id="390a6-114">If you do not use the suffix in the previous declaration, you will get a compilation error because you are trying to store a [double](double.md) value into a `float` variable.</span></span>  
  
## <a name="conversions"></a><span data-ttu-id="390a6-115">Převody</span><span class="sxs-lookup"><span data-stu-id="390a6-115">Conversions</span></span>  
 <span data-ttu-id="390a6-116">Je možné kombinovat číselné integrální typy a typy s plovoucí desetinnou čárkou ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="390a6-116">You can mix numeric integral types and floating-point types in an expression.</span></span> <span data-ttu-id="390a6-117">Celočíselné typy v tomto případě se převedou na typy s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="390a6-117">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="390a6-118">Vyhodnocení výrazu se provádí podle následujících pravidel:</span><span class="sxs-lookup"><span data-stu-id="390a6-118">The evaluation of the expression is performed according to the following rules:</span></span>  
  
-   <span data-ttu-id="390a6-119">Pokud jeden z typů s plovoucí desetinnou čárkou je [dvojité](double.md), výsledkem výrazu [dvojité](double.md) nebo [bool](bool.md) ve výrazech relační nebo logická hodnota.</span><span class="sxs-lookup"><span data-stu-id="390a6-119">If one of the floating-point types is [double](double.md), the expression evaluates to [double](double.md) or [bool](bool.md) in relational or Boolean expressions.</span></span>  
  
-   <span data-ttu-id="390a6-120">Pokud neexistuje žádné [dvojité](double.md) zadejte výraz výraz vyhodnocen jako `float` nebo [bool](bool.md) ve výrazech relační nebo logická hodnota.</span><span class="sxs-lookup"><span data-stu-id="390a6-120">If there is no [double](double.md) type in the expression, the expression evaluates to `float` or [bool](bool.md) in relational or Boolean expressions.</span></span>  
  
 <span data-ttu-id="390a6-121">Výraz s plovoucí desetinnou čárkou mohou obsahovat následující sady hodnot:</span><span class="sxs-lookup"><span data-stu-id="390a6-121">A floating-point expression can contain the following sets of values:</span></span>  
  
-   <span data-ttu-id="390a6-122">Kladné a záporné nuly</span><span class="sxs-lookup"><span data-stu-id="390a6-122">Positive and negative zero</span></span>  
  
-   <span data-ttu-id="390a6-123">Kladné a záporné infinity</span><span class="sxs-lookup"><span data-stu-id="390a6-123">Positive and negative infinity</span></span>  
  
-   <span data-ttu-id="390a6-124">Hodnota not-a-Number (NaN)</span><span class="sxs-lookup"><span data-stu-id="390a6-124">Not-a-Number value (NaN)</span></span>  
  
-   <span data-ttu-id="390a6-125">Konečné sadu nenulové hodnoty</span><span class="sxs-lookup"><span data-stu-id="390a6-125">The finite set of nonzero values</span></span>  
  
 <span data-ttu-id="390a6-126">Další informace o těchto hodnotách naleznete v tématu Standard IEEE pro binární aritmetiku, k dispozici na [IEEE](http://www.ieee.org) webu.</span><span class="sxs-lookup"><span data-stu-id="390a6-126">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](http://www.ieee.org) Web site.</span></span>  
  
## <a name="example"></a><span data-ttu-id="390a6-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="390a6-127">Example</span></span>  
 <span data-ttu-id="390a6-128">V následujícím příkladu se [int](int.md), [krátké](short.md)a `float` jsou zahrnuty v matematickém výrazu, která poskytuje `float` výsledek.</span><span class="sxs-lookup"><span data-stu-id="390a6-128">In the following example, an [int](int.md), a [short](short.md), and a `float` are included in a mathematical expression giving a `float` result.</span></span> <span data-ttu-id="390a6-129">(Nezapomeňte, že `float` je alias <xref:System.Single?displayProperty=nameWithType> typu.) Všimněte si, že neexistuje žádná [dvojité](double.md) ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="390a6-129">(Remember that `float` is an alias for the <xref:System.Single?displayProperty=nameWithType> type.) Notice that there is no [double](double.md) in the expression.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/float_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="390a6-130">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="390a6-130">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="390a6-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="390a6-131">See Also</span></span>  
 <xref:System.Single>  
 [<span data-ttu-id="390a6-132">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="390a6-132">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="390a6-133">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="390a6-133">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="390a6-134">Přetypování a převody typů</span><span class="sxs-lookup"><span data-stu-id="390a6-134">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [<span data-ttu-id="390a6-135">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="390a6-135">C# Keywords</span></span>](index.md)  
 [<span data-ttu-id="390a6-136">Tabulka celočíselných typů</span><span class="sxs-lookup"><span data-stu-id="390a6-136">Integral Types Table</span></span>](integral-types-table.md)  
 [<span data-ttu-id="390a6-137">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="390a6-137">Built-In Types Table</span></span>](built-in-types-table.md)  
 [<span data-ttu-id="390a6-138">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="390a6-138">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="390a6-139">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="390a6-139">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)
