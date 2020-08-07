---
title: výrazy výchozích hodnot – reference jazyka C#
description: Použití výchozích hodnotových výrazů k získání výchozí hodnoty typu
ms.date: 03/13/2020
f1_keywords:
- default_CSharpKeyword
- default
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: f03971efa87bf03967c79512e44d22134dd80c17
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916863"
---
# <a name="default-value-expressions-c-reference"></a><span data-ttu-id="e9de2-103">výrazy výchozích hodnot (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e9de2-103">default value expressions (C# reference)</span></span>

<span data-ttu-id="e9de2-104">Výchozí hodnota výrazu vytvoří [výchozí hodnotu](../builtin-types/default-values.md) typu.</span><span class="sxs-lookup"><span data-stu-id="e9de2-104">A default value expression produces the [default value](../builtin-types/default-values.md) of a type.</span></span> <span data-ttu-id="e9de2-105">Existují dva druhy výchozích hodnot výrazů: [výchozí volání operátoru](#default-operator) a [výchozí literál](#default-literal).</span><span class="sxs-lookup"><span data-stu-id="e9de2-105">There are two kinds of default value expressions: the [default operator](#default-operator) call and a [default literal](#default-literal).</span></span>

<span data-ttu-id="e9de2-106">Klíčové slovo se používá také `default` jako výchozí popisek Case v rámci [ `switch` příkazu](../keywords/switch.md).</span><span class="sxs-lookup"><span data-stu-id="e9de2-106">You also use the `default` keyword as the default case label within a [`switch` statement](../keywords/switch.md).</span></span>

## <a name="default-operator"></a><span data-ttu-id="e9de2-107">default – operátor</span><span class="sxs-lookup"><span data-stu-id="e9de2-107">default operator</span></span>

<span data-ttu-id="e9de2-108">Argument `default` operátoru musí být název typu nebo parametr typu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="e9de2-108">The argument to the `default` operator must be the name of a type or a type parameter, as the following example shows:</span></span>

[!code-csharp-interactive[default of T](snippets/shared/DefaultOperator.cs#WithOperand)]

## <a name="default-literal"></a><span data-ttu-id="e9de2-109">výchozí literál</span><span class="sxs-lookup"><span data-stu-id="e9de2-109">default literal</span></span>

<span data-ttu-id="e9de2-110">Počínaje jazykem C# 7,1 můžete použít `default` literál pro vytvoření výchozí hodnoty typu, když kompilátor může odvodit typ výrazu.</span><span class="sxs-lookup"><span data-stu-id="e9de2-110">Beginning with C# 7.1, you can use the `default` literal to produce the default value of a type when the compiler can infer the expression type.</span></span> <span data-ttu-id="e9de2-111">`default`Literálový výraz vytvoří stejnou hodnotu jako výraz, `default(T)` ve kterém `T` je odvozený typ.</span><span class="sxs-lookup"><span data-stu-id="e9de2-111">The `default` literal expression produces the same value as the `default(T)` expression where `T` is the inferred type.</span></span> <span data-ttu-id="e9de2-112">Literál můžete použít `default` v některém z následujících případů:</span><span class="sxs-lookup"><span data-stu-id="e9de2-112">You can use the `default` literal in any of the following cases:</span></span>

- <span data-ttu-id="e9de2-113">V přiřazení nebo inicializaci proměnné.</span><span class="sxs-lookup"><span data-stu-id="e9de2-113">In the assignment or initialization of a variable.</span></span>
- <span data-ttu-id="e9de2-114">V deklaraci výchozí hodnoty pro [volitelný parametr metody](../../methods.md#optional-parameters-and-arguments).</span><span class="sxs-lookup"><span data-stu-id="e9de2-114">In the declaration of the default value for an [optional method parameter](../../methods.md#optional-parameters-and-arguments).</span></span>
- <span data-ttu-id="e9de2-115">V volání metody pro poskytnutí hodnoty argumentu.</span><span class="sxs-lookup"><span data-stu-id="e9de2-115">In a method call to provide an argument value.</span></span>
- <span data-ttu-id="e9de2-116">V [ `return` příkazu](../keywords/return.md) nebo jako výraz v [členu Expression-těle](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="e9de2-116">In a [`return` statement](../keywords/return.md) or as an expression in an [expression-bodied member](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

<span data-ttu-id="e9de2-117">Následující příklad ukazuje použití `default` literálu:</span><span class="sxs-lookup"><span data-stu-id="e9de2-117">The following example shows the usage of the `default` literal:</span></span>

[!code-csharp-interactive[default literal](snippets/shared/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a><span data-ttu-id="e9de2-118">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e9de2-118">C# language specification</span></span>

<span data-ttu-id="e9de2-119">Další informace naleznete v oddílu [výchozí hodnoty Expressions](~/_csharplang/spec/expressions.md#default-value-expressions) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="e9de2-119">For more information, see the [Default value expressions](~/_csharplang/spec/expressions.md#default-value-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="e9de2-120">Další informace o `default` literálu naleznete v [poznámkách k návrhu funkcí](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span><span class="sxs-lookup"><span data-stu-id="e9de2-120">For more information about the `default` literal, see the [feature proposal note](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e9de2-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9de2-121">See also</span></span>

- [<span data-ttu-id="e9de2-122">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="e9de2-122">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e9de2-123">Operátory a výrazy v C#</span><span class="sxs-lookup"><span data-stu-id="e9de2-123">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="e9de2-124">Výchozí hodnoty typů C#</span><span class="sxs-lookup"><span data-stu-id="e9de2-124">Default values of C# types</span></span>](../builtin-types/default-values.md)
- [<span data-ttu-id="e9de2-125">Obecné typy v .NET</span><span class="sxs-lookup"><span data-stu-id="e9de2-125">Generics in .NET</span></span>](../../../standard/generics/index.md)
