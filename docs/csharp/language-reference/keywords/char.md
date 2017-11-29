---
title: "char (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords: char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
caps.latest.revision: "27"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 41f672e9b12481fa5cce78015e95d2c5245a26db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="char-c-reference"></a><span data-ttu-id="a23b0-102">char (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="a23b0-102">char (C# Reference)</span></span>
<span data-ttu-id="a23b0-103">`char` – Klíčové slovo se používá k deklaraci instance <xref:System.Char?displayProperty=nameWithType> struktura, která rozhraní .NET Framework se používá k reprezentaci znak Unicode.</span><span class="sxs-lookup"><span data-stu-id="a23b0-103">The `char` keyword is used to declare an instance of the <xref:System.Char?displayProperty=nameWithType> structure that the .NET Framework uses to represent a Unicode character.</span></span> <span data-ttu-id="a23b0-104">Hodnota `Char` objekt je hodnotu numerické 16bitové (pořadí).</span><span class="sxs-lookup"><span data-stu-id="a23b0-104">The value of a `Char` object is a 16-bit numeric (ordinal) value.</span></span>  
  
 <span data-ttu-id="a23b0-105">Znaky kódování Unicode se používají k vyjádření většinu psané jazyky po celém světě.</span><span class="sxs-lookup"><span data-stu-id="a23b0-105">Unicode characters are used to represent most of the written languages throughout the world.</span></span>  
  
|<span data-ttu-id="a23b0-106">Typ</span><span class="sxs-lookup"><span data-stu-id="a23b0-106">Type</span></span>|<span data-ttu-id="a23b0-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="a23b0-107">Range</span></span>|<span data-ttu-id="a23b0-108">Velikost</span><span class="sxs-lookup"><span data-stu-id="a23b0-108">Size</span></span>|<span data-ttu-id="a23b0-109">Typ rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a23b0-109">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`char`|<span data-ttu-id="a23b0-110">U + 0000 U + FFFF</span><span class="sxs-lookup"><span data-stu-id="a23b0-110">U+0000 to U+FFFF</span></span>|<span data-ttu-id="a23b0-111">16bitové znak Unicode</span><span class="sxs-lookup"><span data-stu-id="a23b0-111">Unicode 16-bit character</span></span>|<xref:System.Char?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="a23b0-112">Literály</span><span class="sxs-lookup"><span data-stu-id="a23b0-112">Literals</span></span>  
 <span data-ttu-id="a23b0-113">Konstanty z `char` typu lze zapsat jako znakové literály, šestnáctková řídicí sekvence nebo reprezentace kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="a23b0-113">Constants of the `char` type can be written as character literals, hexadecimal escape sequence, or Unicode representation.</span></span> <span data-ttu-id="a23b0-114">Můžete také přetypování kódy integrální znaků.</span><span class="sxs-lookup"><span data-stu-id="a23b0-114">You can also cast the integral character codes.</span></span> <span data-ttu-id="a23b0-115">V následujícím příkladu čtyři `char` proměnné se inicializují ve stejném `X`:</span><span class="sxs-lookup"><span data-stu-id="a23b0-115">In the following example four `char` variables are initialized with the same character `X`:</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/char_1.cs)]  
  
## <a name="conversions"></a><span data-ttu-id="a23b0-116">Převody</span><span class="sxs-lookup"><span data-stu-id="a23b0-116">Conversions</span></span>  
 <span data-ttu-id="a23b0-117">A `char` může být implicitně převedena na [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [Celé_číslo](../../../csharp/language-reference/keywords/uint.md), [dlouho](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md) , [float](../../../csharp/language-reference/keywords/float.md), [dvojité](../../../csharp/language-reference/keywords/double.md), nebo [decimal](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="a23b0-117">A `char` can be implicitly converted to [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="a23b0-118">Existují však žádná implicitní převody z ostatních typů k `char` typu.</span><span class="sxs-lookup"><span data-stu-id="a23b0-118">However, there are no implicit conversions from other types to the `char` type.</span></span>  
  
 <span data-ttu-id="a23b0-119"><xref:System.Char?displayProperty=nameWithType> Typu poskytuje několik statické metody pro práci s `char` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a23b0-119">The <xref:System.Char?displayProperty=nameWithType> type provides several static methods for working with `char` values.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="a23b0-120">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a23b0-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a23b0-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="a23b0-121">See Also</span></span>  
 <xref:System.Char>  
 [<span data-ttu-id="a23b0-122">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a23b0-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a23b0-123">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="a23b0-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a23b0-124">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a23b0-124">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="a23b0-125">Tabulka celočíselných typů</span><span class="sxs-lookup"><span data-stu-id="a23b0-125">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="a23b0-126">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="a23b0-126">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="a23b0-127">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="a23b0-127">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="a23b0-128">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="a23b0-128">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
 [<span data-ttu-id="a23b0-129">Typy s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="a23b0-129">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="a23b0-130">Řetězce</span><span class="sxs-lookup"><span data-stu-id="a23b0-130">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)
