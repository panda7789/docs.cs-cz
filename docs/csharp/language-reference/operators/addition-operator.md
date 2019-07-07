---
title: + operátory a operátory += – C# odkaz
ms.custom: seodec18
ms.date: 05/24/2019
f1_keywords:
- +_CSharpKeyword
- +=_CSharpKeyword
helpviewer_keywords:
- addition operator [C#]
- concatenation operator [C#]
- delegate combination [C#]
- + operator [C#]
- addition assignment operator [C#]
- event subscription [C#]
- += operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: 41355dbadd566648b45d825cdd6515bfc6d411aa
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610042"
---
# <a name="-and--operators-c-reference"></a><span data-ttu-id="bf1f7-102">+ a operátory += (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="bf1f7-102">+ and += operators (C# reference)</span></span>

<span data-ttu-id="bf1f7-103">`+` Předdefinovaných číselných typů, podporuje operátor [řetězec](../keywords/string.md) typ, a [delegovat](../keywords/delegate.md) typy.</span><span class="sxs-lookup"><span data-stu-id="bf1f7-103">The `+` operator is supported by the built-in numeric types, [string](../keywords/string.md) type, and [delegate](../keywords/delegate.md) types.</span></span>

<span data-ttu-id="bf1f7-104">Informace o aritmetické operace `+` operátoru, najdete v článku [Unární plus a minus operátory](arithmetic-operators.md#unary-plus-and-minus-operators) a [operátor sčítání +](arithmetic-operators.md#addition-operator-) oddíly [aritmetické operátory](arithmetic-operators.md)článku.</span><span class="sxs-lookup"><span data-stu-id="bf1f7-104">For information about the arithmetic `+` operator, see the [Unary plus and minus operators](arithmetic-operators.md#unary-plus-and-minus-operators) and [Addition operator +](arithmetic-operators.md#addition-operator-) sections of the [Arithmetic operators](arithmetic-operators.md) article.</span></span>

## <a name="string-concatenation"></a><span data-ttu-id="bf1f7-105">Zřetězení řetězců</span><span class="sxs-lookup"><span data-stu-id="bf1f7-105">String concatenation</span></span>

<span data-ttu-id="bf1f7-106">Když se jeden nebo oba operandy typu [řetězec](../keywords/string.md), `+` zřetězí řetězcové reprezentace jeho operandy operátoru:</span><span class="sxs-lookup"><span data-stu-id="bf1f7-106">When one or both operands are of type [string](../keywords/string.md), the `+` operator concatenates the string representations of its operands:</span></span>

[!code-csharp-interactive[string concatenation](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddStrings)]

<span data-ttu-id="bf1f7-107">Počínaje C# 6, [interpolace](../tokens/interpolated.md) poskytuje pohodlnější způsob, jak formátovací řetězce:</span><span class="sxs-lookup"><span data-stu-id="bf1f7-107">Starting with C# 6, [string interpolation](../tokens/interpolated.md) provides a more convenient way to format strings:</span></span>

[!code-csharp-interactive[string interpolation](~/samples/csharp/language-reference/operators/AdditionOperator.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a><span data-ttu-id="bf1f7-108">Kombinaci delegátů</span><span class="sxs-lookup"><span data-stu-id="bf1f7-108">Delegate combination</span></span>

<span data-ttu-id="bf1f7-109">Pro operandy stejného [delegovat](../keywords/delegate.md) typ, `+` operátor vrátí novou instanci delegáta, která při vyvolání, vyvolá operand levé straně a potom se vyvolá operand pravé strany.</span><span class="sxs-lookup"><span data-stu-id="bf1f7-109">For operands of the same [delegate](../keywords/delegate.md) type, the `+` operator returns a new delegate instance that, when invoked, invokes the left-hand operand and then invokes the right-hand operand.</span></span> <span data-ttu-id="bf1f7-110">Pokud kterýkoli z operandů `null`, `+` operátor vrátí hodnotu jiný operand (která může být také `null`).</span><span class="sxs-lookup"><span data-stu-id="bf1f7-110">If any of the operands is `null`, the `+` operator returns the value of another operand (which also might be `null`).</span></span> <span data-ttu-id="bf1f7-111">Následující příklad ukazuje, jak mohou být kombinovány delegáty s `+` operátor:</span><span class="sxs-lookup"><span data-stu-id="bf1f7-111">The following example shows how delegates can be combined with the `+` operator:</span></span>

[!code-csharp-interactive[delegate combination](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddDelegates)]

<span data-ttu-id="bf1f7-112">Chcete-li provést odebrání delegátů, použijte [ `-` operátor](subtraction-operator.md#delegate-removal).</span><span class="sxs-lookup"><span data-stu-id="bf1f7-112">To perform delegate removal, use the [`-` operator](subtraction-operator.md#delegate-removal).</span></span>

<span data-ttu-id="bf1f7-113">Další informace o typech delegáta, naleznete v tématu [delegáti](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="bf1f7-113">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="addition-assignment-operator-"></a><span data-ttu-id="bf1f7-114">+= – Operátor přiřazení sčítání</span><span class="sxs-lookup"><span data-stu-id="bf1f7-114">Addition assignment operator +=</span></span>

<span data-ttu-id="bf1f7-115">Pomocí výrazu `+=` operátorů, například</span><span class="sxs-lookup"><span data-stu-id="bf1f7-115">An expression using the `+=` operator, such as</span></span>

```csharp
x += y
```

<span data-ttu-id="bf1f7-116">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="bf1f7-116">is equivalent to</span></span>

```csharp
x = x + y
```

<span data-ttu-id="bf1f7-117">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="bf1f7-117">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="bf1f7-118">Následující příklad ukazuje použití `+=` operátor:</span><span class="sxs-lookup"><span data-stu-id="bf1f7-118">The following example demonstrates the usage of the `+=` operator:</span></span>

[!code-csharp-interactive[+= examples](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddAndAssign)]

<span data-ttu-id="bf1f7-119">Můžete také použít `+=` operátor zadat metodu obslužné rutiny události, když se přihlásíte k odběru [události](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="bf1f7-119">You also use the `+=` operator to specify an event handler method when you subscribe to an [event](../keywords/event.md).</span></span> <span data-ttu-id="bf1f7-120">Další informace najdete v tématu [postupy: přihlášení k odběru a zrušit její odběr události](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="bf1f7-120">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="bf1f7-121">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="bf1f7-121">Operator overloadability</span></span>

<span data-ttu-id="bf1f7-122">Uživatelem definovaný typ může [přetížení](operator-overloading.md) `+` operátor.</span><span class="sxs-lookup"><span data-stu-id="bf1f7-122">A user-defined type can [overload](operator-overloading.md) the `+` operator.</span></span> <span data-ttu-id="bf1f7-123">Když do binárního souboru `+` je operátor přetížen, `+=` je také implicitně přetížený operátor.</span><span class="sxs-lookup"><span data-stu-id="bf1f7-123">When a binary `+` operator is overloaded, the `+=` operator is also implicitly overloaded.</span></span> <span data-ttu-id="bf1f7-124">Uživatelem definovaný typ nejde přetížit explicitně `+=` operátor.</span><span class="sxs-lookup"><span data-stu-id="bf1f7-124">A user-defined type cannot explicitly overload the `+=` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="bf1f7-125">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bf1f7-125">C# language specification</span></span>

<span data-ttu-id="bf1f7-126">Další informace najdete v tématu [unární operátor plus](~/_csharplang/spec/expressions.md#unary-plus-operator) a [operátor sčítání](~/_csharplang/spec/expressions.md#addition-operator) oddíly [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="bf1f7-126">For more information, see the [Unary plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) and [Addition operator](~/_csharplang/spec/expressions.md#addition-operator) sections of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bf1f7-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bf1f7-127">See also</span></span>

- [<span data-ttu-id="bf1f7-128">C#referenční dokumentace</span><span class="sxs-lookup"><span data-stu-id="bf1f7-128">C# reference</span></span>](../index.md)
- [<span data-ttu-id="bf1f7-129">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bf1f7-129">C# operators</span></span>](index.md)
- [<span data-ttu-id="bf1f7-130">Interpolace řetězců</span><span class="sxs-lookup"><span data-stu-id="bf1f7-130">String interpolation</span></span>](../tokens/interpolated.md)
- [<span data-ttu-id="bf1f7-131">Postupy: řetězení více řetězců</span><span class="sxs-lookup"><span data-stu-id="bf1f7-131">How to: concatenate multiple strings</span></span>](../../how-to/concatenate-multiple-strings.md)
- [<span data-ttu-id="bf1f7-132">Delegáti</span><span class="sxs-lookup"><span data-stu-id="bf1f7-132">Delegates</span></span>](../../programming-guide/delegates/index.md)
- [<span data-ttu-id="bf1f7-133">Události</span><span class="sxs-lookup"><span data-stu-id="bf1f7-133">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="bf1f7-134">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="bf1f7-134">Arithmetic operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="bf1f7-135">– operátory a operátory-=</span><span class="sxs-lookup"><span data-stu-id="bf1f7-135">- and -= operators</span></span>](subtraction-operator.md)
