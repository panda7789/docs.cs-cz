---
title: + a += operátory - c# odkaz
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
ms.openlocfilehash: cafd07f4b4aefdcc4b43750d61c155fe3d65aa46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399299"
---
# <a name="-and--operators-c-reference"></a><span data-ttu-id="e0ebc-102">+ a += operátory (odkaz C#)</span><span class="sxs-lookup"><span data-stu-id="e0ebc-102">+ and += operators (C# reference)</span></span>

<span data-ttu-id="e0ebc-103">A `+` `+=` operátory jsou podporovány předdefinované [integrální](../builtin-types/integral-numeric-types.md) a [plovoucí desetinnou desetinnou](../builtin-types/floating-point-numeric-types.md) hodnotou, typem [řetězce](../builtin-types/reference-types.md#the-string-type) a [delegací.](../builtin-types/reference-types.md#the-delegate-type)</span><span class="sxs-lookup"><span data-stu-id="e0ebc-103">The `+` and `+=` operators are supported by the built-in [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types, the [string](../builtin-types/reference-types.md#the-string-type) type, and [delegate](../builtin-types/reference-types.md#the-delegate-type) types.</span></span>

<span data-ttu-id="e0ebc-104">Informace o `+` operátoru aritmetiky naleznete [unary plus a minus operátory](arithmetic-operators.md#unary-plus-and-minus-operators) a sčítání operátor [+](arithmetic-operators.md#addition-operator-) části [aritmetické operátory](arithmetic-operators.md) článku.</span><span class="sxs-lookup"><span data-stu-id="e0ebc-104">For information about the arithmetic `+` operator, see the [Unary plus and minus operators](arithmetic-operators.md#unary-plus-and-minus-operators) and [Addition operator +](arithmetic-operators.md#addition-operator-) sections of the [Arithmetic operators](arithmetic-operators.md) article.</span></span>

## <a name="string-concatenation"></a><span data-ttu-id="e0ebc-105">Zřetězení řetězců</span><span class="sxs-lookup"><span data-stu-id="e0ebc-105">String concatenation</span></span>

<span data-ttu-id="e0ebc-106">Pokud jeden nebo oba operandy jsou `+` typu [řetězce](../builtin-types/reference-types.md#the-string-type), operátor zřetězí řetězcové reprezentace jeho operandů:</span><span class="sxs-lookup"><span data-stu-id="e0ebc-106">When one or both operands are of type [string](../builtin-types/reference-types.md#the-string-type), the `+` operator concatenates the string representations of its operands:</span></span>

[!code-csharp-interactive[string concatenation](snippets/AdditionOperator.cs#AddStrings)]

<span data-ttu-id="e0ebc-107">Počínaje C# 6, [řetězec interpolace](../tokens/interpolated.md) poskytuje pohodlnější způsob, jak formátovat řetězce:</span><span class="sxs-lookup"><span data-stu-id="e0ebc-107">Beginning with C# 6, [string interpolation](../tokens/interpolated.md) provides a more convenient way to format strings:</span></span>

[!code-csharp-interactive[string interpolation](snippets/AdditionOperator.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a><span data-ttu-id="e0ebc-108">Kombinace delegátů</span><span class="sxs-lookup"><span data-stu-id="e0ebc-108">Delegate combination</span></span>

<span data-ttu-id="e0ebc-109">Pro operandy stejného typu `+` [delegáta](../builtin-types/reference-types.md#the-delegate-type) operátor vrátí novou instanci delegáta, která při vyvolání vyvolá operand u levé ruky a potom vyvolá pravostranný operand.</span><span class="sxs-lookup"><span data-stu-id="e0ebc-109">For operands of the same [delegate](../builtin-types/reference-types.md#the-delegate-type) type, the `+` operator returns a new delegate instance that, when invoked, invokes the left-hand operand and then invokes the right-hand operand.</span></span> <span data-ttu-id="e0ebc-110">Pokud některý z operandů `null` `+` je , operátor vrátí hodnotu jiného `null`operandu (což může být také ).</span><span class="sxs-lookup"><span data-stu-id="e0ebc-110">If any of the operands is `null`, the `+` operator returns the value of another operand (which also might be `null`).</span></span> <span data-ttu-id="e0ebc-111">Následující příklad ukazuje, jak lze delegáty kombinovat s operátorem: `+`</span><span class="sxs-lookup"><span data-stu-id="e0ebc-111">The following example shows how delegates can be combined with the `+` operator:</span></span>

[!code-csharp-interactive[delegate combination](snippets/AdditionOperator.cs#AddDelegates)]

<span data-ttu-id="e0ebc-112">Chcete-li provést odebrání [ `-` ](subtraction-operator.md#delegate-removal)delegáta, použijte operátor .</span><span class="sxs-lookup"><span data-stu-id="e0ebc-112">To perform delegate removal, use the [`-` operator](subtraction-operator.md#delegate-removal).</span></span>

<span data-ttu-id="e0ebc-113">Další informace o typech delegátů naleznete v tématu [Delegáti](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="e0ebc-113">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="addition-assignment-operator-"></a><span data-ttu-id="e0ebc-114">Operátor přiřazení sčítání +=</span><span class="sxs-lookup"><span data-stu-id="e0ebc-114">Addition assignment operator +=</span></span>

<span data-ttu-id="e0ebc-115">Výraz používající `+=` operátor, například</span><span class="sxs-lookup"><span data-stu-id="e0ebc-115">An expression using the `+=` operator, such as</span></span>

```csharp
x += y
```

<span data-ttu-id="e0ebc-116">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="e0ebc-116">is equivalent to</span></span>

```csharp
x = x + y
```

<span data-ttu-id="e0ebc-117">kromě `x` toho, že se vyhodnocuje pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="e0ebc-117">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="e0ebc-118">Následující příklad ukazuje použití operátoru: `+=`</span><span class="sxs-lookup"><span data-stu-id="e0ebc-118">The following example demonstrates the usage of the `+=` operator:</span></span>

[!code-csharp-interactive[+= examples](snippets/AdditionOperator.cs#AddAndAssign)]

<span data-ttu-id="e0ebc-119">`+=` Operátor můžete také použít k určení metody obslužné rutiny události při přihlášení k odběru [události](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="e0ebc-119">You also use the `+=` operator to specify an event handler method when you subscribe to an [event](../keywords/event.md).</span></span> <span data-ttu-id="e0ebc-120">Další informace naleznete v [tématu Jak: přihlásit se k odběru a odhlásit se z odběru událostí](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="e0ebc-120">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="e0ebc-121">Přetížení obsluhy</span><span class="sxs-lookup"><span data-stu-id="e0ebc-121">Operator overloadability</span></span>

<span data-ttu-id="e0ebc-122">Uživatelem definovaný typ může `+` [přetížit](operator-overloading.md) operátor.</span><span class="sxs-lookup"><span data-stu-id="e0ebc-122">A user-defined type can [overload](operator-overloading.md) the `+` operator.</span></span> <span data-ttu-id="e0ebc-123">Když binární `+` operátor je přetížený, `+=` operátor je také implicitně přetížené.</span><span class="sxs-lookup"><span data-stu-id="e0ebc-123">When a binary `+` operator is overloaded, the `+=` operator is also implicitly overloaded.</span></span> <span data-ttu-id="e0ebc-124">Uživatelem definovaný typ nemůže `+=` explicitně přetížit operátor.</span><span class="sxs-lookup"><span data-stu-id="e0ebc-124">A user-defined type cannot explicitly overload the `+=` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e0ebc-125">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e0ebc-125">C# language specification</span></span>

<span data-ttu-id="e0ebc-126">Další informace naleznete [unary plus operátor](~/_csharplang/spec/expressions.md#unary-plus-operator) a [sčítání operátor](~/_csharplang/spec/expressions.md#addition-operator) části [c# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="e0ebc-126">For more information, see the [Unary plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) and [Addition operator](~/_csharplang/spec/expressions.md#addition-operator) sections of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e0ebc-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="e0ebc-127">See also</span></span>

- [<span data-ttu-id="e0ebc-128">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="e0ebc-128">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e0ebc-129">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e0ebc-129">C# operators</span></span>](index.md)
- [<span data-ttu-id="e0ebc-130">Jak zřetězit více řetězců</span><span class="sxs-lookup"><span data-stu-id="e0ebc-130">How to concatenate multiple strings</span></span>](../../how-to/concatenate-multiple-strings.md)
- [<span data-ttu-id="e0ebc-131">Akce</span><span class="sxs-lookup"><span data-stu-id="e0ebc-131">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="e0ebc-132">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="e0ebc-132">Arithmetic operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="e0ebc-133">- a -= operátoři</span><span class="sxs-lookup"><span data-stu-id="e0ebc-133">- and -= operators</span></span>](subtraction-operator.md)
