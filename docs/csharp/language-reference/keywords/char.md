---
title: Char – klíčové slovo - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 0b4f04a1ba6244373e36cc6a6188edabe33ec453
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424347"
---
# <a name="char-c-reference"></a><span data-ttu-id="95db5-102">char (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="95db5-102">char (C# Reference)</span></span>

<span data-ttu-id="95db5-103">`char` – Klíčové slovo se používá k deklaraci instance <xref:System.Char?displayProperty=nameWithType> strukturu, rozhraní .NET Framework používá k reprezentaci znaku Unicode.</span><span class="sxs-lookup"><span data-stu-id="95db5-103">The `char` keyword is used to declare an instance of the <xref:System.Char?displayProperty=nameWithType> structure that the .NET Framework uses to represent a Unicode character.</span></span> <span data-ttu-id="95db5-104">Hodnota `Char` objektu je hodnota číselná 16 bitů (pořadí).</span><span class="sxs-lookup"><span data-stu-id="95db5-104">The value of a `Char` object is a 16-bit numeric (ordinal) value.</span></span>

 <span data-ttu-id="95db5-105">Znaky kódování Unicode se používá k reprezentování většinu psané jazyky po celém světě.</span><span class="sxs-lookup"><span data-stu-id="95db5-105">Unicode characters are used to represent most of the written languages throughout the world.</span></span>

|<span data-ttu-id="95db5-106">type</span><span class="sxs-lookup"><span data-stu-id="95db5-106">Type</span></span>|<span data-ttu-id="95db5-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="95db5-107">Range</span></span>|<span data-ttu-id="95db5-108">Velikost</span><span class="sxs-lookup"><span data-stu-id="95db5-108">Size</span></span>|<span data-ttu-id="95db5-109">Typ formátu .NET</span><span class="sxs-lookup"><span data-stu-id="95db5-109">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="95db5-110">U + 0000 U + FFFF</span><span class="sxs-lookup"><span data-stu-id="95db5-110">U+0000 to U+FFFF</span></span>|<span data-ttu-id="95db5-111">16bitový znak Unicode</span><span class="sxs-lookup"><span data-stu-id="95db5-111">Unicode 16-bit character</span></span>|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="95db5-112">Literály</span><span class="sxs-lookup"><span data-stu-id="95db5-112">Literals</span></span>

<span data-ttu-id="95db5-113">Konstanty objektu `char` typu lze zapsat jako znakových literálů, šestnáctková řídicí sekvence nebo reprezentace Unicode.</span><span class="sxs-lookup"><span data-stu-id="95db5-113">Constants of the `char` type can be written as character literals, hexadecimal escape sequence, or Unicode representation.</span></span> <span data-ttu-id="95db5-114">Také můžete přetypovat kódy celočíselného znaku.</span><span class="sxs-lookup"><span data-stu-id="95db5-114">You can also cast the integral character codes.</span></span> <span data-ttu-id="95db5-115">V následujícím příkladu čtyři `char` proměnné jsou inicializována ve stejném `X`:</span><span class="sxs-lookup"><span data-stu-id="95db5-115">In the following example four `char` variables are initialized with the same character `X`:</span></span>

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a><span data-ttu-id="95db5-116">Převody</span><span class="sxs-lookup"><span data-stu-id="95db5-116">Conversions</span></span>

<span data-ttu-id="95db5-117">A `char` lze implicitně převést na [ushort](../builtin-types/integral-numeric-types.md), [int](../builtin-types/integral-numeric-types.md), [uint](../builtin-types/integral-numeric-types.md), [double](../../../csharp/language-reference/keywords/double.md), nebo [desetinné](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="95db5-117">A `char` can be implicitly converted to [ushort](../builtin-types/integral-numeric-types.md), [int](../builtin-types/integral-numeric-types.md), [uint](../builtin-types/integral-numeric-types.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="95db5-118">Však nejsou žádné implicitní převody z jiných typů `char` typu.</span><span class="sxs-lookup"><span data-stu-id="95db5-118">However, there are no implicit conversions from other types to the `char` type.</span></span>

<span data-ttu-id="95db5-119"><xref:System.Char?displayProperty=nameWithType> Typ poskytuje několik statické metody pro práci s `char` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="95db5-119">The <xref:System.Char?displayProperty=nameWithType> type provides several static methods for working with `char` values.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="95db5-120">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="95db5-120">C# language specification</span></span>  

<span data-ttu-id="95db5-121">Další informace najdete v tématu [integrální typy](~/_csharplang/spec/types.md#integral-types) v [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="95db5-121">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="95db5-122">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="95db5-122">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="95db5-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="95db5-123">See also</span></span>

- <xref:System.Char>
- [<span data-ttu-id="95db5-124">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="95db5-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="95db5-125">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="95db5-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="95db5-126">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="95db5-126">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="95db5-127">Celočíselné typy</span><span class="sxs-lookup"><span data-stu-id="95db5-127">Integral types</span></span>](../../../csharp/language-reference/builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="95db5-128">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="95db5-128">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [<span data-ttu-id="95db5-129">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="95db5-129">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="95db5-130">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="95db5-130">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
- [<span data-ttu-id="95db5-131">Typy s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="95db5-131">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)
- [<span data-ttu-id="95db5-132">Řetězce</span><span class="sxs-lookup"><span data-stu-id="95db5-132">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)
