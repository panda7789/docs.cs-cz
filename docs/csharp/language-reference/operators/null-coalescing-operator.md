---
title: ?? a?? = operátory – C# referenční informace
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
ms.openlocfilehash: b3d56c6c08443d344002b8e780a72fc547c316bb
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712647"
---
# <a name="-and--operators-c-reference"></a><span data-ttu-id="64727-103">??</span><span class="sxs-lookup"><span data-stu-id="64727-103">??</span></span> <span data-ttu-id="64727-104">a?? = – operátoryC# (Reference)</span><span class="sxs-lookup"><span data-stu-id="64727-104">and ??= operators (C# reference)</span></span>

<span data-ttu-id="64727-105">Operátor slučování null `??` vrátí hodnotu jeho levého operandu, pokud není `null`; v opačném případě vyhodnotí operand na pravé straně a vrátí jeho výsledek.</span><span class="sxs-lookup"><span data-stu-id="64727-105">The null-coalescing operator `??` returns the value of its left-hand operand if it isn't `null`; otherwise, it evaluates the right-hand operand and returns its result.</span></span> <span data-ttu-id="64727-106">Operátor `??` nevyhodnotí svůj operand na pravé straně, pokud je levý operand vyhodnocen jako jiný než null.</span><span class="sxs-lookup"><span data-stu-id="64727-106">The `??` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

<span data-ttu-id="64727-107">K dispozici v 8,0 a novějších operátor přiřazení s nulovou hodnotou `??=` přiřadí hodnotu jeho operandu na levý operand pouze v C# případě, že je operand na levé straně vyhodnocen jako `null`.</span><span class="sxs-lookup"><span data-stu-id="64727-107">Available in C# 8.0 and later, the null-coalescing assignment operator `??=` assigns the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span> <span data-ttu-id="64727-108">Operátor `??=` nevyhodnotí svůj operand na pravé straně, pokud je levý operand vyhodnocen jako jiný než null.</span><span class="sxs-lookup"><span data-stu-id="64727-108">The `??=` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

[!code-csharp[null-coalescing assignment](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#Assignment)]

<span data-ttu-id="64727-109">Levý operand operátoru `??=` musí být proměnná, [vlastnost](../../programming-guide/classes-and-structs/properties.md)nebo element [indexeru](../../programming-guide/indexers/index.md) .</span><span class="sxs-lookup"><span data-stu-id="64727-109">The left-hand operand of the `??=` operator must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element.</span></span>

<span data-ttu-id="64727-110">V C# 7,3 a starších verzích musí být typ levého operandu operátoru `??` buď [odkazový typ](../keywords/reference-types.md) , nebo [typ hodnoty s možnou hodnotou null](../builtin-types/nullable-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="64727-110">In C# 7.3 and earlier, the type of the left-hand operand of the `??` operator must be either a [reference type](../keywords/reference-types.md) or a [nullable value type](../builtin-types/nullable-value-types.md).</span></span> <span data-ttu-id="64727-111">Počínaje C# 8,0 je tento požadavek nahrazen následujícím: typ levého operandu operátorů `??` a `??=` nesmí být typ hodnoty, která není null.</span><span class="sxs-lookup"><span data-stu-id="64727-111">Beginning with C# 8.0, that requirement is replaced with the following: the type of the left-hand operand of the `??` and `??=` operators cannot be a non-nullable value type.</span></span> <span data-ttu-id="64727-112">Konkrétně počínaje C# 8,0 můžete použít operátory slučování s hodnotou null s neomezenými parametry typu:</span><span class="sxs-lookup"><span data-stu-id="64727-112">In particular, beginning with C# 8.0, you can use the null-coalescing operators with unconstrained type parameters:</span></span>

[!code-csharp[unconstrained type parameter](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#UnconstrainedType)]

<span data-ttu-id="64727-113">Operátory slučování s hodnotou null jsou asociativní zprava.</span><span class="sxs-lookup"><span data-stu-id="64727-113">The null-coalescing operators are right-associative.</span></span> <span data-ttu-id="64727-114">To znamená, že výrazy ve formuláři</span><span class="sxs-lookup"><span data-stu-id="64727-114">That is, expressions of the form</span></span>

```csharp
a ?? b ?? c
d ??= e ??= f
```

<span data-ttu-id="64727-115">se vyhodnotí jako</span><span class="sxs-lookup"><span data-stu-id="64727-115">are evaluated as</span></span>

```csharp
a ?? (b ?? c)
d ??= (e ??= f)
```

## <a name="examples"></a><span data-ttu-id="64727-116">Příklady</span><span class="sxs-lookup"><span data-stu-id="64727-116">Examples</span></span>

<span data-ttu-id="64727-117">Operátory `??` a `??=` mohou být užitečné v následujících situacích:</span><span class="sxs-lookup"><span data-stu-id="64727-117">The `??` and `??=` operators can be useful in the following scenarios:</span></span>

- <span data-ttu-id="64727-118">Ve výrazech s [operátory podmíněného příznaku?. a? []](member-access-operators.md#null-conditional-operators--and-)můžete použít operátor `??` k poskytnutí alternativního výrazu pro vyhodnocení pro případ, že je výsledek výrazu s operacemi podmíněného hodnoty null `null`:</span><span class="sxs-lookup"><span data-stu-id="64727-118">In expressions with the [null-conditional operators ?. and ?[]](member-access-operators.md#null-conditional-operators--and-), you can use the `??` operator to provide an alternative expression to evaluate in case the result of the expression with null-conditional operations is `null`:</span></span>

  [!code-csharp-interactive[with null-conditional](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullConditional)]

- <span data-ttu-id="64727-119">Když pracujete s [typy hodnot s možnou hodnotou null](../builtin-types/nullable-value-types.md) a potřebujete zadat hodnotu základního typu hodnoty, použijte operátor `??` k určení hodnoty, která se má zadat pro případ, že hodnota typu s možnou hodnotou null je `null`:</span><span class="sxs-lookup"><span data-stu-id="64727-119">When you work with [nullable value types](../builtin-types/nullable-value-types.md) and need to provide a value of an underlying value type, use the `??` operator to specify the value to provide in case a nullable type value is `null`:</span></span>

  [!code-csharp-interactive[with nullable types](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullableTypes)]

  <span data-ttu-id="64727-120">Metodu <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> použijte v případě, že hodnota, která se má použít, pokud je hodnota typu s možnou hodnotou null `null` by měla být výchozí hodnotou základního typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="64727-120">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a nullable type value is `null` should be the default value of the underlying value type.</span></span>

- <span data-ttu-id="64727-121">Počínaje C# 7,0 můžete použít [výraz`throw`](../keywords/throw.md#the-throw-expression) jako pravý operand operátoru `??`, aby byl kód pro kontrolu argumentu výstižnější:</span><span class="sxs-lookup"><span data-stu-id="64727-121">Beginning with C# 7.0, you can use a [`throw` expression](../keywords/throw.md#the-throw-expression) as the right-hand operand of the `??` operator to make the argument-checking code more concise:</span></span>

  [!code-csharp[with throw expression](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithThrowExpression)]

  <span data-ttu-id="64727-122">Předchozí příklad také ukazuje, jak pomocí [členů Expression-těle](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) definovat vlastnost.</span><span class="sxs-lookup"><span data-stu-id="64727-122">The preceding example also demonstrates how to use [expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) to define a property.</span></span>

- <span data-ttu-id="64727-123">Počínaje C# 8,0 můžete použít operátor `??=` k nahrazení kódu formuláře</span><span class="sxs-lookup"><span data-stu-id="64727-123">Beginning with C# 8.0, you can use the `??=` operator to replace the code of the form</span></span>

  ```csharp
  if (variable is null)
  {
      variable = expression;
  }
  ```

  <span data-ttu-id="64727-124">s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="64727-124">with the following code:</span></span>

  ```csharp
  variable ??= expression;
  ```

## <a name="operator-overloadability"></a><span data-ttu-id="64727-125">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="64727-125">Operator overloadability</span></span>

<span data-ttu-id="64727-126">Operátory `??` a `??=` nelze přečítat.</span><span class="sxs-lookup"><span data-stu-id="64727-126">The operators `??` and `??=` cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="64727-127">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="64727-127">C# language specification</span></span>

<span data-ttu-id="64727-128">Další informace o operátoru `??` naleznete v části [operátor slučování null](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="64727-128">For more information about the `??` operator, see [The null coalescing operator](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="64727-129">Další informace o operátoru `??=` najdete v [poznámce k návrhu funkcí](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).</span><span class="sxs-lookup"><span data-stu-id="64727-129">For more information about the `??=` operator, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="64727-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="64727-130">See also</span></span>

- [<span data-ttu-id="64727-131">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="64727-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="64727-132">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="64727-132">C# operators</span></span>](index.md)
- <span data-ttu-id="64727-133">[?. a ?[] operátory](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="64727-133">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="64727-134">?: – operátor</span><span class="sxs-lookup"><span data-stu-id="64727-134">?: operator</span></span>](conditional-operator.md)
