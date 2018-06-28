---
title: Char – klíčové slovo (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: ea465e240a1d74b3f473316ca63b05bd0ba90777
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37028029"
---
# <a name="char-c-reference"></a><span data-ttu-id="8243f-102">char (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="8243f-102">char (C# Reference)</span></span>

<span data-ttu-id="8243f-103">`char` – Klíčové slovo se používá k deklaraci instance <xref:System.Char?displayProperty=nameWithType> struktura, která rozhraní .NET Framework se používá k reprezentaci znak Unicode.</span><span class="sxs-lookup"><span data-stu-id="8243f-103">The `char` keyword is used to declare an instance of the <xref:System.Char?displayProperty=nameWithType> structure that the .NET Framework uses to represent a Unicode character.</span></span> <span data-ttu-id="8243f-104">Hodnota `Char` objekt je hodnotu numerické 16bitové (pořadí).</span><span class="sxs-lookup"><span data-stu-id="8243f-104">The value of a `Char` object is a 16-bit numeric (ordinal) value.</span></span>

 <span data-ttu-id="8243f-105">Znaky kódování Unicode se používají k vyjádření většinu psané jazyky po celém světě.</span><span class="sxs-lookup"><span data-stu-id="8243f-105">Unicode characters are used to represent most of the written languages throughout the world.</span></span>

|<span data-ttu-id="8243f-106">Typ</span><span class="sxs-lookup"><span data-stu-id="8243f-106">Type</span></span>|<span data-ttu-id="8243f-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="8243f-107">Range</span></span>|<span data-ttu-id="8243f-108">Velikost</span><span class="sxs-lookup"><span data-stu-id="8243f-108">Size</span></span>|<span data-ttu-id="8243f-109">Typ formátu .NET</span><span class="sxs-lookup"><span data-stu-id="8243f-109">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="8243f-110">U + 0000 U + FFFF</span><span class="sxs-lookup"><span data-stu-id="8243f-110">U+0000 to U+FFFF</span></span>|<span data-ttu-id="8243f-111">16bitové znak Unicode</span><span class="sxs-lookup"><span data-stu-id="8243f-111">Unicode 16-bit character</span></span>|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="8243f-112">Literály</span><span class="sxs-lookup"><span data-stu-id="8243f-112">Literals</span></span>

<span data-ttu-id="8243f-113">Konstanty z `char` typu lze zapsat jako znakové literály, šestnáctková řídicí sekvence nebo reprezentace kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="8243f-113">Constants of the `char` type can be written as character literals, hexadecimal escape sequence, or Unicode representation.</span></span> <span data-ttu-id="8243f-114">Můžete také přetypování kódy integrální znaků.</span><span class="sxs-lookup"><span data-stu-id="8243f-114">You can also cast the integral character codes.</span></span> <span data-ttu-id="8243f-115">V následujícím příkladu čtyři `char` proměnné se inicializují ve stejném `X`:</span><span class="sxs-lookup"><span data-stu-id="8243f-115">In the following example four `char` variables are initialized with the same character `X`:</span></span>

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a><span data-ttu-id="8243f-116">Převody</span><span class="sxs-lookup"><span data-stu-id="8243f-116">Conversions</span></span>

<span data-ttu-id="8243f-117">A `char` může být implicitně převedena na [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [Celé_číslo](../../../csharp/language-reference/keywords/uint.md), [dlouho](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md) , [float](../../../csharp/language-reference/keywords/float.md), [dvojité](../../../csharp/language-reference/keywords/double.md), nebo [decimal](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="8243f-117">A `char` can be implicitly converted to [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="8243f-118">Existují však žádná implicitní převody z ostatních typů k `char` typu.</span><span class="sxs-lookup"><span data-stu-id="8243f-118">However, there are no implicit conversions from other types to the `char` type.</span></span>

<span data-ttu-id="8243f-119"><xref:System.Char?displayProperty=nameWithType> Typu poskytuje několik statické metody pro práci s `char` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="8243f-119">The <xref:System.Char?displayProperty=nameWithType> type provides several static methods for working with `char` values.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8243f-120">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8243f-120">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="8243f-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8243f-121">See also</span></span>

<xref:System.Char>  
[<span data-ttu-id="8243f-122">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8243f-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
[<span data-ttu-id="8243f-123">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="8243f-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
[<span data-ttu-id="8243f-124">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8243f-124">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
[<span data-ttu-id="8243f-125">Tabulka celočíselných typů</span><span class="sxs-lookup"><span data-stu-id="8243f-125">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
[<span data-ttu-id="8243f-126">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="8243f-126">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
[<span data-ttu-id="8243f-127">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="8243f-127">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
[<span data-ttu-id="8243f-128">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="8243f-128">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
[<span data-ttu-id="8243f-129">Typy s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="8243f-129">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
[<span data-ttu-id="8243f-130">Řetězce</span><span class="sxs-lookup"><span data-stu-id="8243f-130">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)