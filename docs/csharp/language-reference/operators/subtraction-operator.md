---
title: '- a -= operátory - odkaz C#'
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
ms.openlocfilehash: 2017aade92e8d7ad2af7101a107122fa8d7b9e27
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847648"
---
# <a name="--and---operators-c-reference"></a><span data-ttu-id="0bb72-102">- a -= operátory (odkaz C#)</span><span class="sxs-lookup"><span data-stu-id="0bb72-102">- and -= operators (C# reference)</span></span>

<span data-ttu-id="0bb72-103">A `-` `-=` operátory jsou podporovány integrované [integrální](../builtin-types/integral-numeric-types.md) a [plovoucí desetinnou desetinnou](../builtin-types/floating-point-numeric-types.md) desetinnou a [delegací](../builtin-types/reference-types.md#the-delegate-type) typů.</span><span class="sxs-lookup"><span data-stu-id="0bb72-103">The `-` and `-=` operators are supported by the built-in [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types and [delegate](../builtin-types/reference-types.md#the-delegate-type) types.</span></span>

<span data-ttu-id="0bb72-104">Informace o operátoru `-` aritmetiky naleznete [unary plus a minus operátory](arithmetic-operators.md#unary-plus-and-minus-operators) a [odčítání operátor -](arithmetic-operators.md#subtraction-operator--) části [aritmetické operátory](arithmetic-operators.md) článku.</span><span class="sxs-lookup"><span data-stu-id="0bb72-104">For information about the arithmetic `-` operator, see the [Unary plus and minus operators](arithmetic-operators.md#unary-plus-and-minus-operators) and [Subtraction operator -](arithmetic-operators.md#subtraction-operator--) sections of the [Arithmetic operators](arithmetic-operators.md) article.</span></span>

## <a name="delegate-removal"></a><span data-ttu-id="0bb72-105">Odebrání delegáta</span><span class="sxs-lookup"><span data-stu-id="0bb72-105">Delegate removal</span></span>

<span data-ttu-id="0bb72-106">Pro operandy stejného typu `-` [delegáta](../builtin-types/reference-types.md#the-delegate-type) operátor vrátí instanci delegáta, která je vypočtena takto:</span><span class="sxs-lookup"><span data-stu-id="0bb72-106">For operands of the same [delegate](../builtin-types/reference-types.md#the-delegate-type) type, the `-` operator returns a delegate instance that is calculated as follows:</span></span>

- <span data-ttu-id="0bb72-107">Pokud oba operandy jsou non-null a vvolací seznam pravé operand je správné souvislé podseznam seznamu vyvolání levé operand, výsledkem operace je nový seznam vyvolání, který je získán odebráním pravé operand položky ze seznamu vyvolání levého operandu.</span><span class="sxs-lookup"><span data-stu-id="0bb72-107">If both operands are non-null and the invocation list of the right-hand operand is a proper contiguous sublist of the invocation list of the left-hand operand, the result of the operation is a new invocation list that is obtained by removing the right-hand operand's entries from the invocation list of the left-hand operand.</span></span> <span data-ttu-id="0bb72-108">Pokud seznam pravého operandu odpovídá více sousedícím podseznamům v seznamu levostranných operandů, bude odebrán pouze odpovídající podseznam vpravo.</span><span class="sxs-lookup"><span data-stu-id="0bb72-108">If the right-hand operand's list matches multiple contiguous sublists in the left-hand operand's list, only the right-most matching sublist is removed.</span></span> <span data-ttu-id="0bb72-109">Pokud má za následek odebrání prázdný `null`seznam, výsledek je .</span><span class="sxs-lookup"><span data-stu-id="0bb72-109">If removal results in an empty list, the result is `null`.</span></span>

  [!code-csharp-interactive[delegate removal](snippets/SubtractionOperator.cs#DelegateRemoval)]

- <span data-ttu-id="0bb72-110">Pokud seznam vyvolání pravého operandu není řádným souvislým dílčím seznamem seznamu vyvolání levého operandu, je výsledkem operace levostranný operand.</span><span class="sxs-lookup"><span data-stu-id="0bb72-110">If the invocation list of the right-hand operand is not a proper contiguous sublist of the invocation list of the left-hand operand, the result of the operation is the left-hand operand.</span></span> <span data-ttu-id="0bb72-111">Například odebrání delegáta, který není součástí delegáta vícesměrového vysílání, neprovede nic a výsledkem je nezměněný delegát vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="0bb72-111">For example, removing a delegate that is not part of the multicast delegate does nothing and results in the unchanged multicast delegate.</span></span>

  [!code-csharp-interactive[delegate removal with no effect](snippets/SubtractionOperator.cs#DelegateRemovalNoChange)]

  <span data-ttu-id="0bb72-112">Předchozí příklad také ukazuje, že během delegáta odstranění delegáta instance jsou porovnány.</span><span class="sxs-lookup"><span data-stu-id="0bb72-112">The preceding example also demonstrates that during delegate removal delegate instances are compared.</span></span> <span data-ttu-id="0bb72-113">Například delegáti, které jsou vyrobeny z vyhodnocení identické [lambda výrazy](../../programming-guide/statements-expressions-operators/lambda-expressions.md) nejsou stejné.</span><span class="sxs-lookup"><span data-stu-id="0bb72-113">For example, delegates that are produced from evaluation of identical [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) are not equal.</span></span> <span data-ttu-id="0bb72-114">Další informace o rovnosti delegátů naleznete v části [Operátory rovnosti delegátů](~/_csharplang/spec/expressions.md#delegate-equality-operators) [ve specifikaci jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="0bb72-114">For more information about delegate equality, see the [Delegate equality operators](~/_csharplang/spec/expressions.md#delegate-equality-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

- <span data-ttu-id="0bb72-115">Pokud je `null`levostranný operand , je `null`výsledkem operace .</span><span class="sxs-lookup"><span data-stu-id="0bb72-115">If the left-hand operand is `null`, the result of the operation is `null`.</span></span> <span data-ttu-id="0bb72-116">Pokud je `null`pravostranný operand , výsledkem operace je levostranný operand.</span><span class="sxs-lookup"><span data-stu-id="0bb72-116">If the right-hand operand is `null`, the result of the operation is the left-hand operand.</span></span>

  [!code-csharp-interactive[delegate removal and null](snippets/SubtractionOperator.cs#DelegateRemovalAndNull)]

<span data-ttu-id="0bb72-117">Chcete-li kombinovat [ `+` ](addition-operator.md#delegate-combination)delegáty, použijte operátor .</span><span class="sxs-lookup"><span data-stu-id="0bb72-117">To combine delegates, use the [`+` operator](addition-operator.md#delegate-combination).</span></span>

<span data-ttu-id="0bb72-118">Další informace o typech delegátů naleznete v tématu [Delegáti](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="0bb72-118">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="subtraction-assignment-operator--"></a><span data-ttu-id="0bb72-119">Operátor přiřazení odčítání -=</span><span class="sxs-lookup"><span data-stu-id="0bb72-119">Subtraction assignment operator -=</span></span>

<span data-ttu-id="0bb72-120">Výraz používající `-=` operátor, například</span><span class="sxs-lookup"><span data-stu-id="0bb72-120">An expression using the `-=` operator, such as</span></span>

```csharp
x -= y
```

<span data-ttu-id="0bb72-121">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="0bb72-121">is equivalent to</span></span>

```csharp
x = x - y
```

<span data-ttu-id="0bb72-122">kromě `x` toho, že se vyhodnocuje pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="0bb72-122">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="0bb72-123">Následující příklad ukazuje použití operátoru: `-=`</span><span class="sxs-lookup"><span data-stu-id="0bb72-123">The following example demonstrates the usage of the `-=` operator:</span></span>

[!code-csharp-interactive[-= examples](snippets/SubtractionOperator.cs#SubtractAndAssign)]

<span data-ttu-id="0bb72-124">Operátor můžete `-=` také použít k určení metody obslužné rutiny události, která má být odebrána při odhlášení z [odběru události](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="0bb72-124">You also use the `-=` operator to specify an event handler method to remove when you unsubscribe from an [event](../keywords/event.md).</span></span> <span data-ttu-id="0bb72-125">Další informace naleznete v tématu [Jak se přihlásit k odběru a odhlásit z odběru událostí](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="0bb72-125">For more information, see [How to subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="0bb72-126">Přetížení obsluhy</span><span class="sxs-lookup"><span data-stu-id="0bb72-126">Operator overloadability</span></span>

<span data-ttu-id="0bb72-127">Uživatelem definovaný typ může `-` [přetížit](operator-overloading.md) operátor.</span><span class="sxs-lookup"><span data-stu-id="0bb72-127">A user-defined type can [overload](operator-overloading.md) the `-` operator.</span></span> <span data-ttu-id="0bb72-128">Když binární `-` operátor je přetížený, `-=` operátor je také implicitně přetížené.</span><span class="sxs-lookup"><span data-stu-id="0bb72-128">When a binary `-` operator is overloaded, the `-=` operator is also implicitly overloaded.</span></span> <span data-ttu-id="0bb72-129">Uživatelem definovaný typ nemůže `-=` explicitně přetížit operátor.</span><span class="sxs-lookup"><span data-stu-id="0bb72-129">A user-defined type cannot explicitly overload the `-=` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0bb72-130">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0bb72-130">C# language specification</span></span>

<span data-ttu-id="0bb72-131">Další informace naleznete [unary minus operátor](~/_csharplang/spec/expressions.md#unary-minus-operator) a [odčítání operátor](~/_csharplang/spec/expressions.md#subtraction-operator) části [c# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="0bb72-131">For more information, see the [Unary minus operator](~/_csharplang/spec/expressions.md#unary-minus-operator) and [Subtraction operator](~/_csharplang/spec/expressions.md#subtraction-operator) sections of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0bb72-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="0bb72-132">See also</span></span>

- [<span data-ttu-id="0bb72-133">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="0bb72-133">C# reference</span></span>](../index.md)
- [<span data-ttu-id="0bb72-134">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0bb72-134">C# operators</span></span>](index.md)
- [<span data-ttu-id="0bb72-135">Akce</span><span class="sxs-lookup"><span data-stu-id="0bb72-135">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="0bb72-136">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="0bb72-136">Arithmetic operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="0bb72-137">+ a += operátory</span><span class="sxs-lookup"><span data-stu-id="0bb72-137">+ and += operators</span></span>](addition-operator.md)
