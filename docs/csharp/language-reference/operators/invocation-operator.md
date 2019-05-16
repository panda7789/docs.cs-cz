---
title: () – operátor - C# odkaz
ms.custom: seodec18
ms.date: 01/15/2019
f1_keywords:
- ()_CSharpKeyword
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
ms.openlocfilehash: 412d3ac5296eaf7d67f4a5e84b7a42f6fa5bb8a5
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633805"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="e2dcb-102">() – operátor (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="e2dcb-102">() operator (C# Reference)</span></span>

<span data-ttu-id="e2dcb-103">Závorky, `()`, se obvykle používají pro vyvolání delegáta nebo metody nebo výrazy přetypování.</span><span class="sxs-lookup"><span data-stu-id="e2dcb-103">Parentheses, `()`, are typically used for method or delegate invocation or in cast expressions.</span></span>

<span data-ttu-id="e2dcb-104">Je také použít k určení pořadí, ve kterém se má vyhodnotit operací ve výrazu závorky.</span><span class="sxs-lookup"><span data-stu-id="e2dcb-104">You also use parentheses to specify the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="e2dcb-105">Další informace najdete v tématu [závorek](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) část [operátory](../../programming-guide/statements-expressions-operators/operators.md) článku.</span><span class="sxs-lookup"><span data-stu-id="e2dcb-105">For more information, see the [Adding parentheses](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) section of the [Operators](../../programming-guide/statements-expressions-operators/operators.md) article.</span></span> <span data-ttu-id="e2dcb-106">Seznam operátorů seřazené podle úrovně priority, naleznete v tématu [ C# operátory](index.md).</span><span class="sxs-lookup"><span data-stu-id="e2dcb-106">For the list of operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="method-invocation"></a><span data-ttu-id="e2dcb-107">Volání metody</span><span class="sxs-lookup"><span data-stu-id="e2dcb-107">Method invocation</span></span>

<span data-ttu-id="e2dcb-108">Následující příklad ukazuje, jak vyvolat metodu, s nebo bez argumentů a delegáta:</span><span class="sxs-lookup"><span data-stu-id="e2dcb-108">The following example demonstrates how to invoke a method, with or without arguments, and a delegate:</span></span>

[!code-csharp-interactive[use for invocation](~/samples/snippets/csharp/language-reference/operators/InvocationOperatorExamples.cs#Invocation)]

<span data-ttu-id="e2dcb-109">Můžete také použít závorky, při vyvolání [konstruktor](../../programming-guide/classes-and-structs/constructors.md) s [ `new` ](../keywords/new-operator.md) operátor.</span><span class="sxs-lookup"><span data-stu-id="e2dcb-109">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with a [`new`](../keywords/new-operator.md) operator.</span></span>

<span data-ttu-id="e2dcb-110">Další informace o metodách, naleznete v tématu [metody](../../programming-guide/classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="e2dcb-110">For more information about methods, see [Methods](../../programming-guide/classes-and-structs/methods.md).</span></span> <span data-ttu-id="e2dcb-111">Další informace o delegátech naleznete v tématu [delegáti](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="e2dcb-111">For more information about delegates, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="cast-expression"></a><span data-ttu-id="e2dcb-112">Výraz CAST</span><span class="sxs-lookup"><span data-stu-id="e2dcb-112">Cast expression</span></span>

<span data-ttu-id="e2dcb-113">Přetypování výrazu v podobě `(T)E` vyvolá operátor převodu se převést hodnotu výrazu `E` na typ `T`.</span><span class="sxs-lookup"><span data-stu-id="e2dcb-113">A cast expression of the form `(T)E` invokes a conversion operator to convert the value of expression `E` to type `T`.</span></span> <span data-ttu-id="e2dcb-114">Pokud neexistuje žádný explicitní převod z typu `E` na typ `T`, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="e2dcb-114">If no explicit conversion exists from the type of `E` to type `T`, a compile-time error occurs.</span></span> <span data-ttu-id="e2dcb-115">Informace o tom, jak definovat operátor převodu, najdete v článku [explicitní](../keywords/explicit.md) a [implicitní](../keywords/implicit.md) články – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="e2dcb-115">For information about how to define a conversion operator, see the [explicit](../keywords/explicit.md) and [implicit](../keywords/implicit.md) keyword articles.</span></span>

<span data-ttu-id="e2dcb-116">Následující příklad ukazuje převodů mezi číselnými typy:</span><span class="sxs-lookup"><span data-stu-id="e2dcb-116">The following example demonstrates type conversion between numeric types:</span></span>

[!code-csharp-interactive[use for cast](~/samples/snippets/csharp/language-reference/operators/InvocationOperatorExamples.cs#Cast)]

<span data-ttu-id="e2dcb-117">Další informace o předdefinovaných explicitní převody mezi číselnými typy najdete v tématu [tabulka explicitních číselných převodů](../keywords/explicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="e2dcb-117">For more information about predefined explicit conversions between numeric types, see [Explicit numeric conversions table](../keywords/explicit-numeric-conversions-table.md).</span></span>

<span data-ttu-id="e2dcb-118">Další informace najdete v tématu [přetypování a převody typu](../../programming-guide/types/casting-and-type-conversions.md) a [operátory převodu](../../programming-guide/statements-expressions-operators/conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="e2dcb-118">For more information, see [Casting and type conversions](../../programming-guide/types/casting-and-type-conversions.md) and [Conversion operators](../../programming-guide/statements-expressions-operators/conversion-operators.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="e2dcb-119">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="e2dcb-119">Operator overloadability</span></span>

<span data-ttu-id="e2dcb-120">Operátor `()` nemohou být přetíženy.</span><span class="sxs-lookup"><span data-stu-id="e2dcb-120">The operator `()` cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e2dcb-121">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e2dcb-121">C# language specification</span></span>

<span data-ttu-id="e2dcb-122">Další informace najdete v tématu [výrazy typu Invocation](~/_csharplang/spec/expressions.md#invocation-expressions) a [výrazy přetypování](~/_csharplang/spec/expressions.md#cast-expressions) oddíly [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="e2dcb-122">For more information, see the [Invocation expressions](~/_csharplang/spec/expressions.md#invocation-expressions) and [Cast expressions](~/_csharplang/spec/expressions.md#cast-expressions) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e2dcb-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e2dcb-123">See also</span></span>

- [<span data-ttu-id="e2dcb-124">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e2dcb-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e2dcb-125">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e2dcb-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e2dcb-126">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e2dcb-126">C# Operators</span></span>](index.md)
