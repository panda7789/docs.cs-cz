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
ms.openlocfilehash: 9f43a863de69122e251204668af2ea989fcc993c
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300093"
---
# <a name="--and---operators-c-reference"></a><span data-ttu-id="49c80-102">– operátory a operátory-= (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="49c80-102">- and -= operators (C# Reference)</span></span>

<span data-ttu-id="49c80-103">`-` Operátor je podporován předdefinovaných číselných typů a [delegovat](../keywords/delegate.md) typy.</span><span class="sxs-lookup"><span data-stu-id="49c80-103">The `-` operator is supported by the built-in numeric types and [delegate](../keywords/delegate.md) types.</span></span>

<span data-ttu-id="49c80-104">Informace o aritmetické operace `-` operátoru, najdete v článku [Unární plus a minus operátory](arithmetic-operators.md#unary-plus-and-minus-operators) a [operátor odčítání -](arithmetic-operators.md#subtraction-operator--) oddíly [aritmetické operátory](arithmetic-operators.md) článku.</span><span class="sxs-lookup"><span data-stu-id="49c80-104">For information about the arithmetic `-` operator, see the [Unary plus and minus operators](arithmetic-operators.md#unary-plus-and-minus-operators) and [Subtraction operator -](arithmetic-operators.md#subtraction-operator--) sections of the [Arithmetic operators](arithmetic-operators.md) article.</span></span>

## <a name="delegate-removal"></a><span data-ttu-id="49c80-105">Odebrání delegátů</span><span class="sxs-lookup"><span data-stu-id="49c80-105">Delegate removal</span></span>

<span data-ttu-id="49c80-106">Pro operandy stejného [delegovat](../keywords/delegate.md) typ, `-` operátor vrátí instanci delegáta, který se vypočítává takto:</span><span class="sxs-lookup"><span data-stu-id="49c80-106">For operands of the same [delegate](../keywords/delegate.md) type, the `-` operator returns a delegate instance that is calculated as follows:</span></span>

- <span data-ttu-id="49c80-107">Pokud jsou oba operandy jinou hodnotu než null a vyvolání seznam druhého operandu je správné souvislých podseznam seznamu vyvolání prvního operandu, je výsledek operace nový seznam volání, která se získá tak, že odeberete položky druhého operandu od vyvolání seznamu prvního operandu.</span><span class="sxs-lookup"><span data-stu-id="49c80-107">If both operands are non-null and the invocation list of the second operand is a proper contiguous sublist of the invocation list of the first operand, the result of the operation is a new invocation list that is obtained by removing the second operand's entries from the invocation list of the first operand.</span></span> <span data-ttu-id="49c80-108">Pokud je druhý operand seznamu odpovídá několika dílčích souvislých v seznamu je první operand, odeberou se pouze odpovídající podseznam úplně vpravo.</span><span class="sxs-lookup"><span data-stu-id="49c80-108">If the second operand's list matches multiple contiguous sublists in the first operand's list, only the right-most matching sublist is removed.</span></span> <span data-ttu-id="49c80-109">Pokud je odebrání výsledkem je seznam prázdný, výsledkem je `null`.</span><span class="sxs-lookup"><span data-stu-id="49c80-109">If removal results in an empty list, the result is `null`.</span></span>
- <span data-ttu-id="49c80-110">Pokud seznamu vyvolání druhého operandu není správné souvislých podseznam seznamu vyvolání prvního operandu, je výsledek operace prvním operandem.</span><span class="sxs-lookup"><span data-stu-id="49c80-110">If the invocation list of the second operand is not a proper contiguous sublist of the invocation list of the first operand, the result of the operation is the first operand.</span></span>
- <span data-ttu-id="49c80-111">Pokud je první operand `null`, je výsledek operace `null`.</span><span class="sxs-lookup"><span data-stu-id="49c80-111">If the first operand is `null`, the result of the operation is `null`.</span></span> <span data-ttu-id="49c80-112">Pokud je druhý operand `null`, výsledkem operace je prvním operandem.</span><span class="sxs-lookup"><span data-stu-id="49c80-112">If the second operand is `null`, the result of the operation is the first operand.</span></span>

<span data-ttu-id="49c80-113">Následující příklad ukazuje způsob, jakým `-` operace provede odstranění delegáta:</span><span class="sxs-lookup"><span data-stu-id="49c80-113">The following example shows how the `-` operation performs delegate removal:</span></span>

[!code-csharp-interactive[delegate removal](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemoval)]

## <a name="subtraction-assignment-operator--"></a><span data-ttu-id="49c80-114">Operátor odčítání a přiřazení-=</span><span class="sxs-lookup"><span data-stu-id="49c80-114">Subtraction assignment operator -=</span></span>

<span data-ttu-id="49c80-115">Pomocí výrazu `-=` operátorů, například</span><span class="sxs-lookup"><span data-stu-id="49c80-115">An expression using the `-=` operator, such as</span></span>

```csharp
x -= y
```

<span data-ttu-id="49c80-116">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="49c80-116">is equivalent to</span></span>

```csharp
x = x - y
```

<span data-ttu-id="49c80-117">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="49c80-117">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="49c80-118">Následující příklad ukazuje použití `-=` operátor:</span><span class="sxs-lookup"><span data-stu-id="49c80-118">The following example demonstrates the usage of the `-=` operator:</span></span>

[!code-csharp-interactive[-= examples](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#SubtractAndAssign)]

<span data-ttu-id="49c80-119">Můžete také použít `-=` operátor zadat metodu obslužné rutiny události při vy nemusíte podnikat odebrat [události](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="49c80-119">You also use the `-=` operator to specify an event handler method to remove when you unsubscribe from an [event](../keywords/event.md).</span></span> <span data-ttu-id="49c80-120">Další informace najdete v tématu [postupy: přihlášení k odběru a zrušit její odběr události](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="49c80-120">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="49c80-121">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="49c80-121">Operator overloadability</span></span>

<span data-ttu-id="49c80-122">Uživatelem definovaný typ může [přetížení](../keywords/operator.md) `-` operátor.</span><span class="sxs-lookup"><span data-stu-id="49c80-122">A user-defined type can [overload](../keywords/operator.md) the `-` operator.</span></span> <span data-ttu-id="49c80-123">Když do binárního souboru `-` je operátor přetížen, `-=` je také implicitně přetížený operátor.</span><span class="sxs-lookup"><span data-stu-id="49c80-123">When a binary `-` operator is overloaded, the `-=` operator is also implicitly overloaded.</span></span> <span data-ttu-id="49c80-124">Uživatelem definovaný typ nejde přetížit explicitně `-=` operátor.</span><span class="sxs-lookup"><span data-stu-id="49c80-124">A user-defined type cannot explicitly overload the `-=` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="49c80-125">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="49c80-125">C# language specification</span></span>

<span data-ttu-id="49c80-126">Další informace najdete v tématu [unární operátor minus](~/_csharplang/spec/expressions.md#unary-minus-operator) a [operátor odčítání](~/_csharplang/spec/expressions.md#subtraction-operator) oddíly [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="49c80-126">For more information, see the [Unary minus operator](~/_csharplang/spec/expressions.md#unary-minus-operator) and [Subtraction operator](~/_csharplang/spec/expressions.md#subtraction-operator) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="49c80-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="49c80-127">See also</span></span>

- [<span data-ttu-id="49c80-128">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="49c80-128">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="49c80-129">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="49c80-129">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="49c80-130">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="49c80-130">C# Operators</span></span>](index.md)
- [<span data-ttu-id="49c80-131">Delegáti</span><span class="sxs-lookup"><span data-stu-id="49c80-131">Delegates</span></span>](../../programming-guide/delegates/index.md)
- [<span data-ttu-id="49c80-132">Události</span><span class="sxs-lookup"><span data-stu-id="49c80-132">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="49c80-133">Zaškrtnuto a nezaškrtnuto</span><span class="sxs-lookup"><span data-stu-id="49c80-133">Checked and unchecked</span></span>](../keywords/checked-and-unchecked.md)
- [<span data-ttu-id="49c80-134">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="49c80-134">Arithmetic operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="49c80-135">+ a operátory +=</span><span class="sxs-lookup"><span data-stu-id="49c80-135">+ and += operators</span></span>](addition-operator.md)
