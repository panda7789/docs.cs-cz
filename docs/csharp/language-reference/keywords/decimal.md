---
title: Decimal – klíčové slovo - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- decimal_CSharpKeyword
- decimal
helpviewer_keywords:
- decimal keyword [C#]
ms.assetid: b6522132-b5ee-4be3-ad13-3adfdb7de7a1
ms.openlocfilehash: 7ad01f9e4f5a8b1a153b1ef306e9d6168335eb3d
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424309"
---
# <a name="decimal-c-reference"></a><span data-ttu-id="bfd52-102">decimal (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="bfd52-102">decimal (C# Reference)</span></span>

<span data-ttu-id="bfd52-103">`decimal` – Klíčové slovo označuje typ 128bitových dat.</span><span class="sxs-lookup"><span data-stu-id="bfd52-103">The `decimal` keyword indicates a 128-bit data type.</span></span> <span data-ttu-id="bfd52-104">Ve srovnání s jinými typy s plovoucí desetinnou čárkou `decimal` typ má větší přesnost a menší rozsah, díky čemuž je vhodný pro výpočty finančních a přepočty měn.</span><span class="sxs-lookup"><span data-stu-id="bfd52-104">Compared to other floating-point types, the `decimal` type has more precision and a smaller range, which makes it appropriate for financial and monetary calculations.</span></span> <span data-ttu-id="bfd52-105">Přibližný rozsah a přesnost `decimal` typu jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="bfd52-105">The approximate range and precision for the `decimal` type are shown in the following table.</span></span>

|<span data-ttu-id="bfd52-106">type</span><span class="sxs-lookup"><span data-stu-id="bfd52-106">Type</span></span>|<span data-ttu-id="bfd52-107">Přibližný rozsah</span><span class="sxs-lookup"><span data-stu-id="bfd52-107">Approximate Range</span></span>|<span data-ttu-id="bfd52-108">Přesnost</span><span class="sxs-lookup"><span data-stu-id="bfd52-108">Precision</span></span>|<span data-ttu-id="bfd52-109">Typ formátu .NET</span><span class="sxs-lookup"><span data-stu-id="bfd52-109">.NET type</span></span>|
|----------|-----------------------|---------------|-------------------------|
|`decimal`|<span data-ttu-id="bfd52-110">±1.0 x 10<sup>– 28</sup> k ±7.9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="bfd52-110">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="bfd52-111">28–29 významných číslic</span><span class="sxs-lookup"><span data-stu-id="bfd52-111">28-29 significant digits</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="bfd52-112">Výchozí hodnota `decimal` je 0 m.</span><span class="sxs-lookup"><span data-stu-id="bfd52-112">The default value of a `decimal` is 0m.</span></span>

## <a name="literals"></a><span data-ttu-id="bfd52-113">Literály</span><span class="sxs-lookup"><span data-stu-id="bfd52-113">Literals</span></span>

<span data-ttu-id="bfd52-114">Pokud chcete, aby číselný literál reálného čísla jsou považovány za `decimal`, použijte příponu m nebo M, například:</span><span class="sxs-lookup"><span data-stu-id="bfd52-114">If you want a numeric real literal to be treated as `decimal`, use the suffix m or M, for example:</span></span>

```csharp
decimal myMoney = 300.5m;
```

<span data-ttu-id="bfd52-115">Bez přípony m je číslo považováno za [double](../../../csharp/language-reference/keywords/double.md) a vygeneruje chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="bfd52-115">Without the suffix m, the number is treated as a [double](../../../csharp/language-reference/keywords/double.md) and generates a compiler error.</span></span>

## <a name="conversions"></a><span data-ttu-id="bfd52-116">Převody</span><span class="sxs-lookup"><span data-stu-id="bfd52-116">Conversions</span></span>

<span data-ttu-id="bfd52-117">Integrální typy jsou implicitně převedeny na `decimal` a výsledek je vyhodnocen jako `decimal`.</span><span class="sxs-lookup"><span data-stu-id="bfd52-117">The integral types are implicitly converted to `decimal` and the result evaluates to `decimal`.</span></span> <span data-ttu-id="bfd52-118">Z tohoto důvodu můžete inicializovat proměnnou desítkového čísla pomocí celočíselného literálu bez přípony, a to následovně:</span><span class="sxs-lookup"><span data-stu-id="bfd52-118">Therefore you can initialize a decimal variable using an integer literal, without the suffix, as follows:</span></span>

```csharp
decimal myMoney = 300;
```

<span data-ttu-id="bfd52-119">Neexistuje žádný implicitní převod mezi ostatní typy s plovoucí desetinnou čárkou a `decimal` typ; proto přetypování musí použít k převodu mezi těmito dvěma typy.</span><span class="sxs-lookup"><span data-stu-id="bfd52-119">There is no implicit conversion between other floating-point types and the `decimal` type; therefore, a cast must be used to convert between these two types.</span></span> <span data-ttu-id="bfd52-120">Příklad:</span><span class="sxs-lookup"><span data-stu-id="bfd52-120">For example:</span></span>

```csharp
decimal myMoney = 99.9m;
double x = (double)myMoney;
myMoney = (decimal)x;
```

<span data-ttu-id="bfd52-121">Můžete také kombinovat `decimal` a numerické integrální typy ve stejném výrazu.</span><span class="sxs-lookup"><span data-stu-id="bfd52-121">You can also mix `decimal` and numeric integral types in the same expression.</span></span> <span data-ttu-id="bfd52-122">Kombinace `decimal` a jiné typy s plovoucí desetinnou čárkou bez přetypování způsobí chybu kompilace.</span><span class="sxs-lookup"><span data-stu-id="bfd52-122">However, mixing `decimal` and other floating-point types without a cast causes a compilation error.</span></span>

<span data-ttu-id="bfd52-123">Další informace o implicitním číselném převodu naleznete v tématu [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="bfd52-123">For more information about implicit numeric conversions, see [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>

<span data-ttu-id="bfd52-124">Další informace o explicitním číselném převodu naleznete v tématu [Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="bfd52-124">For more information about explicit numeric conversions, see [Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).</span></span>

## <a name="formatting-decimal-output"></a><span data-ttu-id="bfd52-125">Formátování desítkového výstupu</span><span class="sxs-lookup"><span data-stu-id="bfd52-125">Formatting decimal output</span></span>

<span data-ttu-id="bfd52-126">Výsledky můžete naformátovat pomocí `String.Format` metodu, nebo prostřednictvím <xref:System.Console.Write%2A?displayProperty=nameWithType> metoda, která volá `String.Format()`.</span><span class="sxs-lookup"><span data-stu-id="bfd52-126">You can format the results by using the `String.Format` method, or through the <xref:System.Console.Write%2A?displayProperty=nameWithType> method, which calls `String.Format()`.</span></span> <span data-ttu-id="bfd52-127">Formát měny je určen pomocí řetězce standardního formátu měny "C" nebo "c", jak je uvedeno v druhém příkladu dále v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="bfd52-127">The currency format is specified by using the standard currency format string "C" or "c," as shown in the second example later in this article.</span></span> <span data-ttu-id="bfd52-128">Další informace o `String.Format` metodu, najdete v článku <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bfd52-128">For more information about the `String.Format` method, see <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="bfd52-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="bfd52-129">Example</span></span>

<span data-ttu-id="bfd52-130">Následující příklad způsobí chybu kompilátoru při kompilaci přidáním [double](../../../csharp/language-reference/keywords/double.md) a `decimal` proměnné.</span><span class="sxs-lookup"><span data-stu-id="bfd52-130">The following example causes a compiler error by trying to add [double](../../../csharp/language-reference/keywords/double.md) and `decimal` variables.</span></span>

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

<span data-ttu-id="bfd52-131">Výsledkem je následující chyba:</span><span class="sxs-lookup"><span data-stu-id="bfd52-131">The result is the following error:</span></span>

`Operator '+' cannot be applied to operands of type 'double' and 'decimal'`

<span data-ttu-id="bfd52-132">V tomto příkladu `decimal` a [int](../../../csharp/language-reference/builtin-types/integral-numeric-types.md) jsou kombinované ve stejném výrazu.</span><span class="sxs-lookup"><span data-stu-id="bfd52-132">In this example, a `decimal` and an [int](../../../csharp/language-reference/builtin-types/integral-numeric-types.md) are mixed in the same expression.</span></span> <span data-ttu-id="bfd52-133">Výsledek je vyhodnocen `decimal` typu.</span><span class="sxs-lookup"><span data-stu-id="bfd52-133">The result evaluates to the `decimal` type.</span></span>

[!code-csharp[csrefKeywordsTypes#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#6)]

## <a name="example"></a><span data-ttu-id="bfd52-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="bfd52-134">Example</span></span>

<span data-ttu-id="bfd52-135">V tomto příkladu je výstup naformátován pomocí řetězce formátu měny.</span><span class="sxs-lookup"><span data-stu-id="bfd52-135">In this example, the output is formatted by using the currency format string.</span></span> <span data-ttu-id="bfd52-136">Všimněte si, že `x` je zaokrouhlena, protože desetinná místa překračují hodnotu $0.99.</span><span class="sxs-lookup"><span data-stu-id="bfd52-136">Notice that `x` is rounded because the decimal places exceed $0.99.</span></span> <span data-ttu-id="bfd52-137">Proměnná `y`, která představuje maximální přesné číslice, se zobrazí přesně ve správném formátu.</span><span class="sxs-lookup"><span data-stu-id="bfd52-137">The variable `y`, which represents the maximum exact digits, is displayed exactly in the correct format.</span></span>

[!code-csharp[csrefKeywordsTypes#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#7)]

## <a name="c-language-specification"></a><span data-ttu-id="bfd52-138">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bfd52-138">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="bfd52-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bfd52-139">See also</span></span>

- <xref:System.Decimal>
- [<span data-ttu-id="bfd52-140">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bfd52-140">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="bfd52-141">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="bfd52-141">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="bfd52-142">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bfd52-142">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="bfd52-143">Celočíselné typy</span><span class="sxs-lookup"><span data-stu-id="bfd52-143">Integral types</span></span>](../../../csharp/language-reference/builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="bfd52-144">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="bfd52-144">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [<span data-ttu-id="bfd52-145">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="bfd52-145">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="bfd52-146">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="bfd52-146">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
- [<span data-ttu-id="bfd52-147">Standardní řetězce číselného formátu</span><span class="sxs-lookup"><span data-stu-id="bfd52-147">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
