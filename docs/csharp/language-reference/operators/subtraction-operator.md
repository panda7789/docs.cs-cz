---
title: '- and-= Operators-reference jazyka C#'
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
ms.openlocfilehash: a00957c8d36a96b5ee23b9e5a309b6139b33fd36
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916690"
---
# <a name="--and---operators-c-reference"></a><span data-ttu-id="eb9d1-102">-and-= – operátory (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="eb9d1-102">- and -= operators (C# reference)</span></span>

<span data-ttu-id="eb9d1-103">`-`Operátory a `-=` jsou podporovány integrovanými čísly [integrálu](../builtin-types/integral-numeric-types.md) a typy s [plovoucí desetinnou](../builtin-types/floating-point-numeric-types.md) čárkou a typy [delegátů](../builtin-types/reference-types.md#the-delegate-type) .</span><span class="sxs-lookup"><span data-stu-id="eb9d1-103">The `-` and `-=` operators are supported by the built-in [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types and [delegate](../builtin-types/reference-types.md#the-delegate-type) types.</span></span>

<span data-ttu-id="eb9d1-104">Informace o aritmetickém `-` operátoru naleznete v tématu [unární operátory plus a minus](arithmetic-operators.md#unary-plus-and-minus-operators) a [operátor odčítání –](arithmetic-operators.md#subtraction-operator--) oddíly v článku [aritmetické operátory](arithmetic-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="eb9d1-104">For information about the arithmetic `-` operator, see the [Unary plus and minus operators](arithmetic-operators.md#unary-plus-and-minus-operators) and [Subtraction operator -](arithmetic-operators.md#subtraction-operator--) sections of the [Arithmetic operators](arithmetic-operators.md) article.</span></span>

## <a name="delegate-removal"></a><span data-ttu-id="eb9d1-105">Odebrání delegáta</span><span class="sxs-lookup"><span data-stu-id="eb9d1-105">Delegate removal</span></span>

<span data-ttu-id="eb9d1-106">Pro operandy stejného typu [delegáta](../builtin-types/reference-types.md#the-delegate-type) `-` vrátí operátor instanci delegáta, která je vypočítána takto:</span><span class="sxs-lookup"><span data-stu-id="eb9d1-106">For operands of the same [delegate](../builtin-types/reference-types.md#the-delegate-type) type, the `-` operator returns a delegate instance that is calculated as follows:</span></span>

- <span data-ttu-id="eb9d1-107">Pokud jsou oba operandy nenulové a seznam vyvolání pravého operandu je správným souvislým podseznamem seznamu vyvolání na levém operandu, výsledkem operace je nový seznam vyvolání, který se získá odebráním položek operandu na pravé straně ze seznamu vyvolání operandu na levé straně.</span><span class="sxs-lookup"><span data-stu-id="eb9d1-107">If both operands are non-null and the invocation list of the right-hand operand is a proper contiguous sublist of the invocation list of the left-hand operand, the result of the operation is a new invocation list that is obtained by removing the right-hand operand's entries from the invocation list of the left-hand operand.</span></span> <span data-ttu-id="eb9d1-108">Pokud se v seznamu operandů na pravé straně shoduje více sousedících podseznamů v seznamu operandů na levé straně, bude odebrán pouze odpovídající podseznam.</span><span class="sxs-lookup"><span data-stu-id="eb9d1-108">If the right-hand operand's list matches multiple contiguous sublists in the left-hand operand's list, only the right-most matching sublist is removed.</span></span> <span data-ttu-id="eb9d1-109">Pokud je výsledkem odebrání prázdný seznam, výsledek je `null` .</span><span class="sxs-lookup"><span data-stu-id="eb9d1-109">If removal results in an empty list, the result is `null`.</span></span>

  [!code-csharp-interactive[delegate removal](snippets/shared/SubtractionOperator.cs#DelegateRemoval)]

- <span data-ttu-id="eb9d1-110">Pokud seznam volání na pravé straně operand není správným souvislým podseznamem seznamu vyvolání na levém operandu, výsledkem operace je operand na levé straně.</span><span class="sxs-lookup"><span data-stu-id="eb9d1-110">If the invocation list of the right-hand operand is not a proper contiguous sublist of the invocation list of the left-hand operand, the result of the operation is the left-hand operand.</span></span> <span data-ttu-id="eb9d1-111">Například odebrání delegáta, který není součástí delegáta vícesměrového vysílání, neprovede žádnou akci a dojde ke změně nezměněného delegáta vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="eb9d1-111">For example, removing a delegate that is not part of the multicast delegate does nothing and results in the unchanged multicast delegate.</span></span>

  [!code-csharp-interactive[delegate removal with no effect](snippets/shared/SubtractionOperator.cs#DelegateRemovalNoChange)]

  <span data-ttu-id="eb9d1-112">Předchozí příklad také ukazuje, že během porovnání instancí delegáta pro odebrání delegáta.</span><span class="sxs-lookup"><span data-stu-id="eb9d1-112">The preceding example also demonstrates that during delegate removal delegate instances are compared.</span></span> <span data-ttu-id="eb9d1-113">Například delegáty vytvořené z vyhodnocení identických [výrazů lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) nejsou stejné.</span><span class="sxs-lookup"><span data-stu-id="eb9d1-113">For example, delegates that are produced from evaluation of identical [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) are not equal.</span></span> <span data-ttu-id="eb9d1-114">Další informace o rovnosti delegátů naleznete v části [operátory rovnosti delegátů](~/_csharplang/spec/expressions.md#delegate-equality-operators) ve [specifikaci jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="eb9d1-114">For more information about delegate equality, see the [Delegate equality operators](~/_csharplang/spec/expressions.md#delegate-equality-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

- <span data-ttu-id="eb9d1-115">Pokud je operand na levé straně `null` , výsledkem operace je `null` .</span><span class="sxs-lookup"><span data-stu-id="eb9d1-115">If the left-hand operand is `null`, the result of the operation is `null`.</span></span> <span data-ttu-id="eb9d1-116">Pokud je operand na pravé straně `null` , výsledkem operace je operand na levé straně.</span><span class="sxs-lookup"><span data-stu-id="eb9d1-116">If the right-hand operand is `null`, the result of the operation is the left-hand operand.</span></span>

  [!code-csharp-interactive[delegate removal and null](snippets/shared/SubtractionOperator.cs#DelegateRemovalAndNull)]

<span data-ttu-id="eb9d1-117">Chcete-li kombinovat delegáty, použijte [ `+` operátor](addition-operator.md#delegate-combination).</span><span class="sxs-lookup"><span data-stu-id="eb9d1-117">To combine delegates, use the [`+` operator](addition-operator.md#delegate-combination).</span></span>

<span data-ttu-id="eb9d1-118">Další informace o typech delegátů naleznete v tématu [Delegates](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="eb9d1-118">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="subtraction-assignment-operator--"></a><span data-ttu-id="eb9d1-119">Operátor přiřazení odčítání-=</span><span class="sxs-lookup"><span data-stu-id="eb9d1-119">Subtraction assignment operator -=</span></span>

<span data-ttu-id="eb9d1-120">Výraz, který používá `-=` operátor, například</span><span class="sxs-lookup"><span data-stu-id="eb9d1-120">An expression using the `-=` operator, such as</span></span>

```csharp
x -= y
```

<span data-ttu-id="eb9d1-121">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="eb9d1-121">is equivalent to</span></span>

```csharp
x = x - y
```

<span data-ttu-id="eb9d1-122">s výjimkou, že `x` je vyhodnocena pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="eb9d1-122">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="eb9d1-123">Následující příklad ukazuje použití `-=` operátoru:</span><span class="sxs-lookup"><span data-stu-id="eb9d1-123">The following example demonstrates the usage of the `-=` operator:</span></span>

[!code-csharp-interactive[-= examples](snippets/shared/SubtractionOperator.cs#SubtractAndAssign)]

<span data-ttu-id="eb9d1-124">Operátor můžete také použít `-=` k určení metody obslužné rutiny události, která se má odebrat, když zrušíte odběr [události](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="eb9d1-124">You also use the `-=` operator to specify an event handler method to remove when you unsubscribe from an [event](../keywords/event.md).</span></span> <span data-ttu-id="eb9d1-125">Další informace najdete v tématu [jak se přihlásit k odběru událostí a odhlásit se z](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)nich.</span><span class="sxs-lookup"><span data-stu-id="eb9d1-125">For more information, see [How to subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="eb9d1-126">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="eb9d1-126">Operator overloadability</span></span>

<span data-ttu-id="eb9d1-127">Uživatelsky definovaný typ může [přetížit](operator-overloading.md) `-` operátor.</span><span class="sxs-lookup"><span data-stu-id="eb9d1-127">A user-defined type can [overload](operator-overloading.md) the `-` operator.</span></span> <span data-ttu-id="eb9d1-128">Při přetížení binárního `-` operátoru `-=` je operátor také implicitně přetížený.</span><span class="sxs-lookup"><span data-stu-id="eb9d1-128">When a binary `-` operator is overloaded, the `-=` operator is also implicitly overloaded.</span></span> <span data-ttu-id="eb9d1-129">Uživatelsky definovaný typ nemůže explicitně přetížit `-=` operátor.</span><span class="sxs-lookup"><span data-stu-id="eb9d1-129">A user-defined type cannot explicitly overload the `-=` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="eb9d1-130">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="eb9d1-130">C# language specification</span></span>

<span data-ttu-id="eb9d1-131">Další informace naleznete v částech [unární operátor minus](~/_csharplang/spec/expressions.md#unary-minus-operator) a [odčítání](~/_csharplang/spec/expressions.md#subtraction-operator) v tématu [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="eb9d1-131">For more information, see the [Unary minus operator](~/_csharplang/spec/expressions.md#unary-minus-operator) and [Subtraction operator](~/_csharplang/spec/expressions.md#subtraction-operator) sections of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="eb9d1-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="eb9d1-132">See also</span></span>

- [<span data-ttu-id="eb9d1-133">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="eb9d1-133">C# reference</span></span>](../index.md)
- [<span data-ttu-id="eb9d1-134">Operátory a výrazy v C#</span><span class="sxs-lookup"><span data-stu-id="eb9d1-134">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="eb9d1-135">Události</span><span class="sxs-lookup"><span data-stu-id="eb9d1-135">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="eb9d1-136">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="eb9d1-136">Arithmetic operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="eb9d1-137">+ a + = – operátory</span><span class="sxs-lookup"><span data-stu-id="eb9d1-137">+ and += operators</span></span>](addition-operator.md)
