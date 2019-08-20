---
title: klíčové slovo char C# – referenční informace
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 754c04bfc3b4090906420d55d55e51606b72f187
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605946"
---
# <a name="char-c-reference"></a><span data-ttu-id="4906c-102">char (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="4906c-102">char (C# Reference)</span></span>

<span data-ttu-id="4906c-103">Klíčové slovo slouží k deklaraci instance <xref:System.Char?displayProperty=nameWithType> struktury, kterou .NET Framework používá pro reprezentaci znaku Unicode. `char`</span><span class="sxs-lookup"><span data-stu-id="4906c-103">The `char` keyword is used to declare an instance of the <xref:System.Char?displayProperty=nameWithType> structure that the .NET Framework uses to represent a Unicode character.</span></span> <span data-ttu-id="4906c-104">Hodnota `Char` objektu je 16bitová číselná hodnota (Ordinal).</span><span class="sxs-lookup"><span data-stu-id="4906c-104">The value of a `Char` object is a 16-bit numeric (ordinal) value.</span></span>

 <span data-ttu-id="4906c-105">Znaky Unicode slouží k reprezentaci většiny psaných jazyků po celém světě.</span><span class="sxs-lookup"><span data-stu-id="4906c-105">Unicode characters are used to represent most of the written languages throughout the world.</span></span>

|<span data-ttu-id="4906c-106">type</span><span class="sxs-lookup"><span data-stu-id="4906c-106">Type</span></span>|<span data-ttu-id="4906c-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="4906c-107">Range</span></span>|<span data-ttu-id="4906c-108">Velikost</span><span class="sxs-lookup"><span data-stu-id="4906c-108">Size</span></span>|<span data-ttu-id="4906c-109">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="4906c-109">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="4906c-110">U + 0000 až U + FFFF</span><span class="sxs-lookup"><span data-stu-id="4906c-110">U+0000 to U+FFFF</span></span>|<span data-ttu-id="4906c-111">16 bitový znak Unicode</span><span class="sxs-lookup"><span data-stu-id="4906c-111">Unicode 16-bit character</span></span>|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="4906c-112">Literály</span><span class="sxs-lookup"><span data-stu-id="4906c-112">Literals</span></span>

<span data-ttu-id="4906c-113">Konstanty `char` typu lze zapsat jako znakové literály, šestnáctkové řídicí sekvence nebo reprezentace v kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="4906c-113">Constants of the `char` type can be written as character literals, hexadecimal escape sequence, or Unicode representation.</span></span> <span data-ttu-id="4906c-114">Můžete také přetypovat kódy integrálních znaků.</span><span class="sxs-lookup"><span data-stu-id="4906c-114">You can also cast the integral character codes.</span></span> <span data-ttu-id="4906c-115">V následujícím příkladu jsou čtyři `char` proměnné inicializovány se stejným znakem `X`:</span><span class="sxs-lookup"><span data-stu-id="4906c-115">In the following example four `char` variables are initialized with the same character `X`:</span></span>

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a><span data-ttu-id="4906c-116">Převody</span><span class="sxs-lookup"><span data-stu-id="4906c-116">Conversions</span></span>

<span data-ttu-id="4906c-117">[](../builtin-types/floating-point-numeric-types.md) [](../builtin-types/integral-numeric-types.md) [](../builtin-types/integral-numeric-types.md) [](../builtin-types/floating-point-numeric-types.md) [](../builtin-types/integral-numeric-types.md)Lze implicitně převést na UShort, int, uint, Double nebo Decimal. `char`</span><span class="sxs-lookup"><span data-stu-id="4906c-117">A `char` can be implicitly converted to [ushort](../builtin-types/integral-numeric-types.md), [int](../builtin-types/integral-numeric-types.md), [uint](../builtin-types/integral-numeric-types.md), [double](../builtin-types/floating-point-numeric-types.md), or [decimal](../builtin-types/floating-point-numeric-types.md).</span></span> <span data-ttu-id="4906c-118">Neexistují však žádné implicitní převody z jiných typů na `char` typ.</span><span class="sxs-lookup"><span data-stu-id="4906c-118">However, there are no implicit conversions from other types to the `char` type.</span></span>

<span data-ttu-id="4906c-119">Typ poskytuje několik statických metod pro práci s `char` hodnotami. <xref:System.Char?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="4906c-119">The <xref:System.Char?displayProperty=nameWithType> type provides several static methods for working with `char` values.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4906c-120">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4906c-120">C# language specification</span></span>  

<span data-ttu-id="4906c-121">Další informace naleznete v tématu [integrální typy](~/_csharplang/spec/types.md#integral-types) ve [ C# specifikaci jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="4906c-121">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="4906c-122">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="4906c-122">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="4906c-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4906c-123">See also</span></span>

- <xref:System.Char>
- [<span data-ttu-id="4906c-124">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="4906c-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4906c-125">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4906c-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4906c-126">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4906c-126">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="4906c-127">Celočíselné typy</span><span class="sxs-lookup"><span data-stu-id="4906c-127">Integral types</span></span>](../builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="4906c-128">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="4906c-128">Built-In Types Table</span></span>](./built-in-types-table.md)
- [<span data-ttu-id="4906c-129">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="4906c-129">Implicit Numeric Conversions Table</span></span>](./implicit-numeric-conversions-table.md)
- [<span data-ttu-id="4906c-130">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="4906c-130">Explicit Numeric Conversions Table</span></span>](./explicit-numeric-conversions-table.md)
- [<span data-ttu-id="4906c-131">Typy s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="4906c-131">Nullable Types</span></span>](../../programming-guide/nullable-types/index.md)
- [<span data-ttu-id="4906c-132">Řetězce</span><span class="sxs-lookup"><span data-stu-id="4906c-132">Strings</span></span>](../../programming-guide/strings/index.md)
