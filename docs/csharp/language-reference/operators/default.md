---
title: výchozí C# reference operátoru
description: Použití výchozího operátoru k vytvoření výchozí hodnoty typu
ms.date: 08/01/2019
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: ba4c02caa53a9d532be4012a4543a25cd41b6023
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239310"
---
# <a name="default-operator-c-reference"></a><span data-ttu-id="54ab5-103">Default – operátorC# (Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="54ab5-103">default operator (C# reference)</span></span>

<span data-ttu-id="54ab5-104">Operátor `default` vytváří [výchozí hodnotu](../builtin-types/default-values.md) typu.</span><span class="sxs-lookup"><span data-stu-id="54ab5-104">The `default` operator produces the [default value](../builtin-types/default-values.md) of a type.</span></span> <span data-ttu-id="54ab5-105">Argument operátoru `default` musí být název typu nebo parametr typu.</span><span class="sxs-lookup"><span data-stu-id="54ab5-105">The argument to the `default` operator must be the name of a type or a type parameter.</span></span>

<span data-ttu-id="54ab5-106">Následující příklad ukazuje použití operátoru `default`:</span><span class="sxs-lookup"><span data-stu-id="54ab5-106">The following example shows the usage of the `default` operator:</span></span>

[!code-csharp-interactive[default of T](~/samples/snippets/csharp/language-reference/operators/DefaultOperator.cs#WithOperand)]

<span data-ttu-id="54ab5-107">Klíčové slovo `default` lze také použít jako výchozí popisek Case v rámci [příkazu`switch`](../keywords/switch.md).</span><span class="sxs-lookup"><span data-stu-id="54ab5-107">You also use the `default` keyword as the default case label within a [`switch` statement](../keywords/switch.md).</span></span>

## <a name="default-literal"></a><span data-ttu-id="54ab5-108">výchozí literál</span><span class="sxs-lookup"><span data-stu-id="54ab5-108">default literal</span></span>

<span data-ttu-id="54ab5-109">Počínaje C# 7,1 můžete použít literál `default` k vytvoření výchozí hodnoty typu, když kompilátor může odvodit typ výrazu.</span><span class="sxs-lookup"><span data-stu-id="54ab5-109">Beginning with C# 7.1, you can use the `default` literal to produce the default value of a type when the compiler can infer the expression type.</span></span> <span data-ttu-id="54ab5-110">Výraz literálu `default` vytvoří stejnou hodnotu jako výraz `default(T)`, kde `T` je odvozený typ.</span><span class="sxs-lookup"><span data-stu-id="54ab5-110">The `default` literal expression produces the same value as the `default(T)` expression where `T` is the inferred type.</span></span> <span data-ttu-id="54ab5-111">Literál `default` lze použít v některém z následujících případů:</span><span class="sxs-lookup"><span data-stu-id="54ab5-111">You can use the `default` literal in any of the following cases:</span></span>

- <span data-ttu-id="54ab5-112">V přiřazení nebo inicializaci proměnné.</span><span class="sxs-lookup"><span data-stu-id="54ab5-112">In the assignment or initialization of a variable.</span></span>
- <span data-ttu-id="54ab5-113">V deklaraci výchozí hodnoty pro [volitelný parametr metody](../../methods.md#optional-parameters-and-arguments).</span><span class="sxs-lookup"><span data-stu-id="54ab5-113">In the declaration of the default value for an [optional method parameter](../../methods.md#optional-parameters-and-arguments).</span></span>
- <span data-ttu-id="54ab5-114">V volání metody pro poskytnutí hodnoty argumentu.</span><span class="sxs-lookup"><span data-stu-id="54ab5-114">In a method call to provide an argument value.</span></span>
- <span data-ttu-id="54ab5-115">V [příkazu`return`](../keywords/return.md) nebo jako výraz v [členu Expression-těle](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="54ab5-115">In a [`return` statement](../keywords/return.md) or as an expression in an [expression-bodied member](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

<span data-ttu-id="54ab5-116">Následující příklad ukazuje použití `default` literálu:</span><span class="sxs-lookup"><span data-stu-id="54ab5-116">The following example shows the usage of the `default` literal:</span></span>

[!code-csharp-interactive[default literal](~/samples/snippets/csharp/language-reference/operators/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a><span data-ttu-id="54ab5-117">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="54ab5-117">C# language specification</span></span>

<span data-ttu-id="54ab5-118">Další informace naleznete v oddílu [výchozí hodnoty výrazů](~/_csharplang/spec/expressions.md#default-value-expressions) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="54ab5-118">For more information, see the [Default value expressions](~/_csharplang/spec/expressions.md#default-value-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="54ab5-119">Další informace o `default` literálu naleznete v [poznámkách k návrhu funkcí](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span><span class="sxs-lookup"><span data-stu-id="54ab5-119">For more information about the `default` literal, see the [feature proposal note](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="54ab5-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="54ab5-120">See also</span></span>

- [<span data-ttu-id="54ab5-121">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="54ab5-121">C# reference</span></span>](../index.md)
- [<span data-ttu-id="54ab5-122">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="54ab5-122">C# operators</span></span>](index.md)
- [<span data-ttu-id="54ab5-123">Výchozí hodnoty C# typů</span><span class="sxs-lookup"><span data-stu-id="54ab5-123">Default values of C# types</span></span>](../builtin-types/default-values.md)
- [<span data-ttu-id="54ab5-124">Obecné typy v .NET</span><span class="sxs-lookup"><span data-stu-id="54ab5-124">Generics in .NET</span></span>](../../../standard/generics/index.md)
