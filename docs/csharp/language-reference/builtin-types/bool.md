---
title: bool typ - C# odkaz
ms.date: 11/26/2019
f1_keywords:
- bool
- bool_CSharpKeyword
helpviewer_keywords:
- bool data type [C#]
- Boolean [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 2ba2e54a6b0f24402fc3728dfe19b548a2368830
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846442"
---
# <a name="bool-c-reference"></a><span data-ttu-id="62e32-102">bool (odkaz C#)</span><span class="sxs-lookup"><span data-stu-id="62e32-102">bool (C# reference)</span></span>

<span data-ttu-id="62e32-103">Klíčové `bool` slovo typu je alias <xref:System.Boolean?displayProperty=nameWithType> pro typ struktury .NET, který představuje `true` `false`logickou hodnotu, která může být buď nebo .</span><span class="sxs-lookup"><span data-stu-id="62e32-103">The `bool` type keyword is an alias for the .NET <xref:System.Boolean?displayProperty=nameWithType> structure type that represents a Boolean value, which can be either `true` or `false`.</span></span>

<span data-ttu-id="62e32-104">Chcete-li provádět logické `bool` operace s hodnotami typu, použijte logické operátory [logické hodnoty.](../operators/boolean-logical-operators.md)</span><span class="sxs-lookup"><span data-stu-id="62e32-104">To perform logical operations with values of the `bool` type, use [Boolean logical](../operators/boolean-logical-operators.md) operators.</span></span> <span data-ttu-id="62e32-105">Typ `bool` je výsledek typ [porovnání](../operators/comparison-operators.md) a [rovnosti](../operators/equality-operators.md) operátory.</span><span class="sxs-lookup"><span data-stu-id="62e32-105">The `bool` type is the result type of [comparison](../operators/comparison-operators.md) and [equality](../operators/equality-operators.md) operators.</span></span> <span data-ttu-id="62e32-106">Výraz `bool` může být řídící podmíněný výraz v [if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md)a [for](../keywords/for.md) statements a v [podmíněném `?:`operátoru ](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="62e32-106">A `bool` expression can be a controlling conditional expression in the [if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md), and [for](../keywords/for.md) statements and in the [conditional operator `?:`](../operators/conditional-operator.md).</span></span>

<span data-ttu-id="62e32-107">Výchozí hodnota `bool` typu je `false`.</span><span class="sxs-lookup"><span data-stu-id="62e32-107">The default value of the `bool` type is `false`.</span></span>

## <a name="literals"></a><span data-ttu-id="62e32-108">Literály</span><span class="sxs-lookup"><span data-stu-id="62e32-108">Literals</span></span>

<span data-ttu-id="62e32-109">Literály `true` a `false` můžete použít k inicializaci `bool` proměnné `bool` nebo k předání hodnoty:</span><span class="sxs-lookup"><span data-stu-id="62e32-109">You can use the `true` and `false` literals to initialize a `bool` variable or to pass a `bool` value:</span></span>

[!code-csharp-interactive[bool literals](snippets/BoolType.cs#Literals)]

## <a name="three-valued-boolean-logic"></a><span data-ttu-id="62e32-110">Trojcenná logická logika</span><span class="sxs-lookup"><span data-stu-id="62e32-110">Three-valued Boolean logic</span></span>

<span data-ttu-id="62e32-111">Použijte typ `bool?` s možnou hodnotou null, pokud potřebujete podporovat logiku se třemi hodnotami, například při práci s databázemi, které podporují tříhodnotný logický typ.</span><span class="sxs-lookup"><span data-stu-id="62e32-111">Use the nullable `bool?` type, if you need to support the three-valued logic, for example, when you work with databases that support a three-valued Boolean type.</span></span> <span data-ttu-id="62e32-112">Pro `bool?` operandy předdefinované `&` a `|` operátory podporují logiku se třemi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="62e32-112">For the `bool?` operands, the predefined `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="62e32-113">Další informace naleznete v části [Nullable Boolean logické operátory](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) článku [logické operátory logické.](../operators/boolean-logical-operators.md)</span><span class="sxs-lookup"><span data-stu-id="62e32-113">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

<span data-ttu-id="62e32-114">Další informace o typech hodnot s možnou hodnotou s možnou hodnotou null naleznete v [tématu Nullable typy hodnot](nullable-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="62e32-114">For more information about nullable value types, see [Nullable value types](nullable-value-types.md).</span></span>

## <a name="conversions"></a><span data-ttu-id="62e32-115">Převody</span><span class="sxs-lookup"><span data-stu-id="62e32-115">Conversions</span></span>

<span data-ttu-id="62e32-116">C# poskytuje pouze dva převody, které zahrnují `bool` typ.</span><span class="sxs-lookup"><span data-stu-id="62e32-116">C# provides only two conversions that involve the `bool` type.</span></span> <span data-ttu-id="62e32-117">Jedná se o implicitní převod `bool?` na odpovídající typ `bool?` s možnou hodnotou null a explicitní převod z typu.</span><span class="sxs-lookup"><span data-stu-id="62e32-117">Those are an implicit conversion to the corresponding nullable `bool?` type and an explicit conversion from the `bool?` type.</span></span> <span data-ttu-id="62e32-118">Síť .NET však poskytuje další metody, které `bool` můžete použít k převodu na nebo z typu.</span><span class="sxs-lookup"><span data-stu-id="62e32-118">However, .NET provides additional methods that you can use to convert to or from the `bool` type.</span></span> <span data-ttu-id="62e32-119">Další informace naleznete v části [Převod do a z logické hodnoty](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) na referenční stránce <xref:System.Boolean?displayProperty=nameWithType> rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="62e32-119">For more information, see the [Converting to and from Boolean values](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) section of the <xref:System.Boolean?displayProperty=nameWithType> API reference page.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="62e32-120">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="62e32-120">C# language specification</span></span>

<span data-ttu-id="62e32-121">Další informace naleznete v části [Bool typ](~/_csharplang/spec/types.md#the-bool-type) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="62e32-121">For more information, see [The bool type](~/_csharplang/spec/types.md#the-bool-type) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="62e32-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="62e32-122">See also</span></span>

- [<span data-ttu-id="62e32-123">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="62e32-123">C# reference</span></span>](../index.md)
- [<span data-ttu-id="62e32-124">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="62e32-124">Value types</span></span>](value-types.md)
- [<span data-ttu-id="62e32-125">true a false – operátory</span><span class="sxs-lookup"><span data-stu-id="62e32-125">true and false operators</span></span>](../operators/true-false-operators.md)
