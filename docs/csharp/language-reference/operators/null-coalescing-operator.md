---
description: ?? a?? = – operátory – Referenční dokumentace jazyka C#
title: ?? a?? = – operátory – Referenční dokumentace jazyka C#
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
ms.openlocfilehash: 273bc6d3a4c65c09dc600621b435bf0d1baea9e4
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118283"
---
# <a name="-and--operators-c-reference"></a><span data-ttu-id="0c794-105">??</span><span class="sxs-lookup"><span data-stu-id="0c794-105">??</span></span> <span data-ttu-id="0c794-106">a?? = – operátory (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="0c794-106">and ??= operators (C# reference)</span></span>

<span data-ttu-id="0c794-107">Operátor pro sjednocení hodnoty null `??` vrátí hodnotu jeho levého operandu, pokud není `null` . v opačném případě vyhodnotí operand na pravé straně a vrátí výsledek.</span><span class="sxs-lookup"><span data-stu-id="0c794-107">The null-coalescing operator `??` returns the value of its left-hand operand if it isn't `null`; otherwise, it evaluates the right-hand operand and returns its result.</span></span> <span data-ttu-id="0c794-108">`??`Operátor nevyhodnotí svůj pravý operand, pokud je levý operand vyhodnocen jako jiný než null.</span><span class="sxs-lookup"><span data-stu-id="0c794-108">The `??` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

<span data-ttu-id="0c794-109">K dispozici v jazyce C# 8,0 a novějším operátor přiřazení s hodnotou null `??=` přiřadí hodnotu jeho pravého operandu k levému operandu pouze v případě, že je operand na levé straně vyhodnocen `null` .</span><span class="sxs-lookup"><span data-stu-id="0c794-109">Available in C# 8.0 and later, the null-coalescing assignment operator `??=` assigns the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span> <span data-ttu-id="0c794-110">`??=`Operátor nevyhodnotí svůj pravý operand, pokud je levý operand vyhodnocen jako jiný než null.</span><span class="sxs-lookup"><span data-stu-id="0c794-110">The `??=` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

[!code-csharp[null-coalescing assignment](snippets/shared/NullCoalescingOperator.cs#Assignment)]

<span data-ttu-id="0c794-111">Levý operand `??=` operátoru musí být proměnná, [vlastnost](../../programming-guide/classes-and-structs/properties.md)nebo element [indexeru](../../programming-guide/indexers/index.md) .</span><span class="sxs-lookup"><span data-stu-id="0c794-111">The left-hand operand of the `??=` operator must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element.</span></span>

<span data-ttu-id="0c794-112">V C# 7,3 a starších verzích musí být typ levého operandu `??` operátoru buď [odkazový typ](../keywords/reference-types.md) , nebo [typ hodnoty s možnou hodnotou null](../builtin-types/nullable-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="0c794-112">In C# 7.3 and earlier, the type of the left-hand operand of the `??` operator must be either a [reference type](../keywords/reference-types.md) or a [nullable value type](../builtin-types/nullable-value-types.md).</span></span> <span data-ttu-id="0c794-113">Počínaje jazykem C# 8,0 je tento požadavek nahrazen následujícím: typ levého operandu `??` `??=` operátorů a nemůže být typ hodnoty, která není null.</span><span class="sxs-lookup"><span data-stu-id="0c794-113">Beginning with C# 8.0, that requirement is replaced with the following: the type of the left-hand operand of the `??` and `??=` operators cannot be a non-nullable value type.</span></span> <span data-ttu-id="0c794-114">Konkrétně počínaje jazykem C# 8,0 můžete použít operátory slučování null s neomezenými parametry typu:</span><span class="sxs-lookup"><span data-stu-id="0c794-114">In particular, beginning with C# 8.0, you can use the null-coalescing operators with unconstrained type parameters:</span></span>

[!code-csharp[unconstrained type parameter](snippets/shared/NullCoalescingOperator.cs#UnconstrainedType)]

<span data-ttu-id="0c794-115">Operátory slučování s hodnotou null jsou asociativní zprava.</span><span class="sxs-lookup"><span data-stu-id="0c794-115">The null-coalescing operators are right-associative.</span></span> <span data-ttu-id="0c794-116">To znamená, že výrazy ve formuláři</span><span class="sxs-lookup"><span data-stu-id="0c794-116">That is, expressions of the form</span></span>

```csharp
a ?? b ?? c
d ??= e ??= f
```

<span data-ttu-id="0c794-117">se vyhodnotí jako</span><span class="sxs-lookup"><span data-stu-id="0c794-117">are evaluated as</span></span>

```csharp
a ?? (b ?? c)
d ??= (e ??= f)
```

## <a name="examples"></a><span data-ttu-id="0c794-118">Příklady</span><span class="sxs-lookup"><span data-stu-id="0c794-118">Examples</span></span>

<span data-ttu-id="0c794-119">`??`Operátory a `??=` můžou být užitečné v následujících scénářích:</span><span class="sxs-lookup"><span data-stu-id="0c794-119">The `??` and `??=` operators can be useful in the following scenarios:</span></span>

- <span data-ttu-id="0c794-120">Ve výrazech s [operátory podmíněné hodnoty null?. a? []](member-access-operators.md#null-conditional-operators--and-)můžete použít `??` operátor k poskytnutí alternativního výrazu pro vyhodnocení pro případ, že výsledek výrazu s hodnotami s hodnotou null je `null` :</span><span class="sxs-lookup"><span data-stu-id="0c794-120">In expressions with the [null-conditional operators ?. and ?[]](member-access-operators.md#null-conditional-operators--and-), you can use the `??` operator to provide an alternative expression to evaluate in case the result of the expression with null-conditional operations is `null`:</span></span>

  [!code-csharp-interactive[with null-conditional](snippets/shared/NullCoalescingOperator.cs#WithNullConditional)]

- <span data-ttu-id="0c794-121">Když pracujete s [typy hodnot s možnou hodnotou null](../builtin-types/nullable-value-types.md) a potřebujete zadat hodnotu základního typu hodnoty, použijte `??` operátor k určení hodnoty, která má být zadána pro případ, že hodnota typu s možnou hodnotou null je `null` :</span><span class="sxs-lookup"><span data-stu-id="0c794-121">When you work with [nullable value types](../builtin-types/nullable-value-types.md) and need to provide a value of an underlying value type, use the `??` operator to specify the value to provide in case a nullable type value is `null`:</span></span>

  [!code-csharp-interactive[with nullable types](snippets/shared/NullCoalescingOperator.cs#WithNullableTypes)]

  <span data-ttu-id="0c794-122">Použijte <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> metodu, pokud hodnota, která se má použít, když má být hodnota typu s možnou hodnotou null `null` výchozí hodnotou základního typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0c794-122">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a nullable type value is `null` should be the default value of the underlying value type.</span></span>

- <span data-ttu-id="0c794-123">Počínaje jazykem C# 7,0 můžete použít [ `throw` výraz](../keywords/throw.md#the-throw-expression) jako pravý operand `??` operátoru k zajištění přesnější kódu pro kontrolu argumentu:</span><span class="sxs-lookup"><span data-stu-id="0c794-123">Beginning with C# 7.0, you can use a [`throw` expression](../keywords/throw.md#the-throw-expression) as the right-hand operand of the `??` operator to make the argument-checking code more concise:</span></span>

  [!code-csharp[with throw expression](snippets/shared/NullCoalescingOperator.cs#WithThrowExpression)]

  <span data-ttu-id="0c794-124">Předchozí příklad také ukazuje, jak pomocí [členů Expression-těle](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) definovat vlastnost.</span><span class="sxs-lookup"><span data-stu-id="0c794-124">The preceding example also demonstrates how to use [expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) to define a property.</span></span>

- <span data-ttu-id="0c794-125">Počínaje jazykem C# 8,0 můžete použít `??=` operátor k nahrazení kódu formuláře</span><span class="sxs-lookup"><span data-stu-id="0c794-125">Beginning with C# 8.0, you can use the `??=` operator to replace the code of the form</span></span>

  ```csharp
  if (variable is null)
  {
      variable = expression;
  }
  ```

  <span data-ttu-id="0c794-126">s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="0c794-126">with the following code:</span></span>

  ```csharp
  variable ??= expression;
  ```

## <a name="operator-overloadability"></a><span data-ttu-id="0c794-127">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="0c794-127">Operator overloadability</span></span>

<span data-ttu-id="0c794-128">Operátory `??` a `??=` nemohou být přetíženy.</span><span class="sxs-lookup"><span data-stu-id="0c794-128">The operators `??` and `??=` cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0c794-129">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0c794-129">C# language specification</span></span>

<span data-ttu-id="0c794-130">Další informace o `??` operátoru naleznete v oddílu " [slučovací operátor null](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) " [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="0c794-130">For more information about the `??` operator, see [The null coalescing operator](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="0c794-131">Další informace o `??=` operátoru najdete v [poznámkách k návrhu funkcí](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).</span><span class="sxs-lookup"><span data-stu-id="0c794-131">For more information about the `??=` operator, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0c794-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="0c794-132">See also</span></span>

- [<span data-ttu-id="0c794-133">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="0c794-133">C# reference</span></span>](../index.md)
- [<span data-ttu-id="0c794-134">Operátory a výrazy v C#</span><span class="sxs-lookup"><span data-stu-id="0c794-134">C# operators and expressions</span></span>](index.md)
- <span data-ttu-id="0c794-135">[?. ani? [] – operátory](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="0c794-135">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="0c794-136">?: – operátor</span><span class="sxs-lookup"><span data-stu-id="0c794-136">?: operator</span></span>](conditional-operator.md)
