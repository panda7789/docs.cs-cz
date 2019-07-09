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
ms.openlocfilehash: b58730d945582ded7b76fcd5c4c65bc1dd9324da
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661457"
---
# <a name="char-c-reference"></a><span data-ttu-id="e5e4f-102">char (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e5e4f-102">char (C# Reference)</span></span>

<span data-ttu-id="e5e4f-103">`char` – Klíčové slovo se používá k deklaraci instance <xref:System.Char?displayProperty=nameWithType> strukturu, rozhraní .NET Framework používá k reprezentaci znaku Unicode.</span><span class="sxs-lookup"><span data-stu-id="e5e4f-103">The `char` keyword is used to declare an instance of the <xref:System.Char?displayProperty=nameWithType> structure that the .NET Framework uses to represent a Unicode character.</span></span> <span data-ttu-id="e5e4f-104">Hodnota `Char` objektu je hodnota číselná 16 bitů (pořadí).</span><span class="sxs-lookup"><span data-stu-id="e5e4f-104">The value of a `Char` object is a 16-bit numeric (ordinal) value.</span></span>

 <span data-ttu-id="e5e4f-105">Znaky kódování Unicode se používá k reprezentování většinu psané jazyky po celém světě.</span><span class="sxs-lookup"><span data-stu-id="e5e4f-105">Unicode characters are used to represent most of the written languages throughout the world.</span></span>

|<span data-ttu-id="e5e4f-106">type</span><span class="sxs-lookup"><span data-stu-id="e5e4f-106">Type</span></span>|<span data-ttu-id="e5e4f-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="e5e4f-107">Range</span></span>|<span data-ttu-id="e5e4f-108">Velikost</span><span class="sxs-lookup"><span data-stu-id="e5e4f-108">Size</span></span>|<span data-ttu-id="e5e4f-109">Typ formátu .NET</span><span class="sxs-lookup"><span data-stu-id="e5e4f-109">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="e5e4f-110">U + 0000 U + FFFF</span><span class="sxs-lookup"><span data-stu-id="e5e4f-110">U+0000 to U+FFFF</span></span>|<span data-ttu-id="e5e4f-111">16bitový znak Unicode</span><span class="sxs-lookup"><span data-stu-id="e5e4f-111">Unicode 16-bit character</span></span>|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="e5e4f-112">Literály</span><span class="sxs-lookup"><span data-stu-id="e5e4f-112">Literals</span></span>

<span data-ttu-id="e5e4f-113">Konstanty objektu `char` typu lze zapsat jako znakových literálů, šestnáctková řídicí sekvence nebo reprezentace Unicode.</span><span class="sxs-lookup"><span data-stu-id="e5e4f-113">Constants of the `char` type can be written as character literals, hexadecimal escape sequence, or Unicode representation.</span></span> <span data-ttu-id="e5e4f-114">Také můžete přetypovat kódy celočíselného znaku.</span><span class="sxs-lookup"><span data-stu-id="e5e4f-114">You can also cast the integral character codes.</span></span> <span data-ttu-id="e5e4f-115">V následujícím příkladu čtyři `char` proměnné jsou inicializována ve stejném `X`:</span><span class="sxs-lookup"><span data-stu-id="e5e4f-115">In the following example four `char` variables are initialized with the same character `X`:</span></span>

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a><span data-ttu-id="e5e4f-116">Převody</span><span class="sxs-lookup"><span data-stu-id="e5e4f-116">Conversions</span></span>

<span data-ttu-id="e5e4f-117">A `char` lze implicitně převést na [ushort](../builtin-types/integral-numeric-types.md), [int](../builtin-types/integral-numeric-types.md), [uint](../builtin-types/integral-numeric-types.md), [double](../builtin-types/floating-point-numeric-types.md), nebo [desetinné](../builtin-types/floating-point-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="e5e4f-117">A `char` can be implicitly converted to [ushort](../builtin-types/integral-numeric-types.md), [int](../builtin-types/integral-numeric-types.md), [uint](../builtin-types/integral-numeric-types.md), [double](../builtin-types/floating-point-numeric-types.md), or [decimal](../builtin-types/floating-point-numeric-types.md).</span></span> <span data-ttu-id="e5e4f-118">Však nejsou žádné implicitní převody z jiných typů `char` typu.</span><span class="sxs-lookup"><span data-stu-id="e5e4f-118">However, there are no implicit conversions from other types to the `char` type.</span></span>

<span data-ttu-id="e5e4f-119"><xref:System.Char?displayProperty=nameWithType> Typ poskytuje několik statické metody pro práci s `char` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e5e4f-119">The <xref:System.Char?displayProperty=nameWithType> type provides several static methods for working with `char` values.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e5e4f-120">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e5e4f-120">C# language specification</span></span>  

<span data-ttu-id="e5e4f-121">Další informace najdete v tématu [integrální typy](~/_csharplang/spec/types.md#integral-types) v [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="e5e4f-121">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="e5e4f-122">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="e5e4f-122">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="e5e4f-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e5e4f-123">See also</span></span>

- <xref:System.Char>
- [<span data-ttu-id="e5e4f-124">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e5e4f-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="e5e4f-125">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e5e4f-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="e5e4f-126">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e5e4f-126">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="e5e4f-127">Celočíselné typy</span><span class="sxs-lookup"><span data-stu-id="e5e4f-127">Integral types</span></span>](../../../csharp/language-reference/builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="e5e4f-128">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="e5e4f-128">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [<span data-ttu-id="e5e4f-129">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="e5e4f-129">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="e5e4f-130">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="e5e4f-130">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
- [<span data-ttu-id="e5e4f-131">Typy s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="e5e4f-131">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)
- [<span data-ttu-id="e5e4f-132">Řetězce</span><span class="sxs-lookup"><span data-stu-id="e5e4f-132">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)
