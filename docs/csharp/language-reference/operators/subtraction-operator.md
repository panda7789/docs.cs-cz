---
title: '- operátory a operátory-= – C# odkaz'
ms.custom: seodec18
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
ms.openlocfilehash: 8e93b1d66a375f1f0af104e2a5dd6dfcbb39428d
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/12/2019
ms.locfileid: "67024911"
---
# <a name="--and---operators-c-reference"></a><span data-ttu-id="c69a8-102">– operátory a operátory-= (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="c69a8-102">- and -= operators (C# reference)</span></span>

<span data-ttu-id="c69a8-103">`-` Operátor je podporován předdefinovaných číselných typů a [delegovat](../keywords/delegate.md) typy.</span><span class="sxs-lookup"><span data-stu-id="c69a8-103">The `-` operator is supported by the built-in numeric types and [delegate](../keywords/delegate.md) types.</span></span>

<span data-ttu-id="c69a8-104">Informace o aritmetické operace `-` operátoru, najdete v článku [Unární plus a minus operátory](arithmetic-operators.md#unary-plus-and-minus-operators) a [operátor odčítání -](arithmetic-operators.md#subtraction-operator--) oddíly [aritmetické operátory](arithmetic-operators.md) článku.</span><span class="sxs-lookup"><span data-stu-id="c69a8-104">For information about the arithmetic `-` operator, see the [Unary plus and minus operators](arithmetic-operators.md#unary-plus-and-minus-operators) and [Subtraction operator -](arithmetic-operators.md#subtraction-operator--) sections of the [Arithmetic operators](arithmetic-operators.md) article.</span></span>

## <a name="delegate-removal"></a><span data-ttu-id="c69a8-105">Odebrání delegátů</span><span class="sxs-lookup"><span data-stu-id="c69a8-105">Delegate removal</span></span>

<span data-ttu-id="c69a8-106">Pro operandy stejného [delegovat](../keywords/delegate.md) typ, `-` operátor vrátí instanci delegáta, který se vypočítává takto:</span><span class="sxs-lookup"><span data-stu-id="c69a8-106">For operands of the same [delegate](../keywords/delegate.md) type, the `-` operator returns a delegate instance that is calculated as follows:</span></span>

- <span data-ttu-id="c69a8-107">Pokud jsou oba operandy jinou hodnotu než null a vyvolání seznam druhého operandu je správné souvislých podseznam seznamu vyvolání prvního operandu, je výsledek operace nový seznam volání, která se získá tak, že odeberete položky druhého operandu od vyvolání seznamu prvního operandu.</span><span class="sxs-lookup"><span data-stu-id="c69a8-107">If both operands are non-null and the invocation list of the second operand is a proper contiguous sublist of the invocation list of the first operand, the result of the operation is a new invocation list that is obtained by removing the second operand's entries from the invocation list of the first operand.</span></span> <span data-ttu-id="c69a8-108">Pokud je druhý operand seznamu odpovídá několika dílčích souvislých v seznamu je první operand, odeberou se pouze odpovídající podseznam úplně vpravo.</span><span class="sxs-lookup"><span data-stu-id="c69a8-108">If the second operand's list matches multiple contiguous sublists in the first operand's list, only the right-most matching sublist is removed.</span></span> <span data-ttu-id="c69a8-109">Pokud je odebrání výsledkem je seznam prázdný, výsledkem je `null`.</span><span class="sxs-lookup"><span data-stu-id="c69a8-109">If removal results in an empty list, the result is `null`.</span></span>

  [!code-csharp-interactive[delegate removal](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemoval)]

- <span data-ttu-id="c69a8-110">Pokud seznamu vyvolání druhého operandu není správné souvislých podseznam seznamu vyvolání prvního operandu, je výsledek operace prvním operandem.</span><span class="sxs-lookup"><span data-stu-id="c69a8-110">If the invocation list of the second operand is not a proper contiguous sublist of the invocation list of the first operand, the result of the operation is the first operand.</span></span> <span data-ttu-id="c69a8-111">Například odebráním delegáta, který není součástí vícesměrového vysílání delegáta neprovede žádnou akci a výsledkem beze změny vícesměrového vysílání delegáta.</span><span class="sxs-lookup"><span data-stu-id="c69a8-111">For example, removing a delegate that is not part of the multicast delegate does nothing and results in the unchanged multicast delegate.</span></span>

  [!code-csharp-interactive[delegate removal with no effect](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemovalNoChange)]

  <span data-ttu-id="c69a8-112">Předchozí příklad ukazuje také, že během delegáta instance odebrání delegátů jsou porovnány.</span><span class="sxs-lookup"><span data-stu-id="c69a8-112">The preceding example also demonstrates that during delegate removal delegate instances are compared.</span></span> <span data-ttu-id="c69a8-113">Například delegáty, které jsou vytvářeny ze zkušební verze identických [výrazy lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) nejsou stejné.</span><span class="sxs-lookup"><span data-stu-id="c69a8-113">For example, delegates that are produced from evaluation of identical [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) are not equal.</span></span> <span data-ttu-id="c69a8-114">Další informace o delegáta rovnosti, najdete v článku [delegovat operátory rovnosti](~/_csharplang/spec/expressions.md#delegate-equality-operators) část [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="c69a8-114">For more information about delegate equality, see the [Delegate equality operators](~/_csharplang/spec/expressions.md#delegate-equality-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

- <span data-ttu-id="c69a8-115">Pokud je první operand `null`, je výsledek operace `null`.</span><span class="sxs-lookup"><span data-stu-id="c69a8-115">If the first operand is `null`, the result of the operation is `null`.</span></span> <span data-ttu-id="c69a8-116">Pokud je druhý operand `null`, výsledkem operace je prvním operandem.</span><span class="sxs-lookup"><span data-stu-id="c69a8-116">If the second operand is `null`, the result of the operation is the first operand.</span></span>

  [!code-csharp-interactive[delegate removal and null](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemovalAndNull)]

<span data-ttu-id="c69a8-117">Chcete-li kombinování delegátů, použijte [ `+` operátor](addition-operator.md#delegate-combination).</span><span class="sxs-lookup"><span data-stu-id="c69a8-117">To combine delegates, use the [`+` operator](addition-operator.md#delegate-combination).</span></span>

<span data-ttu-id="c69a8-118">Další informace o typech delegáta, naleznete v tématu [delegáti](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="c69a8-118">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="subtraction-assignment-operator--"></a><span data-ttu-id="c69a8-119">Operátor odčítání a přiřazení-=</span><span class="sxs-lookup"><span data-stu-id="c69a8-119">Subtraction assignment operator -=</span></span>

<span data-ttu-id="c69a8-120">Pomocí výrazu `-=` operátorů, například</span><span class="sxs-lookup"><span data-stu-id="c69a8-120">An expression using the `-=` operator, such as</span></span>

```csharp
x -= y
```

<span data-ttu-id="c69a8-121">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="c69a8-121">is equivalent to</span></span>

```csharp
x = x - y
```

<span data-ttu-id="c69a8-122">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="c69a8-122">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="c69a8-123">Následující příklad ukazuje použití `-=` operátor:</span><span class="sxs-lookup"><span data-stu-id="c69a8-123">The following example demonstrates the usage of the `-=` operator:</span></span>

[!code-csharp-interactive[-= examples](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#SubtractAndAssign)]

<span data-ttu-id="c69a8-124">Můžete také použít `-=` operátor zadat metodu obslužné rutiny události při vy nemusíte podnikat odebrat [události](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="c69a8-124">You also use the `-=` operator to specify an event handler method to remove when you unsubscribe from an [event](../keywords/event.md).</span></span> <span data-ttu-id="c69a8-125">Další informace najdete v tématu [postupy: přihlášení k odběru a zrušit její odběr události](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="c69a8-125">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="c69a8-126">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="c69a8-126">Operator overloadability</span></span>

<span data-ttu-id="c69a8-127">Uživatelem definovaný typ může [přetížení](../keywords/operator.md) `-` operátor.</span><span class="sxs-lookup"><span data-stu-id="c69a8-127">A user-defined type can [overload](../keywords/operator.md) the `-` operator.</span></span> <span data-ttu-id="c69a8-128">Když do binárního souboru `-` je operátor přetížen, `-=` je také implicitně přetížený operátor.</span><span class="sxs-lookup"><span data-stu-id="c69a8-128">When a binary `-` operator is overloaded, the `-=` operator is also implicitly overloaded.</span></span> <span data-ttu-id="c69a8-129">Uživatelem definovaný typ nejde přetížit explicitně `-=` operátor.</span><span class="sxs-lookup"><span data-stu-id="c69a8-129">A user-defined type cannot explicitly overload the `-=` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c69a8-130">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c69a8-130">C# language specification</span></span>

<span data-ttu-id="c69a8-131">Další informace najdete v tématu [unární operátor minus](~/_csharplang/spec/expressions.md#unary-minus-operator) a [operátor odčítání](~/_csharplang/spec/expressions.md#subtraction-operator) oddíly [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="c69a8-131">For more information, see the [Unary minus operator](~/_csharplang/spec/expressions.md#unary-minus-operator) and [Subtraction operator](~/_csharplang/spec/expressions.md#subtraction-operator) sections of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c69a8-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c69a8-132">See also</span></span>

- [<span data-ttu-id="c69a8-133">C#referenční dokumentace</span><span class="sxs-lookup"><span data-stu-id="c69a8-133">C# reference</span></span>](../index.md)
- [<span data-ttu-id="c69a8-134">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c69a8-134">C# operators</span></span>](index.md)
- [<span data-ttu-id="c69a8-135">Delegáti</span><span class="sxs-lookup"><span data-stu-id="c69a8-135">Delegates</span></span>](../../programming-guide/delegates/index.md)
- [<span data-ttu-id="c69a8-136">Události</span><span class="sxs-lookup"><span data-stu-id="c69a8-136">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="c69a8-137">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="c69a8-137">Arithmetic operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="c69a8-138">+ a operátory +=</span><span class="sxs-lookup"><span data-stu-id="c69a8-138">+ and += operators</span></span>](addition-operator.md)
