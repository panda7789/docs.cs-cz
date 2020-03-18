---
title: ?? A?? = operátory - odkaz C#
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
ms.openlocfilehash: 69294f0fb706868b48b8d7fe8b95fa345af169b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847310"
---
# <a name="-and--operators-c-reference"></a><span data-ttu-id="6c436-103">??</span><span class="sxs-lookup"><span data-stu-id="6c436-103">??</span></span> <span data-ttu-id="6c436-104">A?? = operátory (odkaz C#)</span><span class="sxs-lookup"><span data-stu-id="6c436-104">and ??= operators (C# reference)</span></span>

<span data-ttu-id="6c436-105">Null-coalescing operátor `??` vrátí hodnotu jeho levé operand, pokud `null`není ; v opačném případě vyhodnotí pravé operand a vrátí jeho výsledek.</span><span class="sxs-lookup"><span data-stu-id="6c436-105">The null-coalescing operator `??` returns the value of its left-hand operand if it isn't `null`; otherwise, it evaluates the right-hand operand and returns its result.</span></span> <span data-ttu-id="6c436-106">Operátor `??` nevyhodnotí jeho pravé operand, pokud levá operand vyhodnotí na non-null.</span><span class="sxs-lookup"><span data-stu-id="6c436-106">The `??` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

<span data-ttu-id="6c436-107">K dispozici v C# 8.0 a novější, null-coalescing přiřazení operátor `??=` přiřadí hodnotu jeho pravé operand u jeho levé `null`operandpouze v případě, že levé operandu vyhodnotí .</span><span class="sxs-lookup"><span data-stu-id="6c436-107">Available in C# 8.0 and later, the null-coalescing assignment operator `??=` assigns the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span> <span data-ttu-id="6c436-108">Operátor `??=` nevyhodnotí jeho pravé operand, pokud levá operand vyhodnotí na non-null.</span><span class="sxs-lookup"><span data-stu-id="6c436-108">The `??=` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

[!code-csharp[null-coalescing assignment](snippets/NullCoalescingOperator.cs#Assignment)]

<span data-ttu-id="6c436-109">Levá operanda operátoru `??=` musí být proměnná, [vlastnost](../../programming-guide/classes-and-structs/properties.md)nebo [indexerový](../../programming-guide/indexers/index.md) prvek.</span><span class="sxs-lookup"><span data-stu-id="6c436-109">The left-hand operand of the `??=` operator must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element.</span></span>

<span data-ttu-id="6c436-110">V C# 7.3 a starší typ levé operand `??` operátor u operátoru musí být buď [typ odkazu](../keywords/reference-types.md) nebo [typ hodnoty s možnou hodnotou s hodnotou.](../builtin-types/nullable-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="6c436-110">In C# 7.3 and earlier, the type of the left-hand operand of the `??` operator must be either a [reference type](../keywords/reference-types.md) or a [nullable value type](../builtin-types/nullable-value-types.md).</span></span> <span data-ttu-id="6c436-111">Počínaje C# 8.0, tento požadavek je nahrazen následující: typ levé operand `??` `??=` a operátory nemůže být typ hodnoty s nulou.</span><span class="sxs-lookup"><span data-stu-id="6c436-111">Beginning with C# 8.0, that requirement is replaced with the following: the type of the left-hand operand of the `??` and `??=` operators cannot be a non-nullable value type.</span></span> <span data-ttu-id="6c436-112">Zejména počínaje C# 8.0, můžete použít null-coalescing operátory s parametry typu bez omezení:</span><span class="sxs-lookup"><span data-stu-id="6c436-112">In particular, beginning with C# 8.0, you can use the null-coalescing operators with unconstrained type parameters:</span></span>

[!code-csharp[unconstrained type parameter](snippets/NullCoalescingOperator.cs#UnconstrainedType)]

<span data-ttu-id="6c436-113">Null-coalescing operátory jsou právo asociativní.</span><span class="sxs-lookup"><span data-stu-id="6c436-113">The null-coalescing operators are right-associative.</span></span> <span data-ttu-id="6c436-114">To znamená, že výrazy formuláře</span><span class="sxs-lookup"><span data-stu-id="6c436-114">That is, expressions of the form</span></span>

```csharp
a ?? b ?? c
d ??= e ??= f
```

<span data-ttu-id="6c436-115">jsou vyhodnocovány jako</span><span class="sxs-lookup"><span data-stu-id="6c436-115">are evaluated as</span></span>

```csharp
a ?? (b ?? c)
d ??= (e ??= f)
```

## <a name="examples"></a><span data-ttu-id="6c436-116">Příklady</span><span class="sxs-lookup"><span data-stu-id="6c436-116">Examples</span></span>

<span data-ttu-id="6c436-117">A `??` `??=` operátory mohou být užitečné v následujících scénářích:</span><span class="sxs-lookup"><span data-stu-id="6c436-117">The `??` and `??=` operators can be useful in the following scenarios:</span></span>

- <span data-ttu-id="6c436-118">Ve výrazech s [operátory s nulovými podmínkami ?. a ?[]](member-access-operators.md#null-conditional-operators--and-)můžete použít `??` operátor k poskytnutí alternativního výrazu k vyhodnocení v případě, že výsledek výrazu s nulovými podmíněnými operacemi je `null`:</span><span class="sxs-lookup"><span data-stu-id="6c436-118">In expressions with the [null-conditional operators ?. and ?[]](member-access-operators.md#null-conditional-operators--and-), you can use the `??` operator to provide an alternative expression to evaluate in case the result of the expression with null-conditional operations is `null`:</span></span>

  [!code-csharp-interactive[with null-conditional](snippets/NullCoalescingOperator.cs#WithNullConditional)]

- <span data-ttu-id="6c436-119">Při práci s [typy hodnot s možnou hodnotou s hodnotou s možnou hodnotou null](../builtin-types/nullable-value-types.md) a potřebujete zadat hodnotu základního typu hodnoty, použijte `??` operátor k určení hodnoty, která má být poskytnuta v případě, že hodnota typu s možnou hodnotou s možnou hodnotou null je `null`:</span><span class="sxs-lookup"><span data-stu-id="6c436-119">When you work with [nullable value types](../builtin-types/nullable-value-types.md) and need to provide a value of an underlying value type, use the `??` operator to specify the value to provide in case a nullable type value is `null`:</span></span>

  [!code-csharp-interactive[with nullable types](snippets/NullCoalescingOperator.cs#WithNullableTypes)]

  <span data-ttu-id="6c436-120">Metodu <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> použijte, pokud by hodnota, která má `null` být použita, pokud je hodnota typu s hodnotou s možnou hodnotou null, měla být výchozí hodnotou základního typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6c436-120">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a nullable type value is `null` should be the default value of the underlying value type.</span></span>

- <span data-ttu-id="6c436-121">Počínaje C# 7.0, můžete použít [ `throw` výraz](../keywords/throw.md#the-throw-expression) jako pravé operand `??` operátoru, aby kód kontroly argumentů stručnější:</span><span class="sxs-lookup"><span data-stu-id="6c436-121">Beginning with C# 7.0, you can use a [`throw` expression](../keywords/throw.md#the-throw-expression) as the right-hand operand of the `??` operator to make the argument-checking code more concise:</span></span>

  [!code-csharp[with throw expression](snippets/NullCoalescingOperator.cs#WithThrowExpression)]

  <span data-ttu-id="6c436-122">Předchozí příklad také ukazuje, jak používat [členy s výrazem k](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) definování vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6c436-122">The preceding example also demonstrates how to use [expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) to define a property.</span></span>

- <span data-ttu-id="6c436-123">Počínaje c# 8.0, můžete `??=` použít operátor nahradit kód formuláře</span><span class="sxs-lookup"><span data-stu-id="6c436-123">Beginning with C# 8.0, you can use the `??=` operator to replace the code of the form</span></span>

  ```csharp
  if (variable is null)
  {
      variable = expression;
  }
  ```

  <span data-ttu-id="6c436-124">s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="6c436-124">with the following code:</span></span>

  ```csharp
  variable ??= expression;
  ```

## <a name="operator-overloadability"></a><span data-ttu-id="6c436-125">Přetížení obsluhy</span><span class="sxs-lookup"><span data-stu-id="6c436-125">Operator overloadability</span></span>

<span data-ttu-id="6c436-126">Operátory `??` `??=` a nemůže být přetížena.</span><span class="sxs-lookup"><span data-stu-id="6c436-126">The operators `??` and `??=` cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6c436-127">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6c436-127">C# language specification</span></span>

<span data-ttu-id="6c436-128">Další informace o `??` operátoru naleznete v [části null coalescing operator](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) specifikace jazyka [C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="6c436-128">For more information about the `??` operator, see [The null coalescing operator](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="6c436-129">Další informace o `??=` operátorovi naleznete v [poznámce k návrhu funkce](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).</span><span class="sxs-lookup"><span data-stu-id="6c436-129">For more information about the `??=` operator, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6c436-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="6c436-130">See also</span></span>

- [<span data-ttu-id="6c436-131">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="6c436-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="6c436-132">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6c436-132">C# operators</span></span>](index.md)
- <span data-ttu-id="6c436-133">[?. A? [] operátory](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="6c436-133">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="6c436-134">?: operátor</span><span class="sxs-lookup"><span data-stu-id="6c436-134">?: operator</span></span>](conditional-operator.md)
