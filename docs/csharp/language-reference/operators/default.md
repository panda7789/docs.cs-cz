---
title: výchozí výrazy hodnot – odkaz jazyka C#
description: Použití výrazů výchozí hodnoty k získání výchozí hodnoty typu
ms.date: 03/13/2020
f1_keywords:
- default_CSharpKeyword
- default
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 2adfd8d24066e9dad50c3c18407d3ade71b4b68e
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507175"
---
# <a name="default-value-expressions-c-reference"></a><span data-ttu-id="0be2e-103">výchozí výrazy hodnot (odkaz C#</span><span class="sxs-lookup"><span data-stu-id="0be2e-103">default value expressions (C# reference)</span></span>

<span data-ttu-id="0be2e-104">Výchozí hodnota výrazu vytváří [výchozí hodnotu](../builtin-types/default-values.md) typu.</span><span class="sxs-lookup"><span data-stu-id="0be2e-104">A default value expression produces the [default value](../builtin-types/default-values.md) of a type.</span></span> <span data-ttu-id="0be2e-105">Existují dva druhy výchozích výrazů hodnoty: [volání výchozího operátora](#default-operator) a [výchozí literál](#default-literal).</span><span class="sxs-lookup"><span data-stu-id="0be2e-105">There are two kinds of default value expressions: the [default operator](#default-operator) call and a [default literal](#default-literal).</span></span>

<span data-ttu-id="0be2e-106">`default` Klíčové slovo můžete také použít jako výchozí popisek případu v rámci [ `switch` příkazu](../keywords/switch.md).</span><span class="sxs-lookup"><span data-stu-id="0be2e-106">You also use the `default` keyword as the default case label within a [`switch` statement](../keywords/switch.md).</span></span>

## <a name="default-operator"></a><span data-ttu-id="0be2e-107">default – operátor</span><span class="sxs-lookup"><span data-stu-id="0be2e-107">default operator</span></span>

<span data-ttu-id="0be2e-108">Argument pro `default` operátor musí být název typu nebo parametr typu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="0be2e-108">The argument to the `default` operator must be the name of a type or a type parameter, as the following example shows:</span></span>

[!code-csharp-interactive[default of T](snippets/DefaultOperator.cs#WithOperand)]

## <a name="default-literal"></a><span data-ttu-id="0be2e-109">výchozí literál</span><span class="sxs-lookup"><span data-stu-id="0be2e-109">default literal</span></span>

<span data-ttu-id="0be2e-110">Počínaje C# 7.1, můžete `default` použít literál k vytvoření výchozí hodnoty typu, když kompilátor může odvodit typ výrazu.</span><span class="sxs-lookup"><span data-stu-id="0be2e-110">Beginning with C# 7.1, you can use the `default` literal to produce the default value of a type when the compiler can infer the expression type.</span></span> <span data-ttu-id="0be2e-111">Výraz `default` literálu vytváří stejnou hodnotu jako výraz, `default(T)` kde `T` je odvozený typ.</span><span class="sxs-lookup"><span data-stu-id="0be2e-111">The `default` literal expression produces the same value as the `default(T)` expression where `T` is the inferred type.</span></span> <span data-ttu-id="0be2e-112">Literál `default` můžete použít v některém z následujících případů:</span><span class="sxs-lookup"><span data-stu-id="0be2e-112">You can use the `default` literal in any of the following cases:</span></span>

- <span data-ttu-id="0be2e-113">Při přiřazení nebo inicializaci proměnné.</span><span class="sxs-lookup"><span data-stu-id="0be2e-113">In the assignment or initialization of a variable.</span></span>
- <span data-ttu-id="0be2e-114">V deklaraci výchozí hodnoty pro [parametr volitelné metody](../../methods.md#optional-parameters-and-arguments).</span><span class="sxs-lookup"><span data-stu-id="0be2e-114">In the declaration of the default value for an [optional method parameter](../../methods.md#optional-parameters-and-arguments).</span></span>
- <span data-ttu-id="0be2e-115">V volání metody poskytnout hodnotu argument.</span><span class="sxs-lookup"><span data-stu-id="0be2e-115">In a method call to provide an argument value.</span></span>
- <span data-ttu-id="0be2e-116">V [ `return` příkazu](../keywords/return.md) nebo jako výraz v [členu s výrazem](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="0be2e-116">In a [`return` statement](../keywords/return.md) or as an expression in an [expression-bodied member](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

<span data-ttu-id="0be2e-117">Následující příklad ukazuje použití `default` literálu:</span><span class="sxs-lookup"><span data-stu-id="0be2e-117">The following example shows the usage of the `default` literal:</span></span>

[!code-csharp-interactive[default literal](snippets/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a><span data-ttu-id="0be2e-118">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0be2e-118">C# language specification</span></span>

<span data-ttu-id="0be2e-119">Další informace naleznete v části [Výchozí výrazy hodnot](~/_csharplang/spec/expressions.md#default-value-expressions) [ve specifikaci jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="0be2e-119">For more information, see the [Default value expressions](~/_csharplang/spec/expressions.md#default-value-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="0be2e-120">Další informace o `default` literálu naleznete v [poznámce k návrhu funkce](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span><span class="sxs-lookup"><span data-stu-id="0be2e-120">For more information about the `default` literal, see the [feature proposal note](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0be2e-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="0be2e-121">See also</span></span>

- [<span data-ttu-id="0be2e-122">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="0be2e-122">C# reference</span></span>](../index.md)
- [<span data-ttu-id="0be2e-123">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0be2e-123">C# operators</span></span>](index.md)
- [<span data-ttu-id="0be2e-124">Výchozí hodnoty typů jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0be2e-124">Default values of C# types</span></span>](../builtin-types/default-values.md)
- [<span data-ttu-id="0be2e-125">Obecné typy v .NET</span><span class="sxs-lookup"><span data-stu-id="0be2e-125">Generics in .NET</span></span>](../../../standard/generics/index.md)
