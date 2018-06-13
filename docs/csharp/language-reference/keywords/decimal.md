---
title: decimal (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- decimal_CSharpKeyword
- decimal
helpviewer_keywords:
- decimal keyword [C#]
ms.assetid: b6522132-b5ee-4be3-ad13-3adfdb7de7a1
ms.openlocfilehash: 590bd3c6347271f9c4e2c6fd6223db608e010b69
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33219333"
---
# <a name="decimal-c-reference"></a><span data-ttu-id="d848d-102">decimal (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d848d-102">decimal (C# Reference)</span></span>
<span data-ttu-id="d848d-103">`decimal` – Klíčové slovo označuje typ dat 128-bit.</span><span class="sxs-lookup"><span data-stu-id="d848d-103">The `decimal` keyword indicates a 128-bit data type.</span></span> <span data-ttu-id="d848d-104">Porovnání na jiné typy s plovoucí desetinnou čárkou `decimal` typ má více přesnost i s menším rozsahem, takže je vhodné pro finanční a peněžní výpočty.</span><span class="sxs-lookup"><span data-stu-id="d848d-104">Compared to other floating-point types, the `decimal` type has more precision and a smaller range, which makes it appropriate for financial and monetary calculations.</span></span> <span data-ttu-id="d848d-105">Přibližná rozsah a přesnost pro `decimal` typu jsou uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="d848d-105">The approximate range and precision for the `decimal` type are shown in the following table.</span></span>  
  
|<span data-ttu-id="d848d-106">Typ</span><span class="sxs-lookup"><span data-stu-id="d848d-106">Type</span></span>|<span data-ttu-id="d848d-107">Přibližný rozsah</span><span class="sxs-lookup"><span data-stu-id="d848d-107">Approximate Range</span></span>|<span data-ttu-id="d848d-108">Přesnost</span><span class="sxs-lookup"><span data-stu-id="d848d-108">Precision</span></span>|<span data-ttu-id="d848d-109">Typ rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d848d-109">.NET Framework type</span></span>|  
|----------|-----------------------|---------------|-------------------------|  
|`decimal`|<span data-ttu-id="d848d-110">(-7.9 × 10<sup>28</sup> 7.9 × 10<sup>28</sup>) / (10<sup>0</sup> na 10<sup>28</sup>)</span><span class="sxs-lookup"><span data-stu-id="d848d-110">(-7.9 x 10<sup>28</sup> to 7.9 x 10<sup>28</sup>) / (10<sup>0</sup> to 10<sup>28</sup>)</span></span>|<span data-ttu-id="d848d-111">28–29 významných číslic</span><span class="sxs-lookup"><span data-stu-id="d848d-111">28-29 significant digits</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|  

<span data-ttu-id="d848d-112">Výchozí hodnota `decimal` je 0 m.</span><span class="sxs-lookup"><span data-stu-id="d848d-112">The default value of a `decimal` is 0m.</span></span>
  
## <a name="literals"></a><span data-ttu-id="d848d-113">Literály</span><span class="sxs-lookup"><span data-stu-id="d848d-113">Literals</span></span>  
 <span data-ttu-id="d848d-114">Pokud chcete, aby číselný literál skutečné považován za `decimal`, použít příponu m nebo M, například:</span><span class="sxs-lookup"><span data-stu-id="d848d-114">If you want a numeric real literal to be treated as `decimal`, use the suffix m or M, for example:</span></span>  
  
```csharp
decimal myMoney = 300.5m;  
```  
  
 <span data-ttu-id="d848d-115">Bez přípony m číslo považován za [dvojité](../../../csharp/language-reference/keywords/double.md) a vygeneruje chyby kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="d848d-115">Without the suffix m, the number is treated as a [double](../../../csharp/language-reference/keywords/double.md) and generates a compiler error.</span></span>  
  
## <a name="conversions"></a><span data-ttu-id="d848d-116">Převody</span><span class="sxs-lookup"><span data-stu-id="d848d-116">Conversions</span></span>  
 <span data-ttu-id="d848d-117">Celočíselné typy jsou implicitně převést na `decimal` a vyhodnotí jako výsledek `decimal`.</span><span class="sxs-lookup"><span data-stu-id="d848d-117">The integral types are implicitly converted to `decimal` and the result evaluates to `decimal`.</span></span> <span data-ttu-id="d848d-118">Z tohoto důvodu můžete inicializovat proměnnou desítkového čísla pomocí celočíselného literálu bez přípony, a to následovně:</span><span class="sxs-lookup"><span data-stu-id="d848d-118">Therefore you can initialize a decimal variable using an integer literal, without the suffix, as follows:</span></span>  
  
```csharp
decimal myMoney = 300;  
```  
  
 <span data-ttu-id="d848d-119">Neexistuje žádný implicitní převod mezi jiné typy s plovoucí desetinnou čárkou a `decimal` typ; proto přetypování použije pro převod mezi těmito dvěma typy.</span><span class="sxs-lookup"><span data-stu-id="d848d-119">There is no implicit conversion between other floating-point types and the `decimal` type; therefore, a cast must be used to convert between these two types.</span></span> <span data-ttu-id="d848d-120">Příklad:</span><span class="sxs-lookup"><span data-stu-id="d848d-120">For example:</span></span>  
  
```csharp
decimal myMoney = 99.9m;  
double x = (double)myMoney;  
myMoney = (decimal)x;  
```  
  
 <span data-ttu-id="d848d-121">Můžete také kombinovat `decimal` a číselnými integrální typy ve stejném výrazu.</span><span class="sxs-lookup"><span data-stu-id="d848d-121">You can also mix `decimal` and numeric integral types in the same expression.</span></span> <span data-ttu-id="d848d-122">Kombinování však `decimal` a dalších typů s plovoucí desetinnou čárkou bez přetypování způsobí chybu kompilace.</span><span class="sxs-lookup"><span data-stu-id="d848d-122">However, mixing `decimal` and other floating-point types without a cast causes a compilation error.</span></span>  
  
 <span data-ttu-id="d848d-123">Další informace o implicitních číselných převodů najdete v tématu [implicitní číselné převody tabulky](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="d848d-123">For more information about implicit numeric conversions, see [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
 <span data-ttu-id="d848d-124">Další informace o explicitních číselných převodů najdete v tématu [explicitní číselné převody tabulky](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="d848d-124">For more information about explicit numeric conversions, see [Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).</span></span>  
  
## <a name="formatting-decimal-output"></a><span data-ttu-id="d848d-125">Formátování desítkového výstupu</span><span class="sxs-lookup"><span data-stu-id="d848d-125">Formatting Decimal Output</span></span>  
 <span data-ttu-id="d848d-126">Výsledky můžete naformátovat pomocí `String.Format` metoda, nebo pomocí <xref:System.Console.Write%2A?displayProperty=nameWithType> metodu, která volá `String.Format()`.</span><span class="sxs-lookup"><span data-stu-id="d848d-126">You can format the results by using the `String.Format` method, or through the <xref:System.Console.Write%2A?displayProperty=nameWithType> method, which calls `String.Format()`.</span></span> <span data-ttu-id="d848d-127">Formát měny je určen pomocí řetězce standardního formátu měny "C" nebo "c", jak je uvedeno v druhém příkladu dále v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="d848d-127">The currency format is specified by using the standard currency format string "C" or "c," as shown in the second example later in this article.</span></span> <span data-ttu-id="d848d-128">Další informace o `String.Format` metodu, najdete v části <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d848d-128">For more information about the `String.Format` method, see <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d848d-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="d848d-129">Example</span></span>  
 <span data-ttu-id="d848d-130">Následující příklad způsobí chybu kompilátoru tak, že zkusíte přidat [dvojité](../../../csharp/language-reference/keywords/double.md) a `decimal` proměnné.</span><span class="sxs-lookup"><span data-stu-id="d848d-130">The following example causes a compiler error by trying to add [double](../../../csharp/language-reference/keywords/double.md) and `decimal` variables.</span></span>  
  
```csharp  
decimal dec = 0m;
double dub = 9;  
// The following line causes an error that reads "Operator '+' cannot be applied to   
// operands of type 'double' and 'decimal'"  
Console.WriteLine(dec + dub);   
  
// You can fix the error by using explicit casting of either operand.  
Console.WriteLine(dec + (decimal)dub);  
Console.WriteLine((double)dec + dub);  
```  
  
 <span data-ttu-id="d848d-131">Výsledkem je následující chyba:</span><span class="sxs-lookup"><span data-stu-id="d848d-131">The result is the following error:</span></span>  
  
 `Operator '+' cannot be applied to operands of type 'double' and 'decimal'`  
  
 <span data-ttu-id="d848d-132">V tomto příkladu `decimal` a [int](../../../csharp/language-reference/keywords/int.md) jsou kombinované ve stejném výrazu.</span><span class="sxs-lookup"><span data-stu-id="d848d-132">In this example, a `decimal` and an [int](../../../csharp/language-reference/keywords/int.md) are mixed in the same expression.</span></span> <span data-ttu-id="d848d-133">Výsledek se vyhodnocuje `decimal` typu.</span><span class="sxs-lookup"><span data-stu-id="d848d-133">The result evaluates to the `decimal` type.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/decimal_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="d848d-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="d848d-134">Example</span></span>  
 <span data-ttu-id="d848d-135">V tomto příkladu je výstup naformátován pomocí řetězce formátu měny.</span><span class="sxs-lookup"><span data-stu-id="d848d-135">In this example, the output is formatted by using the currency format string.</span></span> <span data-ttu-id="d848d-136">Všimněte si, že `x` se zaokrouhlí, protože překročila $0,99 desetinných míst.</span><span class="sxs-lookup"><span data-stu-id="d848d-136">Notice that `x` is rounded because the decimal places exceed $0.99.</span></span> <span data-ttu-id="d848d-137">Proměnná `y`, která představuje maximální číslice, se zobrazí přesně ve správném formátu.</span><span class="sxs-lookup"><span data-stu-id="d848d-137">The variable `y`, which represents the maximum exact digits, is displayed exactly in the correct format.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/decimal_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="d848d-138">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d848d-138">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d848d-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="d848d-139">See Also</span></span>  
 <xref:System.Decimal>  
 [<span data-ttu-id="d848d-140">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d848d-140">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d848d-141">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d848d-141">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d848d-142">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d848d-142">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="d848d-143">Tabulka celočíselných typů</span><span class="sxs-lookup"><span data-stu-id="d848d-143">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="d848d-144">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="d848d-144">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="d848d-145">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="d848d-145">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="d848d-146">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="d848d-146">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
 [<span data-ttu-id="d848d-147">Standardní řetězce číselného formátu</span><span class="sxs-lookup"><span data-stu-id="d848d-147">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
