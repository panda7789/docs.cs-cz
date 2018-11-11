---
title: '&amp;&amp; – Operátor (referenční dokumentace jazyka C#)'
ms.date: 11/06/2018
f1_keywords:
- '&&_CSharpKeyword'
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
ms.openlocfilehash: d0e6d9a5aedc7dc87393e3dea070bf442b3268dc
ms.sourcegitcommit: b5cd9d5d3b75a5537fc9ad8a3f085f0bb1845ee0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2018
ms.locfileid: "43529232"
---
# <a name="ampamp-operator-c-reference"></a><span data-ttu-id="72493-102">&amp;&amp; – Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="72493-102">&amp;&amp; Operator (C# Reference)</span></span>

<span data-ttu-id="72493-103">Podmíněné logického operátoru AND `&&`, označované také jako "krátký cyklus" logického operátoru AND, vypočítá logický operátor AND z jeho [bool](../keywords/bool.md) operandy.</span><span class="sxs-lookup"><span data-stu-id="72493-103">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its [bool](../keywords/bool.md) operands.</span></span> <span data-ttu-id="72493-104">Výsledek `x && y` je `true` Pokud mají oba `x` a `y` vyhodnotit `true`.</span><span class="sxs-lookup"><span data-stu-id="72493-104">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="72493-105">V opačném případě je výsledek `false`.</span><span class="sxs-lookup"><span data-stu-id="72493-105">Otherwise, the result is `false`.</span></span> <span data-ttu-id="72493-106">Pokud je první operand vyhodnocen jako `false`, druhý operand není vyhodnocen a výsledek operace `false`.</span><span class="sxs-lookup"><span data-stu-id="72493-106">If the first operand evaluates to `false`, the second operand is not evaluated and the result of operation is `false`.</span></span> <span data-ttu-id="72493-107">Následující příklad ukazuje toto chování:</span><span class="sxs-lookup"><span data-stu-id="72493-107">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[conditional logical AND](~/samples/snippets/csharp/language-reference/operators/ConditionalLogicalOperatorsExamples.cs#And)]

<span data-ttu-id="72493-108">[Logického operátoru AND](and-operator.md) `&` také vypočítá logický operátor AND z jeho `bool` operandy, ale vždy vyhodnotí oba operandy.</span><span class="sxs-lookup"><span data-stu-id="72493-108">The [logical AND operator](and-operator.md) `&` also computes the logical AND of its `bool` operands, but always evaluates both operands.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="72493-109">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="72493-109">Operator overloadability</span></span>

<span data-ttu-id="72493-110">Uživatelem definovaný typ nejde přetížit podmíněné logického operátoru AND.</span><span class="sxs-lookup"><span data-stu-id="72493-110">A user-defined type cannot overload the conditional logical AND operator.</span></span> <span data-ttu-id="72493-111">Ale pokud přetížení uživatelem definovaného typu [logický operátor AND](and-operator.md), [true](../keywords/true-operator.md), a [false](../keywords/false-operator.md) operátory určitým způsobem, `&&` operace může být vyhodnocen pro operandy typu.</span><span class="sxs-lookup"><span data-stu-id="72493-111">However, if a user-defined type overloads the [logical AND](and-operator.md), [true](../keywords/true-operator.md), and [false](../keywords/false-operator.md) operators in a certain way, the `&&` operation can be evaluated for the operands of that type.</span></span> <span data-ttu-id="72493-112">Další informace najdete v tématu [podmíněné logické operátory definované uživatelem](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) část [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="72493-112">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="72493-113">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="72493-113">C# language specification</span></span>

<span data-ttu-id="72493-114">Další informace najdete v tématu [podmíněné logické operátory](~/_csharplang/spec/expressions.md#conditional-logical-operators) část [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="72493-114">For more information, see the [Conditional logical operators](~/_csharplang/spec/expressions.md#conditional-logical-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="72493-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="72493-115">See also</span></span>

- [<span data-ttu-id="72493-116">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="72493-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="72493-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="72493-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="72493-118">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="72493-118">C# Operators</span></span>](index.md)
- [<span data-ttu-id="72493-119">|| – operátor</span><span class="sxs-lookup"><span data-stu-id="72493-119">|| operator</span></span>](conditional-or-operator.md)
- [! – operátor]<span data-ttu-id="72493-120">(logical-negation-operator.md)</span><span class="sxs-lookup"><span data-stu-id="72493-120">(logical-negation-operator.md)</span></span>
- [<span data-ttu-id="72493-121">& – operátor</span><span class="sxs-lookup"><span data-stu-id="72493-121">& operator</span></span>](and-operator.md)
