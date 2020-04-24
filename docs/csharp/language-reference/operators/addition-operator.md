---
title: + and + = Operators-C# Reference
ms.date: 04/23/2020
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
ms.openlocfilehash: 18364d80b8117fd4074c2c4231eac07c76829bb3
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135734"
---
# <a name="-and--operators-c-reference"></a><span data-ttu-id="c7471-102">+ a + = – operátory (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="c7471-102">+ and += operators (C# reference)</span></span>

<span data-ttu-id="c7471-103">Operátory `+` a `+=` jsou podporovány integrovanými [celočíselnými](../builtin-types/integral-numeric-types.md) typy a čísly s [plovoucí desetinnou](../builtin-types/floating-point-numeric-types.md) čárkou, typem [řetězce](../builtin-types/reference-types.md#the-string-type) a typy [delegátů](../builtin-types/reference-types.md#the-delegate-type) .</span><span class="sxs-lookup"><span data-stu-id="c7471-103">The `+` and `+=` operators are supported by the built-in [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types, the [string](../builtin-types/reference-types.md#the-string-type) type, and [delegate](../builtin-types/reference-types.md#the-delegate-type) types.</span></span>

<span data-ttu-id="c7471-104">Informace o `+` aritmetickém operátoru naleznete v tématu [unární operátory plus a minus](arithmetic-operators.md#unary-plus-and-minus-operators) a [operátor sčítání](arithmetic-operators.md#addition-operator-) a další části v článku [aritmetické operátory](arithmetic-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="c7471-104">For information about the arithmetic `+` operator, see the [Unary plus and minus operators](arithmetic-operators.md#unary-plus-and-minus-operators) and [Addition operator +](arithmetic-operators.md#addition-operator-) sections of the [Arithmetic operators](arithmetic-operators.md) article.</span></span>

## <a name="string-concatenation"></a><span data-ttu-id="c7471-105">Zřetězení řetězců</span><span class="sxs-lookup"><span data-stu-id="c7471-105">String concatenation</span></span>

<span data-ttu-id="c7471-106">Když je jeden nebo oba operandy typu [String](../builtin-types/reference-types.md#the-string-type), `+` operátor zřetězí řetězcové reprezentace svých operandů (řetězcové vyjádření `null` je prázdným řetězcem):</span><span class="sxs-lookup"><span data-stu-id="c7471-106">When one or both operands are of type [string](../builtin-types/reference-types.md#the-string-type), the `+` operator concatenates the string representations of its operands (the string representation of `null` is an empty string):</span></span>

[!code-csharp-interactive[string concatenation](snippets/AdditionOperator.cs#AddStrings)]

<span data-ttu-id="c7471-107">Počínaje jazykem C# 6 poskytuje [interpolace řetězců](../tokens/interpolated.md) pohodlnější způsob formátování řetězců:</span><span class="sxs-lookup"><span data-stu-id="c7471-107">Beginning with C# 6, [string interpolation](../tokens/interpolated.md) provides a more convenient way to format strings:</span></span>

[!code-csharp-interactive[string interpolation](snippets/AdditionOperator.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a><span data-ttu-id="c7471-108">Kombinace delegátů</span><span class="sxs-lookup"><span data-stu-id="c7471-108">Delegate combination</span></span>

<span data-ttu-id="c7471-109">Pro operandy stejného typu [delegáta](../builtin-types/reference-types.md#the-delegate-type) vrátí `+` operátor novou instanci delegáta, která při vyvolání vyvolá levý operand a poté vyvolá operand na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="c7471-109">For operands of the same [delegate](../builtin-types/reference-types.md#the-delegate-type) type, the `+` operator returns a new delegate instance that, when invoked, invokes the left-hand operand and then invokes the right-hand operand.</span></span> <span data-ttu-id="c7471-110">Pokud je `null`některý z operandů, `+` operátor vrátí hodnotu jiného operandu (což může být `null`také).</span><span class="sxs-lookup"><span data-stu-id="c7471-110">If any of the operands is `null`, the `+` operator returns the value of another operand (which also might be `null`).</span></span> <span data-ttu-id="c7471-111">Následující příklad ukazuje, jak mohou být Delegáti kombinováni `+` s operátorem:</span><span class="sxs-lookup"><span data-stu-id="c7471-111">The following example shows how delegates can be combined with the `+` operator:</span></span>

[!code-csharp-interactive[delegate combination](snippets/AdditionOperator.cs#AddDelegates)]

<span data-ttu-id="c7471-112">Chcete-li provést odebrání delegáta, použijte [ `-` operátor](subtraction-operator.md#delegate-removal).</span><span class="sxs-lookup"><span data-stu-id="c7471-112">To perform delegate removal, use the [`-` operator](subtraction-operator.md#delegate-removal).</span></span>

<span data-ttu-id="c7471-113">Další informace o typech delegátů naleznete v tématu [Delegates](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="c7471-113">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="addition-assignment-operator-"></a><span data-ttu-id="c7471-114">Operátor přiřazení sčítání + =</span><span class="sxs-lookup"><span data-stu-id="c7471-114">Addition assignment operator +=</span></span>

<span data-ttu-id="c7471-115">Výraz, který `+=` používá operátor, například</span><span class="sxs-lookup"><span data-stu-id="c7471-115">An expression using the `+=` operator, such as</span></span>

```csharp
x += y
```

<span data-ttu-id="c7471-116">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="c7471-116">is equivalent to</span></span>

```csharp
x = x + y
```

<span data-ttu-id="c7471-117">s výjimkou, že `x` je vyhodnocena pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="c7471-117">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="c7471-118">Následující příklad ukazuje použití `+=` operátoru:</span><span class="sxs-lookup"><span data-stu-id="c7471-118">The following example demonstrates the usage of the `+=` operator:</span></span>

[!code-csharp-interactive[+= examples](snippets/AdditionOperator.cs#AddAndAssign)]

<span data-ttu-id="c7471-119">`+=` Operátor můžete také použít k určení metody obslužné rutiny události při přihlášení k odběru [události](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="c7471-119">You also use the `+=` operator to specify an event handler method when you subscribe to an [event](../keywords/event.md).</span></span> <span data-ttu-id="c7471-120">Další informace najdete v tématu [Postup: přihlášení a](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)odhlášení odběru událostí.</span><span class="sxs-lookup"><span data-stu-id="c7471-120">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="c7471-121">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="c7471-121">Operator overloadability</span></span>

<span data-ttu-id="c7471-122">Uživatelsky definovaný typ může [přetížit](operator-overloading.md) `+` operátor.</span><span class="sxs-lookup"><span data-stu-id="c7471-122">A user-defined type can [overload](operator-overloading.md) the `+` operator.</span></span> <span data-ttu-id="c7471-123">Při přetížení binárního `+` operátoru je `+=` operátor také implicitně přetížený.</span><span class="sxs-lookup"><span data-stu-id="c7471-123">When a binary `+` operator is overloaded, the `+=` operator is also implicitly overloaded.</span></span> <span data-ttu-id="c7471-124">Uživatelsky definovaný typ nemůže explicitně přetížit `+=` operátor.</span><span class="sxs-lookup"><span data-stu-id="c7471-124">A user-defined type cannot explicitly overload the `+=` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c7471-125">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c7471-125">C# language specification</span></span>

<span data-ttu-id="c7471-126">Další informace naleznete v částech [unárního operátoru plus](~/_csharplang/spec/expressions.md#unary-plus-operator) a [operátoru sčítání](~/_csharplang/spec/expressions.md#addition-operator) ve [specifikaci jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="c7471-126">For more information, see the [Unary plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) and [Addition operator](~/_csharplang/spec/expressions.md#addition-operator) sections of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c7471-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7471-127">See also</span></span>

- [<span data-ttu-id="c7471-128">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="c7471-128">C# reference</span></span>](../index.md)
- [<span data-ttu-id="c7471-129">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c7471-129">C# operators</span></span>](index.md)
- [<span data-ttu-id="c7471-130">Jak zřetězit více řetězců</span><span class="sxs-lookup"><span data-stu-id="c7471-130">How to concatenate multiple strings</span></span>](../../how-to/concatenate-multiple-strings.md)
- [<span data-ttu-id="c7471-131">Události</span><span class="sxs-lookup"><span data-stu-id="c7471-131">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="c7471-132">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="c7471-132">Arithmetic operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="c7471-133">-a-= – operátory</span><span class="sxs-lookup"><span data-stu-id="c7471-133">- and -= operators</span></span>](subtraction-operator.md)
