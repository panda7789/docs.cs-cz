---
title: výchozí C# reference operátoru
ms.custom: seodec18
description: Použít výchozí operátor k vytvoření výchozí hodnoty typu
ms.date: 08/01/2019
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 5623cb9dc3790b5bb99635c41cb3f122f4c71d8e
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/05/2019
ms.locfileid: "68804238"
---
# <a name="default-operator-c-reference"></a><span data-ttu-id="8cca8-103">Default – operátorC# (Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="8cca8-103">default operator (C# reference)</span></span>

<span data-ttu-id="8cca8-104">Operátor vytvoří [výchozí hodnotu typu.](../keywords/default-values-table.md) `default`</span><span class="sxs-lookup"><span data-stu-id="8cca8-104">The `default` operator produces the [default value](../keywords/default-values-table.md) of a type.</span></span> <span data-ttu-id="8cca8-105">Argument `default` operátoru musí být název typu nebo parametr typu.</span><span class="sxs-lookup"><span data-stu-id="8cca8-105">The argument to the `default` operator must be the name of a type or a type parameter.</span></span>

<span data-ttu-id="8cca8-106">Následující příklad ukazuje použití `default` operátoru:</span><span class="sxs-lookup"><span data-stu-id="8cca8-106">The following example shows the usage of the `default` operator:</span></span>

[!code-csharp-interactive[default of T](~/samples/csharp/language-reference/operators/DefaultOperator.cs#WithOperand)]

<span data-ttu-id="8cca8-107">`default` Klíčové slovo se používá také jako výchozí popisek Case [ `switch` ](../keywords/switch.md)v rámci příkazu.</span><span class="sxs-lookup"><span data-stu-id="8cca8-107">You also use the `default` keyword as the default case label within the [`switch` statement](../keywords/switch.md).</span></span>

## <a name="default-literal"></a><span data-ttu-id="8cca8-108">výchozí literál</span><span class="sxs-lookup"><span data-stu-id="8cca8-108">default literal</span></span>

<span data-ttu-id="8cca8-109">Počínaje C# 7,1 můžete použít `default` literál k vytvoření výchozí hodnoty typu, když kompilátor může odvodit typ výrazu.</span><span class="sxs-lookup"><span data-stu-id="8cca8-109">Beginning with C# 7.1, you can use the `default` literal to produce the default value of a type when the compiler can infer the expression type.</span></span> <span data-ttu-id="8cca8-110">Literálový výraz vytvoří stejnou hodnotu `default(T)` jako výraz, ve kterém `T` je odvozený typ. `default`</span><span class="sxs-lookup"><span data-stu-id="8cca8-110">The `default` literal expression produces the same value as the `default(T)` expression where `T` is the inferred type.</span></span> <span data-ttu-id="8cca8-111">`default` Literál můžete použít v některém z následujících případů:</span><span class="sxs-lookup"><span data-stu-id="8cca8-111">You can use the `default` literal in any of the following cases:</span></span>

- <span data-ttu-id="8cca8-112">V přiřazení nebo inicializaci proměnné.</span><span class="sxs-lookup"><span data-stu-id="8cca8-112">In the assignment or initialization of a variable.</span></span>
- <span data-ttu-id="8cca8-113">V deklaraci výchozí hodnoty pro volitelný parametr metody.</span><span class="sxs-lookup"><span data-stu-id="8cca8-113">In the declaration of the default value for an optional method parameter.</span></span>
- <span data-ttu-id="8cca8-114">V volání metody pro poskytnutí hodnoty argumentu.</span><span class="sxs-lookup"><span data-stu-id="8cca8-114">In a method call to provide an argument value.</span></span>
- <span data-ttu-id="8cca8-115">`return` V příkazu nebo jako výraz v členu Expression-těle.</span><span class="sxs-lookup"><span data-stu-id="8cca8-115">In a `return` statement or as an expression in an expression-bodied member.</span></span>

<span data-ttu-id="8cca8-116">Následující příklad ukazuje použití `default` literálu:</span><span class="sxs-lookup"><span data-stu-id="8cca8-116">The following example shows the usage of the `default` literal:</span></span>

[!code-csharp-interactive[default literal](~/samples/csharp/language-reference/operators/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a><span data-ttu-id="8cca8-117">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8cca8-117">C# language specification</span></span>

<span data-ttu-id="8cca8-118">Další informace naleznete v oddílu [výchozí hodnoty výrazů](~/_csharplang/spec/expressions.md#default-value-expressions) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="8cca8-118">For more information, see the [Default value expressions](~/_csharplang/spec/expressions.md#default-value-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="8cca8-119">Další informace o `default` literálu naleznete v poznámkách k [návrhu funkcí](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span><span class="sxs-lookup"><span data-stu-id="8cca8-119">For more information about the `default` literal, see the [feature proposal note](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8cca8-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8cca8-120">See also</span></span>

- [<span data-ttu-id="8cca8-121">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="8cca8-121">C# reference</span></span>](../index.md)
- [<span data-ttu-id="8cca8-122">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8cca8-122">C# operators</span></span>](index.md)
- [<span data-ttu-id="8cca8-123">Tabulka výchozích hodnot</span><span class="sxs-lookup"><span data-stu-id="8cca8-123">Default values table</span></span>](../keywords/default-values-table.md)
