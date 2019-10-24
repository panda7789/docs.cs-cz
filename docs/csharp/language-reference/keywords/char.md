---
title: klíčové slovo char C# – referenční informace
ms.custom: seodec18
ms.date: 10/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 1b9f8d1bb205a6cbfe521830a11bd8878ccde991
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771804"
---
# <a name="char-c-reference"></a><span data-ttu-id="7e212-102">char (C# Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="7e212-102">char (C# reference)</span></span>

<span data-ttu-id="7e212-103">Klíčové slovo Type `char` je alias pro typ struktury <xref:System.Char?displayProperty=nameWithType> .NET, který představuje znak Unicode UTF-16:</span><span class="sxs-lookup"><span data-stu-id="7e212-103">The `char` type keyword is an alias for the .NET <xref:System.Char?displayProperty=nameWithType> structure type that represents a Unicode UTF-16 character:</span></span>

|<span data-ttu-id="7e212-104">Typ</span><span class="sxs-lookup"><span data-stu-id="7e212-104">Type</span></span>|<span data-ttu-id="7e212-105">Rozsah</span><span class="sxs-lookup"><span data-stu-id="7e212-105">Range</span></span>|<span data-ttu-id="7e212-106">Velikost</span><span class="sxs-lookup"><span data-stu-id="7e212-106">Size</span></span>|<span data-ttu-id="7e212-107">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="7e212-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="7e212-108">U + 0000 až U + FFFF</span><span class="sxs-lookup"><span data-stu-id="7e212-108">U+0000 to U+FFFF</span></span>|<span data-ttu-id="7e212-109">16 bitů</span><span class="sxs-lookup"><span data-stu-id="7e212-109">16 bit</span></span>|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="7e212-110">Literály</span><span class="sxs-lookup"><span data-stu-id="7e212-110">Literals</span></span>

<span data-ttu-id="7e212-111">Konstanty `char`ho typu lze zapsat jako znakové literály, hexadecimální sekvence escape nebo reprezentace v kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="7e212-111">Constants of the `char` type can be written as character literals, hexadecimal escape sequence, or Unicode representation.</span></span> <span data-ttu-id="7e212-112">Můžete také přetypovat celočíselný kód znaku do odpovídající `char` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7e212-112">You can also cast an integral character code into the corresponding `char` value.</span></span> <span data-ttu-id="7e212-113">V následujícím příkladu jsou všechny čtyři prvky pole `char` inicializovány se stejným znakem `X`:</span><span class="sxs-lookup"><span data-stu-id="7e212-113">In the following example, the four elements of an array of `char` are initialized with the same character `X`:</span></span>

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a><span data-ttu-id="7e212-114">Převody</span><span class="sxs-lookup"><span data-stu-id="7e212-114">Conversions</span></span>

<span data-ttu-id="7e212-115">`char` typ je implicitně převoditelný na následující [celočíselné](../builtin-types/integral-numeric-types.md) typy: `ushort`, `int`, `uint`, `long`a `ulong`.</span><span class="sxs-lookup"><span data-stu-id="7e212-115">The `char` type is implicitly convertible to the following [integral](../builtin-types/integral-numeric-types.md) types: `ushort`, `int`, `uint`, `long`, and `ulong`.</span></span> <span data-ttu-id="7e212-116">Je také implicitně převoditelná na předdefinované číselné typy s [plovoucí desetinnou](../builtin-types/floating-point-numeric-types.md) čárkou: `float`, `double`a `decimal`.</span><span class="sxs-lookup"><span data-stu-id="7e212-116">It's also implicitly convertible to the built-in [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types: `float`, `double`, and `decimal`.</span></span> <span data-ttu-id="7e212-117">Je explicitně převoditelná na `sbyte`, `byte`a `short` integrálních typů.</span><span class="sxs-lookup"><span data-stu-id="7e212-117">It's explicitly convertible to `sbyte`, `byte`, and `short` integral types.</span></span>

<span data-ttu-id="7e212-118">Neexistují žádné implicitní převody z jiných typů na typ `char`.</span><span class="sxs-lookup"><span data-stu-id="7e212-118">There are no implicit conversions from other types to the `char` type.</span></span> <span data-ttu-id="7e212-119">Jakýkoli [celočíselný](../builtin-types/integral-numeric-types.md) typ nebo číslo [s plovoucí desetinnou](../builtin-types/floating-point-numeric-types.md) čárkou však lze explicitně převést na `char`.</span><span class="sxs-lookup"><span data-stu-id="7e212-119">However, any [integral](../builtin-types/integral-numeric-types.md) or [floating-point](../builtin-types/floating-point-numeric-types.md) numeric type is explicitly convertible to `char`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7e212-120">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7e212-120">C# language specification</span></span>

<span data-ttu-id="7e212-121">Další informace naleznete v části [celočíselné typy](~/_csharplang/spec/types.md#integral-types) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="7e212-121">For more information, see the [Integral types](~/_csharplang/spec/types.md#integral-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7e212-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7e212-122">See also</span></span>

- [<span data-ttu-id="7e212-123">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="7e212-123">C# reference</span></span>](../index.md)
- [<span data-ttu-id="7e212-124">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7e212-124">C# keywords</span></span>](./index.md)
- [<span data-ttu-id="7e212-125">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="7e212-125">Built-in types table</span></span>](./built-in-types-table.md)
- [<span data-ttu-id="7e212-126">Řetězce</span><span class="sxs-lookup"><span data-stu-id="7e212-126">Strings</span></span>](../../programming-guide/strings/index.md)
- <xref:System.Char?displayProperty=nameWithType>
