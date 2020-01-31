---
title: typ znaku – C# odkaz
ms.date: 11/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 3952e9e30706a8cd362ef248955918de5dacf4a3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76787807"
---
# <a name="char-c-reference"></a><span data-ttu-id="f3e77-102">char (C# Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="f3e77-102">char (C# reference)</span></span>

<span data-ttu-id="f3e77-103">Klíčové slovo Type `char` je alias pro typ struktury <xref:System.Char?displayProperty=nameWithType> .NET, který představuje znak Unicode UTF-16.</span><span class="sxs-lookup"><span data-stu-id="f3e77-103">The `char` type keyword is an alias for the .NET <xref:System.Char?displayProperty=nameWithType> structure type that represents a Unicode UTF-16 character.</span></span>

|<span data-ttu-id="f3e77-104">Type</span><span class="sxs-lookup"><span data-stu-id="f3e77-104">Type</span></span>|<span data-ttu-id="f3e77-105">Rozsah</span><span class="sxs-lookup"><span data-stu-id="f3e77-105">Range</span></span>|<span data-ttu-id="f3e77-106">Velikost</span><span class="sxs-lookup"><span data-stu-id="f3e77-106">Size</span></span>|<span data-ttu-id="f3e77-107">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="f3e77-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="f3e77-108">U + 0000 až U + FFFF</span><span class="sxs-lookup"><span data-stu-id="f3e77-108">U+0000 to U+FFFF</span></span>|<span data-ttu-id="f3e77-109">16 bitů</span><span class="sxs-lookup"><span data-stu-id="f3e77-109">16 bit</span></span>|<xref:System.Char?displayProperty=nameWithType>|

<span data-ttu-id="f3e77-110">Výchozí hodnota typu `char` je `\0`, tedy U + 0000.</span><span class="sxs-lookup"><span data-stu-id="f3e77-110">The default value of the `char` type is `\0`, that is, U+0000.</span></span>

<span data-ttu-id="f3e77-111">Typ [řetězce](reference-types.md#the-string-type) představuje text jako posloupnost hodnot `char`.</span><span class="sxs-lookup"><span data-stu-id="f3e77-111">The [string](reference-types.md#the-string-type) type represents text as a sequence of `char` values.</span></span>

## <a name="literals"></a><span data-ttu-id="f3e77-112">Literály</span><span class="sxs-lookup"><span data-stu-id="f3e77-112">Literals</span></span>

<span data-ttu-id="f3e77-113">`char` hodnotu můžete zadat pomocí:</span><span class="sxs-lookup"><span data-stu-id="f3e77-113">You can specify a `char` value with:</span></span>

- <span data-ttu-id="f3e77-114">znakový literál.</span><span class="sxs-lookup"><span data-stu-id="f3e77-114">a character literal.</span></span>
- <span data-ttu-id="f3e77-115">řídicí sekvence Unicode, která je `\u` následovaná hexadecimálním znázorněním kódu znaku se čtyřmi symboly.</span><span class="sxs-lookup"><span data-stu-id="f3e77-115">a Unicode escape sequence, which is `\u` followed by the four-symbol hexadecimal representation of a character code.</span></span>
- <span data-ttu-id="f3e77-116">šestnáctková řídicí sekvence, která je `\x` následovaná hexadecimálním znázorněním kódu znaku.</span><span class="sxs-lookup"><span data-stu-id="f3e77-116">a hexadecimal escape sequence, which is `\x` followed by the hexadecimal representation of a character code.</span></span>

[!code-csharp-interactive[char literals](~/samples/csharp/language-reference/builtin-types/CharType.cs#Literals)]

<span data-ttu-id="f3e77-117">Jak ukazuje předchozí příklad, můžete také přetypovat hodnotu kódu znaku na odpovídající `char`ovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f3e77-117">As the preceding example shows, you also can cast the value of a character code into the corresponding `char` value.</span></span>

> [!NOTE]
> <span data-ttu-id="f3e77-118">V případě řídicí sekvence Unicode je nutné zadat všechny čtyři šestnáctkové číslice.</span><span class="sxs-lookup"><span data-stu-id="f3e77-118">In the case of a Unicode escape sequence, you must specify all four hexadecimal digits.</span></span> <span data-ttu-id="f3e77-119">To znamená, že `\u006A` je platná řídicí sekvence, zatímco `\u06A` a `\u6A` nejsou platné.</span><span class="sxs-lookup"><span data-stu-id="f3e77-119">That is, `\u006A` is a valid escape sequence, while `\u06A` and `\u6A` are not valid.</span></span>
>
> <span data-ttu-id="f3e77-120">V případě hexadecimální sekvence escape můžete vynechat úvodní nuly.</span><span class="sxs-lookup"><span data-stu-id="f3e77-120">In the case of a hexadecimal escape sequence, you can omit the leading zeros.</span></span> <span data-ttu-id="f3e77-121">To znamená, že řídicí sekvence `\x006A`, `\x06A`a `\x6A` jsou platné a odpovídají stejnému znaku.</span><span class="sxs-lookup"><span data-stu-id="f3e77-121">That is, the `\x006A`, `\x06A`, and `\x6A` escape sequences are valid and correspond to the same character.</span></span>

## <a name="conversions"></a><span data-ttu-id="f3e77-122">Převody</span><span class="sxs-lookup"><span data-stu-id="f3e77-122">Conversions</span></span>

<span data-ttu-id="f3e77-123">`char` typ je implicitně převoditelný na následující [celočíselné](integral-numeric-types.md) typy: `ushort`, `int`, `uint`, `long`a `ulong`.</span><span class="sxs-lookup"><span data-stu-id="f3e77-123">The `char` type is implicitly convertible to the following [integral](integral-numeric-types.md) types: `ushort`, `int`, `uint`, `long`, and `ulong`.</span></span> <span data-ttu-id="f3e77-124">Je také implicitně převoditelná na předdefinované číselné typy s [plovoucí desetinnou](floating-point-numeric-types.md) čárkou: `float`, `double`a `decimal`.</span><span class="sxs-lookup"><span data-stu-id="f3e77-124">It's also implicitly convertible to the built-in [floating-point](floating-point-numeric-types.md) numeric types: `float`, `double`, and `decimal`.</span></span> <span data-ttu-id="f3e77-125">Je explicitně převoditelná na `sbyte`, `byte`a `short` integrálních typů.</span><span class="sxs-lookup"><span data-stu-id="f3e77-125">It's explicitly convertible to `sbyte`, `byte`, and `short` integral types.</span></span>

<span data-ttu-id="f3e77-126">Neexistují žádné implicitní převody z jiných typů na typ `char`.</span><span class="sxs-lookup"><span data-stu-id="f3e77-126">There are no implicit conversions from other types to the `char` type.</span></span> <span data-ttu-id="f3e77-127">Jakýkoli [celočíselný](integral-numeric-types.md) typ nebo číslo [s plovoucí desetinnou](floating-point-numeric-types.md) čárkou však lze explicitně převést na `char`.</span><span class="sxs-lookup"><span data-stu-id="f3e77-127">However, any [integral](integral-numeric-types.md) or [floating-point](floating-point-numeric-types.md) numeric type is explicitly convertible to `char`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f3e77-128">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f3e77-128">C# language specification</span></span>

<span data-ttu-id="f3e77-129">Další informace naleznete v části [celočíselné typy](~/_csharplang/spec/types.md#integral-types) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="f3e77-129">For more information, see the [Integral types](~/_csharplang/spec/types.md#integral-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f3e77-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f3e77-130">See also</span></span>

- [<span data-ttu-id="f3e77-131">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="f3e77-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="f3e77-132">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="f3e77-132">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="f3e77-133">Řetězce</span><span class="sxs-lookup"><span data-stu-id="f3e77-133">Strings</span></span>](../../programming-guide/strings/index.md)
- <xref:System.Text.Rune?displayProperty=nameWithType>
