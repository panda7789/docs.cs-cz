---
title: typ char – Referenční dokumentace jazyka C#
ms.date: 05/11/2020
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: f771626e9777deab30e798559d847615d6124e6d
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205783"
---
# <a name="char-c-reference"></a><span data-ttu-id="12350-102">char (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="12350-102">char (C# reference)</span></span>

<span data-ttu-id="12350-103">`char`Klíčové slovo Type je alias pro <xref:System.Char?displayProperty=nameWithType> typ struktury .NET, který představuje znak Unicode UTF-16.</span><span class="sxs-lookup"><span data-stu-id="12350-103">The `char` type keyword is an alias for the .NET <xref:System.Char?displayProperty=nameWithType> structure type that represents a Unicode UTF-16 character.</span></span>

|<span data-ttu-id="12350-104">Typ</span><span class="sxs-lookup"><span data-stu-id="12350-104">Type</span></span>|<span data-ttu-id="12350-105">Rozsah</span><span class="sxs-lookup"><span data-stu-id="12350-105">Range</span></span>|<span data-ttu-id="12350-106">Velikost</span><span class="sxs-lookup"><span data-stu-id="12350-106">Size</span></span>|<span data-ttu-id="12350-107">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="12350-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="12350-108">U + 0000 až U + FFFF</span><span class="sxs-lookup"><span data-stu-id="12350-108">U+0000 to U+FFFF</span></span>|<span data-ttu-id="12350-109">16 bitů</span><span class="sxs-lookup"><span data-stu-id="12350-109">16 bit</span></span>|<xref:System.Char?displayProperty=nameWithType>|

<span data-ttu-id="12350-110">Výchozí hodnota `char` typu je `\0` , tedy U + 0000.</span><span class="sxs-lookup"><span data-stu-id="12350-110">The default value of the `char` type is `\0`, that is, U+0000.</span></span>

<span data-ttu-id="12350-111">`char`Typ podporuje operátory [porovnání](../operators/comparison-operators.md), [rovnosti](../operators/equality-operators.md), [zvýšení](../operators/arithmetic-operators.md#increment-operator-)a [snížení](../operators/arithmetic-operators.md#decrement-operator---) .</span><span class="sxs-lookup"><span data-stu-id="12350-111">The `char` type supports [comparison](../operators/comparison-operators.md), [equality](../operators/equality-operators.md), [increment](../operators/arithmetic-operators.md#increment-operator-), and [decrement](../operators/arithmetic-operators.md#decrement-operator---) operators.</span></span> <span data-ttu-id="12350-112">Kromě toho pro `char` operandy [aritmetické](../operators/arithmetic-operators.md) a [bitové logické](../operators/bitwise-and-shift-operators.md) operátory provádějí operaci s odpovídajícími kódy znaků a vytvoří výsledek `int` typu.</span><span class="sxs-lookup"><span data-stu-id="12350-112">Moreover, for `char` operands, [arithmetic](../operators/arithmetic-operators.md) and [bitwise logical](../operators/bitwise-and-shift-operators.md) operators perform an operation on the corresponding character codes and produce the result of the `int` type.</span></span>

<span data-ttu-id="12350-113">Typ [řetězce](reference-types.md#the-string-type) představuje text jako sekvenci `char` hodnot.</span><span class="sxs-lookup"><span data-stu-id="12350-113">The [string](reference-types.md#the-string-type) type represents text as a sequence of `char` values.</span></span>

## <a name="literals"></a><span data-ttu-id="12350-114">Literály</span><span class="sxs-lookup"><span data-stu-id="12350-114">Literals</span></span>

<span data-ttu-id="12350-115">Hodnotu můžete zadat `char` pomocí:</span><span class="sxs-lookup"><span data-stu-id="12350-115">You can specify a `char` value with:</span></span>

- <span data-ttu-id="12350-116">znakový literál.</span><span class="sxs-lookup"><span data-stu-id="12350-116">a character literal.</span></span>
- <span data-ttu-id="12350-117">řídicí sekvence Unicode, která `\u` následuje hexadecimální reprezentace kódu znaku se čtyřmi symboly.</span><span class="sxs-lookup"><span data-stu-id="12350-117">a Unicode escape sequence, which is `\u` followed by the four-symbol hexadecimal representation of a character code.</span></span>
- <span data-ttu-id="12350-118">šestnáctková řídicí sekvence, která `\x` následuje hexadecimální reprezentace kódu znaku.</span><span class="sxs-lookup"><span data-stu-id="12350-118">a hexadecimal escape sequence, which is `\x` followed by the hexadecimal representation of a character code.</span></span>

[!code-csharp-interactive[char literals](snippets/CharType.cs#Literals)]

<span data-ttu-id="12350-119">Jak ukazuje předchozí příklad, můžete také přetypovat hodnotu kódu znaku na odpovídající `char` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="12350-119">As the preceding example shows, you can also cast the value of a character code into the corresponding `char` value.</span></span>

> [!NOTE]
> <span data-ttu-id="12350-120">V případě řídicí sekvence Unicode je nutné zadat všechny čtyři šestnáctkové číslice.</span><span class="sxs-lookup"><span data-stu-id="12350-120">In the case of a Unicode escape sequence, you must specify all four hexadecimal digits.</span></span> <span data-ttu-id="12350-121">To znamená, že `\u006A` je platná řídicí sekvence, zatímco `\u06A` a `\u6A` nejsou platné.</span><span class="sxs-lookup"><span data-stu-id="12350-121">That is, `\u006A` is a valid escape sequence, while `\u06A` and `\u6A` are not valid.</span></span>
>
> <span data-ttu-id="12350-122">V případě hexadecimální sekvence escape můžete vynechat úvodní nuly.</span><span class="sxs-lookup"><span data-stu-id="12350-122">In the case of a hexadecimal escape sequence, you can omit the leading zeros.</span></span> <span data-ttu-id="12350-123">To znamená, že `\x006A` `\x06A` `\x6A` řídicí sekvence, a jsou platné a odpovídají stejnému znaku.</span><span class="sxs-lookup"><span data-stu-id="12350-123">That is, the `\x006A`, `\x06A`, and `\x6A` escape sequences are valid and correspond to the same character.</span></span>

## <a name="conversions"></a><span data-ttu-id="12350-124">Převody</span><span class="sxs-lookup"><span data-stu-id="12350-124">Conversions</span></span>

<span data-ttu-id="12350-125">`char`Typ je implicitně převoditelné na následující [celočíselné](integral-numeric-types.md) typy: `ushort` , `int` , `uint` , `long` a `ulong` .</span><span class="sxs-lookup"><span data-stu-id="12350-125">The `char` type is implicitly convertible to the following [integral](integral-numeric-types.md) types: `ushort`, `int`, `uint`, `long`, and `ulong`.</span></span> <span data-ttu-id="12350-126">Je také implicitně převoditelné na předdefinované číselné typy s [plovoucí desetinnou](floating-point-numeric-types.md) čárkou: `float` , a `double` `decimal` .</span><span class="sxs-lookup"><span data-stu-id="12350-126">It's also implicitly convertible to the built-in [floating-point](floating-point-numeric-types.md) numeric types: `float`, `double`, and `decimal`.</span></span> <span data-ttu-id="12350-127">Je explicitně převoditelná na `sbyte` , `byte` a `short` integrální typy.</span><span class="sxs-lookup"><span data-stu-id="12350-127">It's explicitly convertible to `sbyte`, `byte`, and `short` integral types.</span></span>

<span data-ttu-id="12350-128">Neexistují žádné implicitní převody z jiných typů na `char` typ.</span><span class="sxs-lookup"><span data-stu-id="12350-128">There are no implicit conversions from other types to the `char` type.</span></span> <span data-ttu-id="12350-129">Jakýkoli [celočíselný](integral-numeric-types.md) typ nebo číslo [s plovoucí desetinnou](floating-point-numeric-types.md) čárkou je však explicitně převoditelné na `char` .</span><span class="sxs-lookup"><span data-stu-id="12350-129">However, any [integral](integral-numeric-types.md) or [floating-point](floating-point-numeric-types.md) numeric type is explicitly convertible to `char`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="12350-130">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="12350-130">C# language specification</span></span>

<span data-ttu-id="12350-131">Další informace naleznete v části [integrální typy](~/_csharplang/spec/types.md#integral-types) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="12350-131">For more information, see the [Integral types](~/_csharplang/spec/types.md#integral-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="12350-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="12350-132">See also</span></span>

- [<span data-ttu-id="12350-133">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="12350-133">C# reference</span></span>](../index.md)
- [<span data-ttu-id="12350-134">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="12350-134">Value types</span></span>](value-types.md)
- [<span data-ttu-id="12350-135">Řetězce</span><span class="sxs-lookup"><span data-stu-id="12350-135">Strings</span></span>](../../programming-guide/strings/index.md)
- <xref:System.Text.Rune?displayProperty=nameWithType>
- [<span data-ttu-id="12350-136">Kódování znaků v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="12350-136">Character encoding in .NET</span></span>](../../../standard/base-types/character-encoding-introduction.md)
