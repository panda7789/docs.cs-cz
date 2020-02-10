---
title: typ bool – C# referenční informace
ms.date: 11/26/2019
f1_keywords:
- bool
- bool_CSharpKeyword
helpviewer_keywords:
- bool data type [C#]
- Boolean [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 720ece2f7f47961e0ab6ebf03c8afeb5fa3a6271
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093263"
---
# <a name="bool-c-reference"></a><span data-ttu-id="79aec-102">bool (C# Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="79aec-102">bool (C# reference)</span></span>

<span data-ttu-id="79aec-103">Klíčové slovo typu `bool` je alias pro typ struktury .NET <xref:System.Boolean?displayProperty=nameWithType>, který představuje logickou hodnotu, která může být buď `true`, nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="79aec-103">The `bool` type keyword is an alias for the .NET <xref:System.Boolean?displayProperty=nameWithType> structure type that represents a Boolean value, which can be either `true` or `false`.</span></span>

<span data-ttu-id="79aec-104">K provedení logických operací s hodnotami `bool`ho typu použijte logické [logické](../operators/boolean-logical-operators.md) operátory.</span><span class="sxs-lookup"><span data-stu-id="79aec-104">To perform logical operations with values of the `bool` type, use [Boolean logical](../operators/boolean-logical-operators.md) operators.</span></span> <span data-ttu-id="79aec-105">Typ `bool` je výsledný typ operátoru [porovnání](../operators/comparison-operators.md) a [rovnosti](../operators/equality-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="79aec-105">The `bool` type is the result type of [comparison](../operators/comparison-operators.md) and [equality](../operators/equality-operators.md) operators.</span></span> <span data-ttu-id="79aec-106">Výraz `bool` může být řídicí podmíněný výraz v příkazech [if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md)a [for](../keywords/for.md) a v [podmíněných operátorech `?:`](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="79aec-106">A `bool` expression can be a controlling conditional expression in the [if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md), and [for](../keywords/for.md) statements and in the [conditional operator `?:`](../operators/conditional-operator.md).</span></span>

<span data-ttu-id="79aec-107">Výchozí hodnota typu `bool` je `false`.</span><span class="sxs-lookup"><span data-stu-id="79aec-107">The default value of the `bool` type is `false`.</span></span>

## <a name="literals"></a><span data-ttu-id="79aec-108">Literály</span><span class="sxs-lookup"><span data-stu-id="79aec-108">Literals</span></span>

<span data-ttu-id="79aec-109">Můžete použít `true` a `false` literály k inicializaci `bool` proměnné nebo pro předání hodnoty `bool`:</span><span class="sxs-lookup"><span data-stu-id="79aec-109">You can use the `true` and `false` literals to initialize a `bool` variable or to pass a `bool` value:</span></span>

[!code-csharp-interactive[bool literals](~/samples/csharp/language-reference/builtin-types/BoolType.cs#Literals)]

## <a name="three-valued-boolean-logic"></a><span data-ttu-id="79aec-110">Logická logika se třemi hodnotami</span><span class="sxs-lookup"><span data-stu-id="79aec-110">Three-valued Boolean logic</span></span>

<span data-ttu-id="79aec-111">Použijte `bool?` typ s možnou hodnotou null, pokud potřebujete podporovat logiku se třemi hodnotami, například při práci s databázemi, které podporují logický typ se třemi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="79aec-111">Use the nullable `bool?` type, if you need to support the three-valued logic, for example, when you work with databases that support a three-valued Boolean type.</span></span> <span data-ttu-id="79aec-112">Pro operandy `bool?` jsou předdefinované operátory `&` a `|` podporovány v rámci logiky se třemi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="79aec-112">For the `bool?` operands, the predefined `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="79aec-113">Další informace naleznete v části s [možnou hodnotou null logických operátorů](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) v článku [Boolean Logical Operators](../operators/boolean-logical-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="79aec-113">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

<span data-ttu-id="79aec-114">Další informace o typech hodnot s možnou hodnotou null naleznete v tématu [typy hodnot s možnou hodnotou null](nullable-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="79aec-114">For more information about nullable value types, see [Nullable value types](nullable-value-types.md).</span></span>

## <a name="conversions"></a><span data-ttu-id="79aec-115">Převody</span><span class="sxs-lookup"><span data-stu-id="79aec-115">Conversions</span></span>

<span data-ttu-id="79aec-116">C#poskytuje pouze dva převody, které zahrnují `bool` typ.</span><span class="sxs-lookup"><span data-stu-id="79aec-116">C# provides only two conversions that involve the `bool` type.</span></span> <span data-ttu-id="79aec-117">Jedná se o implicitní převod na odpovídající typ `bool?` s možnou hodnotou null a explicitní převod z `bool?` typu.</span><span class="sxs-lookup"><span data-stu-id="79aec-117">Those are an implicit conversion to the corresponding nullable `bool?` type and an explicit conversion from the `bool?` type.</span></span> <span data-ttu-id="79aec-118">Nicméně rozhraní .NET poskytuje další metody, které lze použít pro převod na nebo z `bool`ho typu.</span><span class="sxs-lookup"><span data-stu-id="79aec-118">However, .NET provides additional methods that you can use to convert to or from the `bool` type.</span></span> <span data-ttu-id="79aec-119">Další informace naleznete v části [Převod do a z logických hodnot](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) na referenční stránce rozhraní API <xref:System.Boolean?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="79aec-119">For more information, see the [Converting to and from Boolean values](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) section of the <xref:System.Boolean?displayProperty=nameWithType> API reference page.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="79aec-120">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="79aec-120">C# language specification</span></span>

<span data-ttu-id="79aec-121">Další informace naleznete v části [typ bool](~/_csharplang/spec/types.md#the-bool-type) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="79aec-121">For more information, see [The bool type](~/_csharplang/spec/types.md#the-bool-type) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="79aec-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="79aec-122">See also</span></span>

- [<span data-ttu-id="79aec-123">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="79aec-123">C# reference</span></span>](../index.md)
- [<span data-ttu-id="79aec-124">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="79aec-124">Value types</span></span>](value-types.md)
- [<span data-ttu-id="79aec-125">operátory true a false</span><span class="sxs-lookup"><span data-stu-id="79aec-125">true and false operators</span></span>](../operators/true-false-operators.md)
