---
title: + a + = operátory – C# referenční informace
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
ms.openlocfilehash: 709994632d704c6a9c6c7f4fc7180ae08cb901d7
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039094"
---
# <a name="-and--operators-c-reference"></a><span data-ttu-id="96a6a-102">+ a + = – operátoryC# (Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="96a6a-102">+ and += operators (C# reference)</span></span>

<span data-ttu-id="96a6a-103">Operátory `+` a `+=` jsou podporovány integrovanými čísly [integrálních](../builtin-types/integral-numeric-types.md) typů a čísel s [plovoucí desetinnou](../builtin-types/floating-point-numeric-types.md) čárkou, typu [řetězce](../builtin-types/reference-types.md#the-string-type) a typy [delegátů](../builtin-types/reference-types.md#the-delegate-type) .</span><span class="sxs-lookup"><span data-stu-id="96a6a-103">The `+` and `+=` operators are supported by the built-in [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types, the [string](../builtin-types/reference-types.md#the-string-type) type, and [delegate](../builtin-types/reference-types.md#the-delegate-type) types.</span></span>

<span data-ttu-id="96a6a-104">Informace o aritmetickém operátoru `+` naleznete v části [unární operátory plus a minus](arithmetic-operators.md#unary-plus-and-minus-operators) a [operátor sčítání](arithmetic-operators.md#addition-operator-) a další části v článku [aritmetické operátory](arithmetic-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="96a6a-104">For information about the arithmetic `+` operator, see the [Unary plus and minus operators](arithmetic-operators.md#unary-plus-and-minus-operators) and [Addition operator +](arithmetic-operators.md#addition-operator-) sections of the [Arithmetic operators](arithmetic-operators.md) article.</span></span>

## <a name="string-concatenation"></a><span data-ttu-id="96a6a-105">Zřetězení řetězců</span><span class="sxs-lookup"><span data-stu-id="96a6a-105">String concatenation</span></span>

<span data-ttu-id="96a6a-106">Když je jeden nebo oba operandy typu [String](../builtin-types/reference-types.md#the-string-type), operátor `+` zřetězí řetězcové reprezentace svých operandů:</span><span class="sxs-lookup"><span data-stu-id="96a6a-106">When one or both operands are of type [string](../builtin-types/reference-types.md#the-string-type), the `+` operator concatenates the string representations of its operands:</span></span>

[!code-csharp-interactive[string concatenation](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddStrings)]

<span data-ttu-id="96a6a-107">Počínaje C# 6, [interpolace řetězců](../tokens/interpolated.md) poskytuje pohodlnější způsob formátování řetězců:</span><span class="sxs-lookup"><span data-stu-id="96a6a-107">Beginning with C# 6, [string interpolation](../tokens/interpolated.md) provides a more convenient way to format strings:</span></span>

[!code-csharp-interactive[string interpolation](~/samples/csharp/language-reference/operators/AdditionOperator.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a><span data-ttu-id="96a6a-108">Kombinace delegátů</span><span class="sxs-lookup"><span data-stu-id="96a6a-108">Delegate combination</span></span>

<span data-ttu-id="96a6a-109">U operandů stejného typu [delegát](../builtin-types/reference-types.md#the-delegate-type) vrací operátor `+` novou instanci delegáta, která při vyvolání vyvolá levý operand a poté vyvolá operand na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="96a6a-109">For operands of the same [delegate](../builtin-types/reference-types.md#the-delegate-type) type, the `+` operator returns a new delegate instance that, when invoked, invokes the left-hand operand and then invokes the right-hand operand.</span></span> <span data-ttu-id="96a6a-110">Pokud je některý z operandů `null`, vrátí operátor `+` hodnotu jiného operandu (který také může být `null`).</span><span class="sxs-lookup"><span data-stu-id="96a6a-110">If any of the operands is `null`, the `+` operator returns the value of another operand (which also might be `null`).</span></span> <span data-ttu-id="96a6a-111">Následující příklad ukazuje, jak mohou být Delegáti kombinováni s operátorem `+`:</span><span class="sxs-lookup"><span data-stu-id="96a6a-111">The following example shows how delegates can be combined with the `+` operator:</span></span>

[!code-csharp-interactive[delegate combination](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddDelegates)]

<span data-ttu-id="96a6a-112">Chcete-li provést odebrání delegáta, použijte [operátor`-`](subtraction-operator.md#delegate-removal).</span><span class="sxs-lookup"><span data-stu-id="96a6a-112">To perform delegate removal, use the [`-` operator](subtraction-operator.md#delegate-removal).</span></span>

<span data-ttu-id="96a6a-113">Další informace o typech delegátů naleznete v tématu [Delegates](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="96a6a-113">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="addition-assignment-operator-"></a><span data-ttu-id="96a6a-114">Operátor přiřazení sčítání + =</span><span class="sxs-lookup"><span data-stu-id="96a6a-114">Addition assignment operator +=</span></span>

<span data-ttu-id="96a6a-115">Výraz používající operátor `+=`, například</span><span class="sxs-lookup"><span data-stu-id="96a6a-115">An expression using the `+=` operator, such as</span></span>

```csharp
x += y
```

<span data-ttu-id="96a6a-116">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="96a6a-116">is equivalent to</span></span>

```csharp
x = x + y
```

<span data-ttu-id="96a6a-117">s výjimkou, že `x` je vyhodnocena pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="96a6a-117">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="96a6a-118">Následující příklad ukazuje použití operátoru `+=`:</span><span class="sxs-lookup"><span data-stu-id="96a6a-118">The following example demonstrates the usage of the `+=` operator:</span></span>

[!code-csharp-interactive[+= examples](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddAndAssign)]

<span data-ttu-id="96a6a-119">Operátor `+=` lze také použít k určení metody obslužné rutiny události při přihlášení k odběru [události](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="96a6a-119">You also use the `+=` operator to specify an event handler method when you subscribe to an [event](../keywords/event.md).</span></span> <span data-ttu-id="96a6a-120">Další informace najdete v tématu [Postup: přihlášení a](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)odhlášení odběru událostí.</span><span class="sxs-lookup"><span data-stu-id="96a6a-120">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="96a6a-121">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="96a6a-121">Operator overloadability</span></span>

<span data-ttu-id="96a6a-122">Uživatelsky definovaný typ může [přetížit](operator-overloading.md) operátor `+`.</span><span class="sxs-lookup"><span data-stu-id="96a6a-122">A user-defined type can [overload](operator-overloading.md) the `+` operator.</span></span> <span data-ttu-id="96a6a-123">Je-li operátor binárního `+` přetížen, je operátor `+=` také implicitně přetížený.</span><span class="sxs-lookup"><span data-stu-id="96a6a-123">When a binary `+` operator is overloaded, the `+=` operator is also implicitly overloaded.</span></span> <span data-ttu-id="96a6a-124">Uživatelsky definovaný typ nemůže explicitně přetížit operátor `+=`.</span><span class="sxs-lookup"><span data-stu-id="96a6a-124">A user-defined type cannot explicitly overload the `+=` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="96a6a-125">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="96a6a-125">C# language specification</span></span>

<span data-ttu-id="96a6a-126">Další informace naleznete v částech [unárního operátoru plus](~/_csharplang/spec/expressions.md#unary-plus-operator) a [operátoru sčítání](~/_csharplang/spec/expressions.md#addition-operator) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="96a6a-126">For more information, see the [Unary plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) and [Addition operator](~/_csharplang/spec/expressions.md#addition-operator) sections of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="96a6a-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="96a6a-127">See also</span></span>

- [<span data-ttu-id="96a6a-128">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="96a6a-128">C# reference</span></span>](../index.md)
- [<span data-ttu-id="96a6a-129">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="96a6a-129">C# operators</span></span>](index.md)
- [<span data-ttu-id="96a6a-130">Postupy: zřetězení více řetězců</span><span class="sxs-lookup"><span data-stu-id="96a6a-130">How to: concatenate multiple strings</span></span>](../../how-to/concatenate-multiple-strings.md)
- [<span data-ttu-id="96a6a-131">Události</span><span class="sxs-lookup"><span data-stu-id="96a6a-131">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="96a6a-132">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="96a6a-132">Arithmetic operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="96a6a-133">-a-= – operátory</span><span class="sxs-lookup"><span data-stu-id="96a6a-133">- and -= operators</span></span>](subtraction-operator.md)
