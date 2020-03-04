---
title: '- and-= Operators C# – reference'
ms.date: 05/27/2019
f1_keywords:
- -_CSharpKeyword
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction operator [C#]
- delegate removal [C#]
- '- operator [C#]'
- subtraction assignment operator [C#]
- event unsubscription [C#]
- -= operator [C#]
ms.assetid: 4de7a4fa-c69d-48e6-aff1-3130af970b2d
ms.openlocfilehash: ccf3572df99f5c3de127c9ada690a977843648af
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78238840"
---
# <a name="--and---operators-c-reference"></a><span data-ttu-id="73d3e-102">-and-= – operátoryC# (referenční informace)</span><span class="sxs-lookup"><span data-stu-id="73d3e-102">- and -= operators (C# reference)</span></span>

<span data-ttu-id="73d3e-103">Operátory `-` a `-=` jsou podporovány integrovanými čísly [integrálu](../builtin-types/integral-numeric-types.md) a typy s [plovoucí desetinnou](../builtin-types/floating-point-numeric-types.md) čárkou a typy [delegátů](../builtin-types/reference-types.md#the-delegate-type) .</span><span class="sxs-lookup"><span data-stu-id="73d3e-103">The `-` and `-=` operators are supported by the built-in [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types and [delegate](../builtin-types/reference-types.md#the-delegate-type) types.</span></span>

<span data-ttu-id="73d3e-104">Informace o aritmetickém operátoru `-` naleznete v tématu [unární operátory plus a minus](arithmetic-operators.md#unary-plus-and-minus-operators) a [operátor odčítání –](arithmetic-operators.md#subtraction-operator--) oddíly v článku [aritmetické operátory](arithmetic-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="73d3e-104">For information about the arithmetic `-` operator, see the [Unary plus and minus operators](arithmetic-operators.md#unary-plus-and-minus-operators) and [Subtraction operator -](arithmetic-operators.md#subtraction-operator--) sections of the [Arithmetic operators](arithmetic-operators.md) article.</span></span>

## <a name="delegate-removal"></a><span data-ttu-id="73d3e-105">Odebrání delegáta</span><span class="sxs-lookup"><span data-stu-id="73d3e-105">Delegate removal</span></span>

<span data-ttu-id="73d3e-106">Pro operandy stejného typu [delegáta](../builtin-types/reference-types.md#the-delegate-type) operátor `-` vrací instanci delegáta, která je vypočítána takto:</span><span class="sxs-lookup"><span data-stu-id="73d3e-106">For operands of the same [delegate](../builtin-types/reference-types.md#the-delegate-type) type, the `-` operator returns a delegate instance that is calculated as follows:</span></span>

- <span data-ttu-id="73d3e-107">Jsou-li oba operandy nenulové a seznam vyvolání pravého operandu je správným souvislým podseznamem seznamu volání na levé straně, výsledkem operace je nový seznam vyvolání, který se získá odebráním operandu pravého operandu. položky ze seznamu volání z levého operandu.</span><span class="sxs-lookup"><span data-stu-id="73d3e-107">If both operands are non-null and the invocation list of the right-hand operand is a proper contiguous sublist of the invocation list of the left-hand operand, the result of the operation is a new invocation list that is obtained by removing the right-hand operand's entries from the invocation list of the left-hand operand.</span></span> <span data-ttu-id="73d3e-108">Pokud se v seznamu operandů na pravé straně shoduje více sousedících podseznamů v seznamu operandů na levé straně, bude odebrán pouze odpovídající podseznam.</span><span class="sxs-lookup"><span data-stu-id="73d3e-108">If the right-hand operand's list matches multiple contiguous sublists in the left-hand operand's list, only the right-most matching sublist is removed.</span></span> <span data-ttu-id="73d3e-109">Pokud je výsledkem odebrání prázdný seznam, výsledek je `null`.</span><span class="sxs-lookup"><span data-stu-id="73d3e-109">If removal results in an empty list, the result is `null`.</span></span>

  [!code-csharp-interactive[delegate removal](~/samples/snippets/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemoval)]

- <span data-ttu-id="73d3e-110">Pokud seznam volání na pravé straně operand není správným souvislým podseznamem seznamu vyvolání na levém operandu, výsledkem operace je operand na levé straně.</span><span class="sxs-lookup"><span data-stu-id="73d3e-110">If the invocation list of the right-hand operand is not a proper contiguous sublist of the invocation list of the left-hand operand, the result of the operation is the left-hand operand.</span></span> <span data-ttu-id="73d3e-111">Například odebrání delegáta, který není součástí delegáta vícesměrového vysílání, neprovede žádnou akci a dojde ke změně nezměněného delegáta vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="73d3e-111">For example, removing a delegate that is not part of the multicast delegate does nothing and results in the unchanged multicast delegate.</span></span>

  [!code-csharp-interactive[delegate removal with no effect](~/samples/snippets/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemovalNoChange)]

  <span data-ttu-id="73d3e-112">Předchozí příklad také ukazuje, že během porovnání instancí delegáta pro odebrání delegáta.</span><span class="sxs-lookup"><span data-stu-id="73d3e-112">The preceding example also demonstrates that during delegate removal delegate instances are compared.</span></span> <span data-ttu-id="73d3e-113">Například delegáty vytvořené z vyhodnocení identických [výrazů lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) nejsou stejné.</span><span class="sxs-lookup"><span data-stu-id="73d3e-113">For example, delegates that are produced from evaluation of identical [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) are not equal.</span></span> <span data-ttu-id="73d3e-114">Další informace o rovnosti delegátů naleznete v části [operátory rovnosti delegátů](~/_csharplang/spec/expressions.md#delegate-equality-operators) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="73d3e-114">For more information about delegate equality, see the [Delegate equality operators](~/_csharplang/spec/expressions.md#delegate-equality-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

- <span data-ttu-id="73d3e-115">Je-li operand na levé straně `null`, výsledek operace je `null`.</span><span class="sxs-lookup"><span data-stu-id="73d3e-115">If the left-hand operand is `null`, the result of the operation is `null`.</span></span> <span data-ttu-id="73d3e-116">Je-li operand na pravé straně `null`, výsledkem operace je operand na levé straně.</span><span class="sxs-lookup"><span data-stu-id="73d3e-116">If the right-hand operand is `null`, the result of the operation is the left-hand operand.</span></span>

  [!code-csharp-interactive[delegate removal and null](~/samples/snippets/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemovalAndNull)]

<span data-ttu-id="73d3e-117">Chcete-li kombinovat delegáty, použijte [operátor`+`](addition-operator.md#delegate-combination).</span><span class="sxs-lookup"><span data-stu-id="73d3e-117">To combine delegates, use the [`+` operator](addition-operator.md#delegate-combination).</span></span>

<span data-ttu-id="73d3e-118">Další informace o typech delegátů naleznete v tématu [Delegates](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="73d3e-118">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="subtraction-assignment-operator--"></a><span data-ttu-id="73d3e-119">Operátor přiřazení odčítání-=</span><span class="sxs-lookup"><span data-stu-id="73d3e-119">Subtraction assignment operator -=</span></span>

<span data-ttu-id="73d3e-120">Výraz používající operátor `-=`, například</span><span class="sxs-lookup"><span data-stu-id="73d3e-120">An expression using the `-=` operator, such as</span></span>

```csharp
x -= y
```

<span data-ttu-id="73d3e-121">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="73d3e-121">is equivalent to</span></span>

```csharp
x = x - y
```

<span data-ttu-id="73d3e-122">s výjimkou `x` je vyhodnocena pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="73d3e-122">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="73d3e-123">Následující příklad ukazuje použití operátoru `-=`:</span><span class="sxs-lookup"><span data-stu-id="73d3e-123">The following example demonstrates the usage of the `-=` operator:</span></span>

[!code-csharp-interactive[-= examples](~/samples/snippets/csharp/language-reference/operators/SubtractionOperator.cs#SubtractAndAssign)]

<span data-ttu-id="73d3e-124">Operátor `-=` můžete použít také k určení metody obslužné rutiny události, která se má odebrat při zrušení odběru [události](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="73d3e-124">You also use the `-=` operator to specify an event handler method to remove when you unsubscribe from an [event](../keywords/event.md).</span></span> <span data-ttu-id="73d3e-125">Další informace najdete v tématu [jak se přihlásit k odběru událostí a odhlásit se z](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)nich.</span><span class="sxs-lookup"><span data-stu-id="73d3e-125">For more information, see [How to subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="73d3e-126">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="73d3e-126">Operator overloadability</span></span>

<span data-ttu-id="73d3e-127">Uživatelsky definovaný typ může [přetížit](operator-overloading.md) operátor `-`.</span><span class="sxs-lookup"><span data-stu-id="73d3e-127">A user-defined type can [overload](operator-overloading.md) the `-` operator.</span></span> <span data-ttu-id="73d3e-128">Je-li operátor binárního `-` přetížen, je operátor `-=` také implicitně přetížený.</span><span class="sxs-lookup"><span data-stu-id="73d3e-128">When a binary `-` operator is overloaded, the `-=` operator is also implicitly overloaded.</span></span> <span data-ttu-id="73d3e-129">Uživatelsky definovaný typ nemůže explicitně přetížit operátor `-=`.</span><span class="sxs-lookup"><span data-stu-id="73d3e-129">A user-defined type cannot explicitly overload the `-=` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="73d3e-130">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="73d3e-130">C# language specification</span></span>

<span data-ttu-id="73d3e-131">Další informace naleznete v částech [unárního operátoru minus](~/_csharplang/spec/expressions.md#unary-minus-operator) a [operátoru odčítání](~/_csharplang/spec/expressions.md#subtraction-operator) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="73d3e-131">For more information, see the [Unary minus operator](~/_csharplang/spec/expressions.md#unary-minus-operator) and [Subtraction operator](~/_csharplang/spec/expressions.md#subtraction-operator) sections of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="73d3e-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="73d3e-132">See also</span></span>

- [<span data-ttu-id="73d3e-133">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="73d3e-133">C# reference</span></span>](../index.md)
- [<span data-ttu-id="73d3e-134">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="73d3e-134">C# operators</span></span>](index.md)
- [<span data-ttu-id="73d3e-135">Události</span><span class="sxs-lookup"><span data-stu-id="73d3e-135">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="73d3e-136">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="73d3e-136">Arithmetic operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="73d3e-137">+ a + = – operátory</span><span class="sxs-lookup"><span data-stu-id="73d3e-137">+ and += operators</span></span>](addition-operator.md)
