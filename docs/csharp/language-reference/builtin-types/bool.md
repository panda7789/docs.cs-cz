---
description: 'Seznamte se s předdefinovaným typem Boolean v jazyce C. #'
title: bool – typ – reference jazyka C#
ms.date: 11/26/2019
f1_keywords:
- bool
- bool_CSharpKeyword
- "true"
- "false"
- true_CSharpKeyword
- false_CSharpKeyword
helpviewer_keywords:
- bool data type [C#]
- Boolean [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 23e5bc34f1751b0a706c20dae340920239fcda9d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89126460"
---
# <a name="bool-c-reference"></a><span data-ttu-id="dc564-103">bool (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="dc564-103">bool (C# reference)</span></span>

<span data-ttu-id="dc564-104">`bool`Klíčové slovo Type je alias pro <xref:System.Boolean?displayProperty=nameWithType> typ struktury .NET, který představuje logickou hodnotu, která může být buď `true` nebo `false` .</span><span class="sxs-lookup"><span data-stu-id="dc564-104">The `bool` type keyword is an alias for the .NET <xref:System.Boolean?displayProperty=nameWithType> structure type that represents a Boolean value, which can be either `true` or `false`.</span></span>

<span data-ttu-id="dc564-105">K provádění logických operací s hodnotami `bool` typu použijte logické [logické](../operators/boolean-logical-operators.md) operátory.</span><span class="sxs-lookup"><span data-stu-id="dc564-105">To perform logical operations with values of the `bool` type, use [Boolean logical](../operators/boolean-logical-operators.md) operators.</span></span> <span data-ttu-id="dc564-106">`bool`Typ je výsledný typ operátoru [porovnání](../operators/comparison-operators.md) a [rovnosti](../operators/equality-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="dc564-106">The `bool` type is the result type of [comparison](../operators/comparison-operators.md) and [equality](../operators/equality-operators.md) operators.</span></span> <span data-ttu-id="dc564-107">`bool`Výraz může být řídicí podmíněný výraz v příkazech [if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md)a [for](../keywords/for.md) a v [podmíněných operátorech `?:` ](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="dc564-107">A `bool` expression can be a controlling conditional expression in the [if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md), and [for](../keywords/for.md) statements and in the [conditional operator `?:`](../operators/conditional-operator.md).</span></span>

<span data-ttu-id="dc564-108">Výchozí hodnota `bool` typu je `false` .</span><span class="sxs-lookup"><span data-stu-id="dc564-108">The default value of the `bool` type is `false`.</span></span>

## <a name="literals"></a><span data-ttu-id="dc564-109">Literály</span><span class="sxs-lookup"><span data-stu-id="dc564-109">Literals</span></span>

<span data-ttu-id="dc564-110">`true`Literály a lze použít `false` k inicializaci `bool` proměnné nebo k předání `bool` hodnoty:</span><span class="sxs-lookup"><span data-stu-id="dc564-110">You can use the `true` and `false` literals to initialize a `bool` variable or to pass a `bool` value:</span></span>

[!code-csharp-interactive[bool literals](snippets/BoolType.cs#Literals)]

## <a name="three-valued-boolean-logic"></a><span data-ttu-id="dc564-111">Logická logika se třemi hodnotami</span><span class="sxs-lookup"><span data-stu-id="dc564-111">Three-valued Boolean logic</span></span>

<span data-ttu-id="dc564-112">Typ s povolenou hodnotou null použijte `bool?` , pokud potřebujete podporovat logiku se třemi hodnotami, například když pracujete s databázemi, které podporují logický typ se třemi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="dc564-112">Use the nullable `bool?` type, if you need to support the three-valued logic, for example, when you work with databases that support a three-valued Boolean type.</span></span> <span data-ttu-id="dc564-113">Pro `bool?` operandy, předdefinované `&` a `|` operátory podporují logiku se třemi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="dc564-113">For the `bool?` operands, the predefined `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="dc564-114">Další informace naleznete v části s [možnou hodnotou null logických operátorů](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) v článku [Boolean Logical Operators](../operators/boolean-logical-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="dc564-114">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

<span data-ttu-id="dc564-115">Další informace o typech hodnot s možnou hodnotou null naleznete v tématu [typy hodnot s možnou hodnotou null](nullable-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="dc564-115">For more information about nullable value types, see [Nullable value types](nullable-value-types.md).</span></span>

## <a name="conversions"></a><span data-ttu-id="dc564-116">Převody</span><span class="sxs-lookup"><span data-stu-id="dc564-116">Conversions</span></span>

<span data-ttu-id="dc564-117">Jazyk C# poskytuje pouze dva převody, které obsahují `bool` typ.</span><span class="sxs-lookup"><span data-stu-id="dc564-117">C# provides only two conversions that involve the `bool` type.</span></span> <span data-ttu-id="dc564-118">Jedná se o implicitní převod na odpovídající typ s možnou hodnotou null `bool?` a explicitní převod z `bool?` typu.</span><span class="sxs-lookup"><span data-stu-id="dc564-118">Those are an implicit conversion to the corresponding nullable `bool?` type and an explicit conversion from the `bool?` type.</span></span> <span data-ttu-id="dc564-119">Nicméně rozhraní .NET poskytuje další metody, které lze použít pro převod na nebo z `bool` typu.</span><span class="sxs-lookup"><span data-stu-id="dc564-119">However, .NET provides additional methods that you can use to convert to or from the `bool` type.</span></span> <span data-ttu-id="dc564-120">Další informace naleznete v části [Převod do a z logických hodnot](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) na <xref:System.Boolean?displayProperty=nameWithType> referenční stránce rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="dc564-120">For more information, see the [Converting to and from Boolean values](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) section of the <xref:System.Boolean?displayProperty=nameWithType> API reference page.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="dc564-121">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="dc564-121">C# language specification</span></span>

<span data-ttu-id="dc564-122">Další informace naleznete v části [typ bool](~/_csharplang/spec/types.md#the-bool-type) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="dc564-122">For more information, see [The bool type](~/_csharplang/spec/types.md#the-bool-type) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dc564-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="dc564-123">See also</span></span>

- [<span data-ttu-id="dc564-124">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="dc564-124">C# reference</span></span>](../index.md)
- [<span data-ttu-id="dc564-125">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="dc564-125">Value types</span></span>](value-types.md)
- [<span data-ttu-id="dc564-126">true a false – operátory</span><span class="sxs-lookup"><span data-stu-id="dc564-126">true and false operators</span></span>](../operators/true-false-operators.md)
