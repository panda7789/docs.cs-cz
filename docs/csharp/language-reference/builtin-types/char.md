---
title: typ znaku – C# odkaz
ms.date: 11/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 3b2eec4f0e17aa329fe3865fb3ef453ee030c6a7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451162"
---
# <a name="char-c-reference"></a><span data-ttu-id="18cc2-102">char (C# Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="18cc2-102">char (C# reference)</span></span>

<span data-ttu-id="18cc2-103">Klíčové slovo Type `char` je alias pro typ struktury <xref:System.Char?displayProperty=nameWithType> .NET, který představuje znak Unicode UTF-16.</span><span class="sxs-lookup"><span data-stu-id="18cc2-103">The `char` type keyword is an alias for the .NET <xref:System.Char?displayProperty=nameWithType> structure type that represents a Unicode UTF-16 character.</span></span>

|<span data-ttu-id="18cc2-104">Typ</span><span class="sxs-lookup"><span data-stu-id="18cc2-104">Type</span></span>|<span data-ttu-id="18cc2-105">Rozsah</span><span class="sxs-lookup"><span data-stu-id="18cc2-105">Range</span></span>|<span data-ttu-id="18cc2-106">Velikost</span><span class="sxs-lookup"><span data-stu-id="18cc2-106">Size</span></span>|<span data-ttu-id="18cc2-107">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="18cc2-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="18cc2-108">U + 0000 až U + FFFF</span><span class="sxs-lookup"><span data-stu-id="18cc2-108">U+0000 to U+FFFF</span></span>|<span data-ttu-id="18cc2-109">16 bitů</span><span class="sxs-lookup"><span data-stu-id="18cc2-109">16 bit</span></span>|<xref:System.Char?displayProperty=nameWithType>|

<span data-ttu-id="18cc2-110">Typ [řetězce](reference-types.md#the-string-type) představuje text jako posloupnost hodnot `char`.</span><span class="sxs-lookup"><span data-stu-id="18cc2-110">The [string](reference-types.md#the-string-type) type represents text as a sequence of `char` values.</span></span>

## <a name="literals"></a><span data-ttu-id="18cc2-111">Literály</span><span class="sxs-lookup"><span data-stu-id="18cc2-111">Literals</span></span>

<span data-ttu-id="18cc2-112">`char` hodnotu můžete zadat pomocí:</span><span class="sxs-lookup"><span data-stu-id="18cc2-112">You can specify a `char` value with:</span></span>

- <span data-ttu-id="18cc2-113">znakový literál.</span><span class="sxs-lookup"><span data-stu-id="18cc2-113">a character literal.</span></span>
- <span data-ttu-id="18cc2-114">řídicí sekvence Unicode, která je `\u` následovaná hexadecimálním znázorněním kódu znaku se čtyřmi symboly.</span><span class="sxs-lookup"><span data-stu-id="18cc2-114">a Unicode escape sequence, which is `\u` followed by the four-symbol hexadecimal representation of a character code.</span></span>
- <span data-ttu-id="18cc2-115">šestnáctková řídicí sekvence, která je `\x` následovaná hexadecimálním znázorněním kódu znaku.</span><span class="sxs-lookup"><span data-stu-id="18cc2-115">a hexadecimal escape sequence, which is `\x` followed by the hexadecimal representation of a character code.</span></span>

[!code-csharp-interactive[char literals](~/samples/csharp/language-reference/builtin-types/CharType.cs#Literals)]

<span data-ttu-id="18cc2-116">Jak ukazuje předchozí příklad, můžete také přetypovat hodnotu kódu znaku na odpovídající `char`ovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="18cc2-116">As the preceding example shows, you also can cast the value of a character code into the corresponding `char` value.</span></span>

> [!NOTE]
> <span data-ttu-id="18cc2-117">V případě řídicí sekvence Unicode je nutné zadat všechny čtyři šestnáctkové číslice.</span><span class="sxs-lookup"><span data-stu-id="18cc2-117">In the case of a Unicode escape sequence, you must specify all four hexadecimal digits.</span></span> <span data-ttu-id="18cc2-118">To znamená, že `\u006A` je platná řídicí sekvence, zatímco `\u06A` a `\u6A` nejsou platné.</span><span class="sxs-lookup"><span data-stu-id="18cc2-118">That is, `\u006A` is a valid escape sequence, while `\u06A` and `\u6A` are not valid.</span></span>
>
> <span data-ttu-id="18cc2-119">V případě hexadecimální sekvence escape můžete vynechat úvodní nuly.</span><span class="sxs-lookup"><span data-stu-id="18cc2-119">In the case of a hexadecimal escape sequence, you can omit the leading zeros.</span></span> <span data-ttu-id="18cc2-120">To znamená, že řídicí sekvence `\x006A`, `\x06A`a `\x6A` jsou platné a odpovídají stejnému znaku.</span><span class="sxs-lookup"><span data-stu-id="18cc2-120">That is, the `\x006A`, `\x06A`, and `\x6A` escape sequences are valid and correspond to the same character.</span></span>

## <a name="conversions"></a><span data-ttu-id="18cc2-121">Převody</span><span class="sxs-lookup"><span data-stu-id="18cc2-121">Conversions</span></span>

<span data-ttu-id="18cc2-122">`char` typ je implicitně převoditelný na následující [celočíselné](integral-numeric-types.md) typy: `ushort`, `int`, `uint`, `long`a `ulong`.</span><span class="sxs-lookup"><span data-stu-id="18cc2-122">The `char` type is implicitly convertible to the following [integral](integral-numeric-types.md) types: `ushort`, `int`, `uint`, `long`, and `ulong`.</span></span> <span data-ttu-id="18cc2-123">Je také implicitně převoditelná na předdefinované číselné typy s [plovoucí desetinnou](floating-point-numeric-types.md) čárkou: `float`, `double`a `decimal`.</span><span class="sxs-lookup"><span data-stu-id="18cc2-123">It's also implicitly convertible to the built-in [floating-point](floating-point-numeric-types.md) numeric types: `float`, `double`, and `decimal`.</span></span> <span data-ttu-id="18cc2-124">Je explicitně převoditelná na `sbyte`, `byte`a `short` integrálních typů.</span><span class="sxs-lookup"><span data-stu-id="18cc2-124">It's explicitly convertible to `sbyte`, `byte`, and `short` integral types.</span></span>

<span data-ttu-id="18cc2-125">Neexistují žádné implicitní převody z jiných typů na typ `char`.</span><span class="sxs-lookup"><span data-stu-id="18cc2-125">There are no implicit conversions from other types to the `char` type.</span></span> <span data-ttu-id="18cc2-126">Jakýkoli [celočíselný](integral-numeric-types.md) typ nebo číslo [s plovoucí desetinnou](floating-point-numeric-types.md) čárkou však lze explicitně převést na `char`.</span><span class="sxs-lookup"><span data-stu-id="18cc2-126">However, any [integral](integral-numeric-types.md) or [floating-point](floating-point-numeric-types.md) numeric type is explicitly convertible to `char`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="18cc2-127">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="18cc2-127">C# language specification</span></span>

<span data-ttu-id="18cc2-128">Další informace naleznete v části [celočíselné typy](~/_csharplang/spec/types.md#integral-types) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="18cc2-128">For more information, see the [Integral types](~/_csharplang/spec/types.md#integral-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="18cc2-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="18cc2-129">See also</span></span>

- [<span data-ttu-id="18cc2-130">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="18cc2-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="18cc2-131">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="18cc2-131">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="18cc2-132">Řetězce</span><span class="sxs-lookup"><span data-stu-id="18cc2-132">Strings</span></span>](../../programming-guide/strings/index.md)
