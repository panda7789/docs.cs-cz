---
title: ?? a?? = operátory – C# referenční informace
ms.custom: seodec18
ms.date: 09/10/2019
f1_keywords:
- ??_CSharpKeyword
- ??=_CSharpKeyword
helpviewer_keywords:
- null-coalescing operator [C#]
- ?? operator [C#]
- null-coalescing assignment [C#]
- ??= operator [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: 1e94038a41a6a6cc19be6c67bff2891397793fb3
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70924685"
---
# <a name="-and--operators-c-reference"></a><span data-ttu-id="1815f-103">??</span><span class="sxs-lookup"><span data-stu-id="1815f-103">??</span></span> <span data-ttu-id="1815f-104">a?? = – operátoryC# (Reference)</span><span class="sxs-lookup"><span data-stu-id="1815f-104">and ??= operators (C# reference)</span></span>

<span data-ttu-id="1815f-105">Operátor `??` pro sjednocení hodnoty null vrátí hodnotu jeho levého operandu, pokud není `null`. v opačném případě vyhodnotí operand na pravé straně a vrátí výsledek.</span><span class="sxs-lookup"><span data-stu-id="1815f-105">The null-coalescing operator `??` returns the value of its left-hand operand if it isn't `null`; otherwise, it evaluates the right-hand operand and returns its result.</span></span> <span data-ttu-id="1815f-106">`??` Operátor nevyhodnotí svůj pravý operand, pokud je levý operand vyhodnocen jako jiný než null.</span><span class="sxs-lookup"><span data-stu-id="1815f-106">The `??` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

<span data-ttu-id="1815f-107">K dispozici v C# 8,0 a novějším operátor `??=` přiřazení s hodnotou null přiřadí hodnotu jeho pravého operandu k jeho levému operandu pouze v případě, že je `null`operand na levé straně vyhodnocen.</span><span class="sxs-lookup"><span data-stu-id="1815f-107">Available in C# 8.0 and later, the null-coalescing assignment operator `??=` assigns the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span> <span data-ttu-id="1815f-108">`??=` Operátor nevyhodnotí svůj pravý operand, pokud je levý operand vyhodnocen jako jiný než null.</span><span class="sxs-lookup"><span data-stu-id="1815f-108">The `??=` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

[!code-csharp[null-coalescing assignment](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#Assignment)]

<span data-ttu-id="1815f-109">Levý operand `??=` operátoru musí být proměnná, [vlastnost](../../programming-guide/classes-and-structs/properties.md)nebo element [indexeru](../../programming-guide/indexers/index.md) .</span><span class="sxs-lookup"><span data-stu-id="1815f-109">The left-hand operand of the `??=` operator must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element.</span></span> <span data-ttu-id="1815f-110">Další informace o přiřazení pro slučování s hodnotou null najdete v [poznámce k návrhu funkcí](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).</span><span class="sxs-lookup"><span data-stu-id="1815f-110">For more information about null-coalescing assignment, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).</span></span>

<span data-ttu-id="1815f-111">V C# 7,3 a starších verzích musí být typ levého operandu `??` operátoru buď odkazový typ, nebo [typ hodnoty s možnou hodnotou null](../../programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="1815f-111">In C# 7.3 and earlier, the type of the left-hand operand of the `??` operator must be either a reference type or a [nullable value type](../../programming-guide/nullable-types/index.md).</span></span> <span data-ttu-id="1815f-112">Počínaje C# 8,0 je tento požadavek nahrazen následujícím: typ levého operandu `??` operátorů a `??=` nemůže být typ hodnoty, která není null.</span><span class="sxs-lookup"><span data-stu-id="1815f-112">Beginning with C# 8.0, that requirement is replaced with the following: the type of the left-hand operand of the `??` and `??=` operators cannot be a non-nullable value type.</span></span> <span data-ttu-id="1815f-113">Konkrétně můžete použít operátory slučování s hodnotou null s neomezenými parametry typu v C# 8,0 a novějším:</span><span class="sxs-lookup"><span data-stu-id="1815f-113">In particular, you can use the null-coalescing operators with unconstrained type parameters in C# 8.0 and later:</span></span>

[!code-csharp[unconstrained type parameter](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#UnconstrainedType)]

<span data-ttu-id="1815f-114">Operátory slučování s hodnotou null jsou asociativní zprava.</span><span class="sxs-lookup"><span data-stu-id="1815f-114">The null-coalescing operators are right-associative.</span></span> <span data-ttu-id="1815f-115">To znamená, že výrazy ve formuláři</span><span class="sxs-lookup"><span data-stu-id="1815f-115">That is, expressions of the form</span></span>

```csharp
a ?? b ?? c
d ??= e ??= f
```

<span data-ttu-id="1815f-116">se vyhodnotí jako</span><span class="sxs-lookup"><span data-stu-id="1815f-116">are evaluated as</span></span>

```csharp
a ?? (b ?? c)
d ??= (e ??= f)
```

## <a name="examples"></a><span data-ttu-id="1815f-117">Příklady</span><span class="sxs-lookup"><span data-stu-id="1815f-117">Examples</span></span>

<span data-ttu-id="1815f-118">Operátory `??` a`??=` můžou být užitečné v následujících scénářích:</span><span class="sxs-lookup"><span data-stu-id="1815f-118">The `??` and `??=` operators can be useful in the following scenarios:</span></span>

- <span data-ttu-id="1815f-119">Ve výrazech s [podmíněné operátory s null?. a ?[]](member-access-operators.md#null-conditional-operators--and-), můžete poskytnout alternativní výraz k vyhodnocení v případě, že je výsledek výrazu s operacemi null podmíněného operátoru nulového sjednocení `null`:</span><span class="sxs-lookup"><span data-stu-id="1815f-119">In expressions with the [null-conditional operators ?. and ?[]](member-access-operators.md#null-conditional-operators--and-), you can use the null-coalescing operator to provide an alternative expression to evaluate in case the result of the expression with null-conditional operations is `null`:</span></span>

  [!code-csharp-interactive[with null-conditional](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullConditional)]

- <span data-ttu-id="1815f-120">Když pracujete s [typy hodnot s možnou hodnotou null](../../programming-guide/nullable-types/index.md) a potřebujete zadat hodnotu základního typu hodnoty, použijte operátor pro sjednocení null k určení hodnoty, která se má zadat pro případ, že hodnota `null`typu s možnou hodnotou null je:</span><span class="sxs-lookup"><span data-stu-id="1815f-120">When you work with [nullable value types](../../programming-guide/nullable-types/index.md) and need to provide a value of an underlying value type, use the null-coalescing operator to specify the value to provide in case a nullable type value is `null`:</span></span>

  [!code-csharp-interactive[with nullable types](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullableTypes)]

  <span data-ttu-id="1815f-121">Použijte metodu <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> , pokud hodnota, která se má použít, když má být `null` hodnota typu s možnou hodnotou null výchozí hodnotou základního typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1815f-121">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a nullable type value is `null` should be the default value of the underlying value type.</span></span>

- <span data-ttu-id="1815f-122">Počínaje C# 7,0 můžete použít [ `throw` výraz](../keywords/throw.md#the-throw-expression) jako pravý operand operátoru pro sjednocení s hodnotou null, aby byl kód pro kontrolu argumentu výstižnější:</span><span class="sxs-lookup"><span data-stu-id="1815f-122">Starting with C# 7.0, you can use a [`throw` expression](../keywords/throw.md#the-throw-expression) as the right-hand operand of the null-coalescing operator to make the argument-checking code more concise:</span></span>

  [!code-csharp[with throw expression](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithThrowExpression)]

  <span data-ttu-id="1815f-123">Předchozí příklad také ukazuje, jak pomocí [členů Expression-těle](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) definovat vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1815f-123">The preceding example also demonstrates how to use [expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) to define a property.</span></span>

- <span data-ttu-id="1815f-124">Počínaje C# 8,0 můžete `??=` operátor použít k nahrazení kódu formuláře.</span><span class="sxs-lookup"><span data-stu-id="1815f-124">Starting with C# 8.0, you can use the `??=` operator to replace the code of the form</span></span>

  ```csharp
  if (variable is null)
  {
      variable = expression;
  }
  ```

  <span data-ttu-id="1815f-125">s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="1815f-125">with the following code:</span></span>

  ```csharp
  variable ??= expression;
  ```

## <a name="operator-overloadability"></a><span data-ttu-id="1815f-126">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="1815f-126">Operator overloadability</span></span>

<span data-ttu-id="1815f-127">Operátory `??` a`??=` nemohou být přetíženy.</span><span class="sxs-lookup"><span data-stu-id="1815f-127">The operators `??` and `??=` cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1815f-128">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1815f-128">C# language specification</span></span>

<span data-ttu-id="1815f-129">Další informace o `??` operátoru naleznete v části [operátor slučování null](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="1815f-129">For more information about the `??` operator, see [The null coalescing operator](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1815f-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1815f-130">See also</span></span>

- [<span data-ttu-id="1815f-131">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="1815f-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="1815f-132">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1815f-132">C# operators</span></span>](index.md)
- <span data-ttu-id="1815f-133">[?. a ?[] operátory](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="1815f-133">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="1815f-134">?: – operátor</span><span class="sxs-lookup"><span data-stu-id="1815f-134">?: operator</span></span>](conditional-operator.md)
