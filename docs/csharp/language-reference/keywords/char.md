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
ms.openlocfilehash: 255e69d3715a22e7933b4036e968e610657748cf
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353762"
---
# <a name="char-c-reference"></a><span data-ttu-id="92e7f-102">char (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="92e7f-102">char (C# Reference)</span></span>

<span data-ttu-id="92e7f-103">Klíčové slovo `char` slouží k deklaraci instance struktury <xref:System.Char?displayProperty=nameWithType>, kterou .NET Framework používá pro reprezentaci znaku Unicode.</span><span class="sxs-lookup"><span data-stu-id="92e7f-103">The `char` keyword is used to declare an instance of the <xref:System.Char?displayProperty=nameWithType> structure that the .NET Framework uses to represent a Unicode character.</span></span> <span data-ttu-id="92e7f-104">Hodnota objektu `Char` je 16bitová číselná hodnota (Ordinal).</span><span class="sxs-lookup"><span data-stu-id="92e7f-104">The value of a `Char` object is a 16-bit numeric (ordinal) value.</span></span>

 <span data-ttu-id="92e7f-105">Znaky Unicode slouží k reprezentaci většiny psaných jazyků po celém světě.</span><span class="sxs-lookup"><span data-stu-id="92e7f-105">Unicode characters are used to represent most of the written languages throughout the world.</span></span>

|<span data-ttu-id="92e7f-106">type</span><span class="sxs-lookup"><span data-stu-id="92e7f-106">Type</span></span>|<span data-ttu-id="92e7f-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="92e7f-107">Range</span></span>|<span data-ttu-id="92e7f-108">Size</span><span class="sxs-lookup"><span data-stu-id="92e7f-108">Size</span></span>|<span data-ttu-id="92e7f-109">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="92e7f-109">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="92e7f-110">U + 0000 až U + FFFF</span><span class="sxs-lookup"><span data-stu-id="92e7f-110">U+0000 to U+FFFF</span></span>|<span data-ttu-id="92e7f-111">16 bitový znak Unicode</span><span class="sxs-lookup"><span data-stu-id="92e7f-111">Unicode 16-bit character</span></span>|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="92e7f-112">Literály</span><span class="sxs-lookup"><span data-stu-id="92e7f-112">Literals</span></span>

<span data-ttu-id="92e7f-113">Konstanty typu `char` lze zapsat jako znakové literály, hexadecimální sekvence escape nebo reprezentace v kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="92e7f-113">Constants of the `char` type can be written as character literals, hexadecimal escape sequence, or Unicode representation.</span></span> <span data-ttu-id="92e7f-114">Můžete také přetypovat kódy integrálních znaků.</span><span class="sxs-lookup"><span data-stu-id="92e7f-114">You can also cast the integral character codes.</span></span> <span data-ttu-id="92e7f-115">V následujícím příkladu se čtyřmi proměnnými `char` inicializuje se stejným znakem `X`:</span><span class="sxs-lookup"><span data-stu-id="92e7f-115">In the following example four `char` variables are initialized with the same character `X`:</span></span>

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a><span data-ttu-id="92e7f-116">Převody</span><span class="sxs-lookup"><span data-stu-id="92e7f-116">Conversions</span></span>

<span data-ttu-id="92e7f-117">@No__t-0 lze implicitně převést na [UShort](../builtin-types/integral-numeric-types.md), [int](../builtin-types/integral-numeric-types.md), [uint](../builtin-types/integral-numeric-types.md), [Double](../builtin-types/floating-point-numeric-types.md)nebo [Decimal](../builtin-types/floating-point-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="92e7f-117">A `char` can be implicitly converted to [ushort](../builtin-types/integral-numeric-types.md), [int](../builtin-types/integral-numeric-types.md), [uint](../builtin-types/integral-numeric-types.md), [double](../builtin-types/floating-point-numeric-types.md), or [decimal](../builtin-types/floating-point-numeric-types.md).</span></span> <span data-ttu-id="92e7f-118">Neexistují však žádné implicitní převody z jiných typů na typ `char`.</span><span class="sxs-lookup"><span data-stu-id="92e7f-118">However, there are no implicit conversions from other types to the `char` type.</span></span>

<span data-ttu-id="92e7f-119">Typ <xref:System.Char?displayProperty=nameWithType> poskytuje několik statických metod pro práci s hodnotami `char`.</span><span class="sxs-lookup"><span data-stu-id="92e7f-119">The <xref:System.Char?displayProperty=nameWithType> type provides several static methods for working with `char` values.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="92e7f-120">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="92e7f-120">C# language specification</span></span>  

<span data-ttu-id="92e7f-121">Další informace naleznete v tématu [integrální typy](~/_csharplang/spec/types.md#integral-types) ve [ C# specifikaci jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="92e7f-121">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="92e7f-122">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="92e7f-122">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="92e7f-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="92e7f-123">See also</span></span>

- <xref:System.Char>
- [<span data-ttu-id="92e7f-124">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="92e7f-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="92e7f-125">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="92e7f-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="92e7f-126">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="92e7f-126">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="92e7f-127">Celočíselné typy</span><span class="sxs-lookup"><span data-stu-id="92e7f-127">Integral types</span></span>](../builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="92e7f-128">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="92e7f-128">Built-In Types Table</span></span>](./built-in-types-table.md)
- [<span data-ttu-id="92e7f-129">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="92e7f-129">Implicit Numeric Conversions Table</span></span>](./implicit-numeric-conversions-table.md)
- [<span data-ttu-id="92e7f-130">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="92e7f-130">Explicit Numeric Conversions Table</span></span>](./explicit-numeric-conversions-table.md)
- [<span data-ttu-id="92e7f-131">Řetězce</span><span class="sxs-lookup"><span data-stu-id="92e7f-131">Strings</span></span>](../../programming-guide/strings/index.md)
