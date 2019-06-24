---
title: ?? Operator - C# odkaz
ms.custom: seodec18
ms.date: 06/07/2019
f1_keywords:
- ??_CSharpKeyword
helpviewer_keywords:
- null-coalescing operator [C#]
- ?? operator [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: a19b5558da36ffb11dabd1b9bec419a3623a0f17
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/12/2019
ms.locfileid: "67024990"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="8e4a4-103">??</span><span class="sxs-lookup"><span data-stu-id="8e4a4-103">??</span></span> <span data-ttu-id="8e4a4-104">– operátor (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="8e4a4-104">operator (C# reference)</span></span>

<span data-ttu-id="8e4a4-105">Operátoru nulového sjednocení `??` vrací hodnotu svého operandu vlevo, pokud není `null`; v opačném případě zpracovával pravý operand vyhodnotí a vrátí její výsledek.</span><span class="sxs-lookup"><span data-stu-id="8e4a4-105">The null-coalescing operator `??` returns the value of its left-hand operand if it isn't `null`; otherwise, it evaluates the right-hand operand and returns its result.</span></span> <span data-ttu-id="8e4a4-106">`??` Operátor nevyhodnocuje jeho zpracovával pravý operand, pokud levý operand je vyhodnocen jako nenulové.</span><span class="sxs-lookup"><span data-stu-id="8e4a4-106">The `??` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

<span data-ttu-id="8e4a4-107">Operátoru nulového sjednocení je asociativní zprava, to znamená, výraz ve tvaru</span><span class="sxs-lookup"><span data-stu-id="8e4a4-107">The null-coalescing operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ?? b ?? c
```

<span data-ttu-id="8e4a4-108">je vyhodnocen jako</span><span class="sxs-lookup"><span data-stu-id="8e4a4-108">is evaluated as</span></span>

```csharp
a ?? (b ?? c)
```

<span data-ttu-id="8e4a4-109">`??` Operátor může být užitečné v následujících scénářích:</span><span class="sxs-lookup"><span data-stu-id="8e4a4-109">The `??` operator can be useful in the following scenarios:</span></span>

- <span data-ttu-id="8e4a4-110">Ve výrazech s [podmíněné operátory s null?. a ?[]](member-access-operators.md#null-conditional-operators--and-), můžete poskytnout alternativní výraz k vyhodnocení v případě, že je výsledek výrazu s operacemi null podmíněného operátoru nulového sjednocení `null`:</span><span class="sxs-lookup"><span data-stu-id="8e4a4-110">In expressions with the [null-conditional operators ?. and ?[]](member-access-operators.md#null-conditional-operators--and-), you can use the null-coalescing operator to provide an alternative expression to evaluate in case the result of the expression with null-conditional operations is `null`:</span></span>

  [!code-csharp-interactive[with null-conditional](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullConditional)]

- <span data-ttu-id="8e4a4-111">Při práci s [typy s možnou hodnotou](../../programming-guide/nullable-types/index.md) a je nutné zadat hodnotu podkladového typu hodnoty, zadejte hodnotu zadejte v případě, že je hodnota s možnou hodnotou Null typu pomocí operátoru nulového sjednocení `null`:</span><span class="sxs-lookup"><span data-stu-id="8e4a4-111">When you work with [nullable value types](../../programming-guide/nullable-types/index.md) and need to provide a value of an underlying value type, use the null-coalescing operator to specify the value to provide in case a nullable type value is `null`:</span></span>

  [!code-csharp-interactive[with nullable types](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullableTypes)]

  <span data-ttu-id="8e4a4-112">Použití <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> metoda Pokud hodnota, která má použít, pokud je hodnota s možnou hodnotou Null typu `null` musí mít výchozí hodnotu podkladového typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="8e4a4-112">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a nullable type value is `null` should be the default value of the underlying value type.</span></span>

- <span data-ttu-id="8e4a4-113">Počínaje C# 7.0, můžete použít [ `throw` výraz](../keywords/throw.md#the-throw-expression) jako operand pravé strany operátoru nulového sjednocení, aby byl kód kontroluje argument stručnější:</span><span class="sxs-lookup"><span data-stu-id="8e4a4-113">Starting with C# 7.0, you can use a [`throw` expression](../keywords/throw.md#the-throw-expression) as the right-hand operand of the null-coalescing operator to make the argument-checking code more concise:</span></span>

  [!code-csharp[with throw expression](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithThrowExpression)]

  <span data-ttu-id="8e4a4-114">V předchozím příkladu také ukazuje, jak používat [členové tvoření](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) definovat vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8e4a4-114">The preceding example also demonstrates how to use [expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) to define a property.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="8e4a4-115">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="8e4a4-115">Operator overloadability</span></span>

<span data-ttu-id="8e4a4-116">Operátoru nulového sjednocení nemohou být přetíženy.</span><span class="sxs-lookup"><span data-stu-id="8e4a4-116">The null-coalescing operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8e4a4-117">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8e4a4-117">C# language specification</span></span>

<span data-ttu-id="8e4a4-118">Další informace najdete v tématu [null operátor sloučení](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="8e4a4-118">For more information, see [The null coalescing operator](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8e4a4-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8e4a4-119">See also</span></span>

- [<span data-ttu-id="8e4a4-120">C#referenční dokumentace</span><span class="sxs-lookup"><span data-stu-id="8e4a4-120">C# reference</span></span>](../index.md)
- [<span data-ttu-id="8e4a4-121">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8e4a4-121">C# operators</span></span>](index.md)
- <span data-ttu-id="8e4a4-122">[?. a ?[] operátory](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="8e4a4-122">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="8e4a4-123">?: – operátor</span><span class="sxs-lookup"><span data-stu-id="8e4a4-123">?: operator</span></span>](conditional-operator.md)
