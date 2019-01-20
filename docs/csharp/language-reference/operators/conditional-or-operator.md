---
title: '|| Operator - C# odkaz'
ms.custom: seodec18
ms.date: 11/06/2018
f1_keywords:
- '||_CSharpKeyword'
helpviewer_keywords:
- logical OR operator [C#]
- conditional-OR operator (||) [C#]
- '|| operator [C#]'
ms.assetid: 7d442d8e-400d-421f-b4d2-034bf82bcbdc
ms.openlocfilehash: 079c021eb68ece097c7f644416f1e9469a82dcea
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415426"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="94962-102">|| – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="94962-102">|| Operator (C# Reference)</span></span>

<span data-ttu-id="94962-103">Podmíněné logického operátoru OR `||`, označované také jako "krátký cyklus" logického operátoru OR, vypočítá logický operátor OR z jeho [bool](../keywords/bool.md) operandy.</span><span class="sxs-lookup"><span data-stu-id="94962-103">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its [bool](../keywords/bool.md) operands.</span></span> <span data-ttu-id="94962-104">Výsledek `x || y` je `true` Pokud `x` nebo `y` vyhodnotí jako `true`.</span><span class="sxs-lookup"><span data-stu-id="94962-104">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="94962-105">V opačném případě je výsledek `false`.</span><span class="sxs-lookup"><span data-stu-id="94962-105">Otherwise, the result is `false`.</span></span> <span data-ttu-id="94962-106">Pokud je první operand vyhodnocen jako `true`, druhý operand není vyhodnocen a výsledek operace `true`.</span><span class="sxs-lookup"><span data-stu-id="94962-106">If the first operand evaluates to `true`, the second operand is not evaluated and the result of operation is `true`.</span></span> <span data-ttu-id="94962-107">Následující příklad ukazuje toto chování:</span><span class="sxs-lookup"><span data-stu-id="94962-107">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[conditional logical OR](~/samples/snippets/csharp/language-reference/operators/ConditionalLogicalOperatorsExamples.cs#Or)]

<span data-ttu-id="94962-108">[Logického operátoru OR](or-operator.md) `|` také vypočítá logický operátor OR z jeho `bool` operandy, ale vždy vyhodnotí oba operandy.</span><span class="sxs-lookup"><span data-stu-id="94962-108">The [logical OR operator](or-operator.md) `|` also computes the logical OR of its `bool` operands, but always evaluates both operands.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="94962-109">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="94962-109">Operator overloadability</span></span>

<span data-ttu-id="94962-110">Uživatelem definovaný typ nejde přetížit podmíněné logický operátor OR.</span><span class="sxs-lookup"><span data-stu-id="94962-110">A user-defined type cannot overload the conditional logical OR operator.</span></span> <span data-ttu-id="94962-111">Ale pokud přetížení uživatelem definovaného typu [logický operátor OR](or-operator.md) a [operátory true a false](../keywords/true-false-operators.md) určitým způsobem, `||` operace může být vyhodnocen pro operandy typu.</span><span class="sxs-lookup"><span data-stu-id="94962-111">However, if a user-defined type overloads the [logical OR](or-operator.md) and [true and false operators](../keywords/true-false-operators.md) in a certain way, the `||` operation can be evaluated for the operands of that type.</span></span> <span data-ttu-id="94962-112">Další informace najdete v tématu [podmíněné logické operátory definované uživatelem](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) část [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="94962-112">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="94962-113">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="94962-113">C# language specification</span></span>

<span data-ttu-id="94962-114">Další informace najdete v tématu [podmíněné logické operátory](~/_csharplang/spec/expressions.md#conditional-logical-operators) část [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="94962-114">For more information, see the [Conditional logical operators](~/_csharplang/spec/expressions.md#conditional-logical-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="94962-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="94962-115">See also</span></span>

- [<span data-ttu-id="94962-116">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="94962-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="94962-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="94962-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="94962-118">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="94962-118">C# Operators</span></span>](index.md)
- [<span data-ttu-id="94962-119">& & – operátor</span><span class="sxs-lookup"><span data-stu-id="94962-119">&& operator</span></span>](conditional-and-operator.md)
- [<span data-ttu-id="94962-120">\! – Operátor</span><span class="sxs-lookup"><span data-stu-id="94962-120">\! operator</span></span>](logical-negation-operator.md)
- [<span data-ttu-id="94962-121">| – operátor</span><span class="sxs-lookup"><span data-stu-id="94962-121">| operator</span></span>](or-operator.md)
