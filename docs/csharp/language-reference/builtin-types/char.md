---
title: typ znaku – odkaz jazyka C#
ms.date: 11/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: c4e29e6437edfe549b36a04a2050f63caa0d3d2a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846519"
---
# <a name="char-c-reference"></a><span data-ttu-id="df7f5-102">char (odkaz C#)</span><span class="sxs-lookup"><span data-stu-id="df7f5-102">char (C# reference)</span></span>

<span data-ttu-id="df7f5-103">Klíčové `char` slovo type je alias <xref:System.Char?displayProperty=nameWithType> pro typ struktury .NET, který představuje znak Unicode UTF-16.</span><span class="sxs-lookup"><span data-stu-id="df7f5-103">The `char` type keyword is an alias for the .NET <xref:System.Char?displayProperty=nameWithType> structure type that represents a Unicode UTF-16 character.</span></span>

|<span data-ttu-id="df7f5-104">Typ</span><span class="sxs-lookup"><span data-stu-id="df7f5-104">Type</span></span>|<span data-ttu-id="df7f5-105">Rozsah</span><span class="sxs-lookup"><span data-stu-id="df7f5-105">Range</span></span>|<span data-ttu-id="df7f5-106">Velikost</span><span class="sxs-lookup"><span data-stu-id="df7f5-106">Size</span></span>|<span data-ttu-id="df7f5-107">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="df7f5-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="df7f5-108">U+0000 až U+FFFF</span><span class="sxs-lookup"><span data-stu-id="df7f5-108">U+0000 to U+FFFF</span></span>|<span data-ttu-id="df7f5-109">16 bitů</span><span class="sxs-lookup"><span data-stu-id="df7f5-109">16 bit</span></span>|<xref:System.Char?displayProperty=nameWithType>|

<span data-ttu-id="df7f5-110">Výchozí hodnota `char` typu je `\0`, to znamená U + 0000.</span><span class="sxs-lookup"><span data-stu-id="df7f5-110">The default value of the `char` type is `\0`, that is, U+0000.</span></span>

<span data-ttu-id="df7f5-111">Typ [řetězce](reference-types.md#the-string-type) představuje text jako `char` posloupnost hodnot.</span><span class="sxs-lookup"><span data-stu-id="df7f5-111">The [string](reference-types.md#the-string-type) type represents text as a sequence of `char` values.</span></span>

## <a name="literals"></a><span data-ttu-id="df7f5-112">Literály</span><span class="sxs-lookup"><span data-stu-id="df7f5-112">Literals</span></span>

<span data-ttu-id="df7f5-113">Hodnotu `char` můžete zadat pomocí:</span><span class="sxs-lookup"><span data-stu-id="df7f5-113">You can specify a `char` value with:</span></span>

- <span data-ttu-id="df7f5-114">znak literál.</span><span class="sxs-lookup"><span data-stu-id="df7f5-114">a character literal.</span></span>
- <span data-ttu-id="df7f5-115">řídicí sekvence Unicode, `\u` po níž následuje šestnáctková reprezentace znakového kódu se čtyřmi symboly.</span><span class="sxs-lookup"><span data-stu-id="df7f5-115">a Unicode escape sequence, which is `\u` followed by the four-symbol hexadecimal representation of a character code.</span></span>
- <span data-ttu-id="df7f5-116">šestnáctková escape sekvence, `\x` po které následuje šestnáctkové znázornění znakového kódu.</span><span class="sxs-lookup"><span data-stu-id="df7f5-116">a hexadecimal escape sequence, which is `\x` followed by the hexadecimal representation of a character code.</span></span>

[!code-csharp-interactive[char literals](snippets/CharType.cs#Literals)]

<span data-ttu-id="df7f5-117">Jak ukazuje předchozí příklad, můžete také přetypovat hodnotu `char` kódu znaku do odpovídající hodnoty.</span><span class="sxs-lookup"><span data-stu-id="df7f5-117">As the preceding example shows, you also can cast the value of a character code into the corresponding `char` value.</span></span>

> [!NOTE]
> <span data-ttu-id="df7f5-118">V případě sekvence escape Unicode je nutné zadat všechny čtyři šestnáctkové číslice.</span><span class="sxs-lookup"><span data-stu-id="df7f5-118">In the case of a Unicode escape sequence, you must specify all four hexadecimal digits.</span></span> <span data-ttu-id="df7f5-119">To znamená, `\u006A` že je platná `\u06A` `\u6A` sekvence escape, zatímco a nejsou platné.</span><span class="sxs-lookup"><span data-stu-id="df7f5-119">That is, `\u006A` is a valid escape sequence, while `\u06A` and `\u6A` are not valid.</span></span>
>
> <span data-ttu-id="df7f5-120">V případě šestnáctkové únikové sekvence můžete vynechat úvodní nuly.</span><span class="sxs-lookup"><span data-stu-id="df7f5-120">In the case of a hexadecimal escape sequence, you can omit the leading zeros.</span></span> <span data-ttu-id="df7f5-121">To znamená `\x006A`, `\x06A`, `\x6A` a escape sekvence jsou platné a odpovídají stejnému znaku.</span><span class="sxs-lookup"><span data-stu-id="df7f5-121">That is, the `\x006A`, `\x06A`, and `\x6A` escape sequences are valid and correspond to the same character.</span></span>

## <a name="conversions"></a><span data-ttu-id="df7f5-122">Převody</span><span class="sxs-lookup"><span data-stu-id="df7f5-122">Conversions</span></span>

<span data-ttu-id="df7f5-123">Typ `char` je implicitně převoditelný na `int`následující `uint` `long` [integrální](integral-numeric-types.md) typy: `ushort`, , , a `ulong`.</span><span class="sxs-lookup"><span data-stu-id="df7f5-123">The `char` type is implicitly convertible to the following [integral](integral-numeric-types.md) types: `ushort`, `int`, `uint`, `long`, and `ulong`.</span></span> <span data-ttu-id="df7f5-124">Je také implicitně převoditelný na předdefinované číselné `float` `double`typy `decimal` [s plovoucí desetinnou desetinnou desetinnou desetinnou hodnotou:](floating-point-numeric-types.md) , , a .</span><span class="sxs-lookup"><span data-stu-id="df7f5-124">It's also implicitly convertible to the built-in [floating-point](floating-point-numeric-types.md) numeric types: `float`, `double`, and `decimal`.</span></span> <span data-ttu-id="df7f5-125">Je explicitně převoditelný na `sbyte`, `byte`a `short` integrální typy.</span><span class="sxs-lookup"><span data-stu-id="df7f5-125">It's explicitly convertible to `sbyte`, `byte`, and `short` integral types.</span></span>

<span data-ttu-id="df7f5-126">Neexistují žádné implicitní převody z `char` jiných typů na typ.</span><span class="sxs-lookup"><span data-stu-id="df7f5-126">There are no implicit conversions from other types to the `char` type.</span></span> <span data-ttu-id="df7f5-127">Všechny [integrální](integral-numeric-types.md) nebo [plovoucí desetinné](floating-point-numeric-types.md) číselné typy je však explicitně převodonvertorní na `char`.</span><span class="sxs-lookup"><span data-stu-id="df7f5-127">However, any [integral](integral-numeric-types.md) or [floating-point](floating-point-numeric-types.md) numeric type is explicitly convertible to `char`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="df7f5-128">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="df7f5-128">C# language specification</span></span>

<span data-ttu-id="df7f5-129">Další informace naleznete [v](~/_csharplang/spec/types.md#integral-types) části Integral types ve [specifikaci jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="df7f5-129">For more information, see the [Integral types](~/_csharplang/spec/types.md#integral-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="df7f5-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="df7f5-130">See also</span></span>

- [<span data-ttu-id="df7f5-131">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="df7f5-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="df7f5-132">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="df7f5-132">Value types</span></span>](value-types.md)
- [<span data-ttu-id="df7f5-133">Řetězce</span><span class="sxs-lookup"><span data-stu-id="df7f5-133">Strings</span></span>](../../programming-guide/strings/index.md)
- <xref:System.Text.Rune?displayProperty=nameWithType>
