---
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
ms.openlocfilehash: d3d6a5032a5b4fb7059eb93b0024fd292b74fb70
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555237"
---
# <a name="-and--operators-c-reference"></a><span data-ttu-id="6370a-103">??</span><span class="sxs-lookup"><span data-stu-id="6370a-103">??</span></span> <span data-ttu-id="6370a-104">a?? = – operátory (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="6370a-104">and ??= operators (C# reference)</span></span>

<span data-ttu-id="6370a-105">Operátor pro sjednocení hodnoty null `??` vrátí hodnotu jeho levého operandu, pokud není `null` . v opačném případě vyhodnotí operand na pravé straně a vrátí výsledek.</span><span class="sxs-lookup"><span data-stu-id="6370a-105">The null-coalescing operator `??` returns the value of its left-hand operand if it isn't `null`; otherwise, it evaluates the right-hand operand and returns its result.</span></span> <span data-ttu-id="6370a-106">`??`Operátor nevyhodnotí svůj pravý operand, pokud je levý operand vyhodnocen jako jiný než null.</span><span class="sxs-lookup"><span data-stu-id="6370a-106">The `??` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

<span data-ttu-id="6370a-107">K dispozici v jazyce C# 8,0 a novějším operátor přiřazení s hodnotou null `??=` přiřadí hodnotu jeho pravého operandu k levému operandu pouze v případě, že je operand na levé straně vyhodnocen `null` .</span><span class="sxs-lookup"><span data-stu-id="6370a-107">Available in C# 8.0 and later, the null-coalescing assignment operator `??=` assigns the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span> <span data-ttu-id="6370a-108">`??=`Operátor nevyhodnotí svůj pravý operand, pokud je levý operand vyhodnocen jako jiný než null.</span><span class="sxs-lookup"><span data-stu-id="6370a-108">The `??=` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

[!code-csharp[null-coalescing assignment](snippets/NullCoalescingOperator.cs#Assignment)]

<span data-ttu-id="6370a-109">Levý operand `??=` operátoru musí být proměnná, [vlastnost](../../programming-guide/classes-and-structs/properties.md)nebo element [indexeru](../../programming-guide/indexers/index.md) .</span><span class="sxs-lookup"><span data-stu-id="6370a-109">The left-hand operand of the `??=` operator must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element.</span></span>

<span data-ttu-id="6370a-110">V C# 7,3 a starších verzích musí být typ levého operandu `??` operátoru buď [odkazový typ](../keywords/reference-types.md) , nebo [typ hodnoty s možnou hodnotou null](../builtin-types/nullable-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="6370a-110">In C# 7.3 and earlier, the type of the left-hand operand of the `??` operator must be either a [reference type](../keywords/reference-types.md) or a [nullable value type](../builtin-types/nullable-value-types.md).</span></span> <span data-ttu-id="6370a-111">Počínaje jazykem C# 8,0 je tento požadavek nahrazen následujícím: typ levého operandu `??` `??=` operátorů a nemůže být typ hodnoty, která není null.</span><span class="sxs-lookup"><span data-stu-id="6370a-111">Beginning with C# 8.0, that requirement is replaced with the following: the type of the left-hand operand of the `??` and `??=` operators cannot be a non-nullable value type.</span></span> <span data-ttu-id="6370a-112">Konkrétně počínaje jazykem C# 8,0 můžete použít operátory slučování null s neomezenými parametry typu:</span><span class="sxs-lookup"><span data-stu-id="6370a-112">In particular, beginning with C# 8.0, you can use the null-coalescing operators with unconstrained type parameters:</span></span>

[!code-csharp[unconstrained type parameter](snippets/NullCoalescingOperator.cs#UnconstrainedType)]

<span data-ttu-id="6370a-113">Operátory slučování s hodnotou null jsou asociativní zprava.</span><span class="sxs-lookup"><span data-stu-id="6370a-113">The null-coalescing operators are right-associative.</span></span> <span data-ttu-id="6370a-114">To znamená, že výrazy ve formuláři</span><span class="sxs-lookup"><span data-stu-id="6370a-114">That is, expressions of the form</span></span>

```csharp
a ?? b ?? c
d ??= e ??= f
```

<span data-ttu-id="6370a-115">se vyhodnotí jako</span><span class="sxs-lookup"><span data-stu-id="6370a-115">are evaluated as</span></span>

```csharp
a ?? (b ?? c)
d ??= (e ??= f)
```

## <a name="examples"></a><span data-ttu-id="6370a-116">Příklady</span><span class="sxs-lookup"><span data-stu-id="6370a-116">Examples</span></span>

<span data-ttu-id="6370a-117">`??`Operátory a `??=` můžou být užitečné v následujících scénářích:</span><span class="sxs-lookup"><span data-stu-id="6370a-117">The `??` and `??=` operators can be useful in the following scenarios:</span></span>

- <span data-ttu-id="6370a-118">Ve výrazech s [operátory podmíněné hodnoty null?. a? []](member-access-operators.md#null-conditional-operators--and-)můžete použít `??` operátor k poskytnutí alternativního výrazu pro vyhodnocení pro případ, že výsledek výrazu s hodnotami s hodnotou null je `null` :</span><span class="sxs-lookup"><span data-stu-id="6370a-118">In expressions with the [null-conditional operators ?. and ?[]](member-access-operators.md#null-conditional-operators--and-), you can use the `??` operator to provide an alternative expression to evaluate in case the result of the expression with null-conditional operations is `null`:</span></span>

  [!code-csharp-interactive[with null-conditional](snippets/NullCoalescingOperator.cs#WithNullConditional)]

- <span data-ttu-id="6370a-119">Když pracujete s [typy hodnot s možnou hodnotou null](../builtin-types/nullable-value-types.md) a potřebujete zadat hodnotu základního typu hodnoty, použijte `??` operátor k určení hodnoty, která má být zadána pro případ, že hodnota typu s možnou hodnotou null je `null` :</span><span class="sxs-lookup"><span data-stu-id="6370a-119">When you work with [nullable value types](../builtin-types/nullable-value-types.md) and need to provide a value of an underlying value type, use the `??` operator to specify the value to provide in case a nullable type value is `null`:</span></span>

  [!code-csharp-interactive[with nullable types](snippets/NullCoalescingOperator.cs#WithNullableTypes)]

  <span data-ttu-id="6370a-120">Použijte <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> metodu, pokud hodnota, která se má použít, když má být hodnota typu s možnou hodnotou null `null` výchozí hodnotou základního typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6370a-120">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a nullable type value is `null` should be the default value of the underlying value type.</span></span>

- <span data-ttu-id="6370a-121">Počínaje jazykem C# 7,0 můžete použít [ `throw` výraz](../keywords/throw.md#the-throw-expression) jako pravý operand `??` operátoru k zajištění přesnější kódu pro kontrolu argumentu:</span><span class="sxs-lookup"><span data-stu-id="6370a-121">Beginning with C# 7.0, you can use a [`throw` expression](../keywords/throw.md#the-throw-expression) as the right-hand operand of the `??` operator to make the argument-checking code more concise:</span></span>

  [!code-csharp[with throw expression](snippets/NullCoalescingOperator.cs#WithThrowExpression)]

  <span data-ttu-id="6370a-122">Předchozí příklad také ukazuje, jak pomocí [členů Expression-těle](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) definovat vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6370a-122">The preceding example also demonstrates how to use [expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) to define a property.</span></span>

- <span data-ttu-id="6370a-123">Počínaje jazykem C# 8,0 můžete použít `??=` operátor k nahrazení kódu formuláře</span><span class="sxs-lookup"><span data-stu-id="6370a-123">Beginning with C# 8.0, you can use the `??=` operator to replace the code of the form</span></span>

  ```csharp
  if (variable is null)
  {
      variable = expression;
  }
  ```

  <span data-ttu-id="6370a-124">s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="6370a-124">with the following code:</span></span>

  ```csharp
  variable ??= expression;
  ```

## <a name="operator-overloadability"></a><span data-ttu-id="6370a-125">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="6370a-125">Operator overloadability</span></span>

<span data-ttu-id="6370a-126">Operátory `??` a `??=` nemohou být přetíženy.</span><span class="sxs-lookup"><span data-stu-id="6370a-126">The operators `??` and `??=` cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6370a-127">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6370a-127">C# language specification</span></span>

<span data-ttu-id="6370a-128">Další informace o `??` operátoru naleznete v oddílu " [slučovací operátor null](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) " [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="6370a-128">For more information about the `??` operator, see [The null coalescing operator](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="6370a-129">Další informace o `??=` operátoru najdete v [poznámkách k návrhu funkcí](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).</span><span class="sxs-lookup"><span data-stu-id="6370a-129">For more information about the `??=` operator, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6370a-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="6370a-130">See also</span></span>

- [<span data-ttu-id="6370a-131">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="6370a-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="6370a-132">Operátory a výrazy v C#</span><span class="sxs-lookup"><span data-stu-id="6370a-132">C# operators and expressions</span></span>](index.md)
- <span data-ttu-id="6370a-133">[?. ani? [] – operátory](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="6370a-133">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="6370a-134">?: – operátor</span><span class="sxs-lookup"><span data-stu-id="6370a-134">?: operator</span></span>](conditional-operator.md)
