---
title: '?: operátor- C# reference'
ms.custom: seodec18
ms.date: 11/20/2018
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 7397c5b2b2278f487a98b029b00924d3151913db
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036292"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="3f7bf-102">?: – operátorC# (Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="3f7bf-102">?: operator (C# reference)</span></span>

<span data-ttu-id="3f7bf-103">Podmíněný operátor `?:`, označovaný také jako Ternární podmíněný operátor, vyhodnotí logický výraz a vrátí výsledek jednoho ze dvou výrazů, v závislosti na tom, zda se logický výraz vyhodnotí jako `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="3f7bf-103">The conditional operator `?:`, also known as the ternary conditional operator, evaluates a Boolean expression and returns the result of one of the two expressions, depending on whether the Boolean expression evaluates to `true` or `false`.</span></span> <span data-ttu-id="3f7bf-104">Počínaje C# 7,2, [podmíněný výraz ref](#conditional-ref-expression) vrátí odkaz na výsledek jednoho ze dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="3f7bf-104">Beginning with C# 7.2, the [conditional ref expression](#conditional-ref-expression) returns the reference to the result of one of the two expressions.</span></span>

<span data-ttu-id="3f7bf-105">Syntaxe podmíněného operátoru je následující:</span><span class="sxs-lookup"><span data-stu-id="3f7bf-105">The syntax for the conditional operator is as follows:</span></span>

```csharp
condition ? consequent : alternative
```

<span data-ttu-id="3f7bf-106">Výraz `condition` musí být vyhodnocen jako `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="3f7bf-106">The `condition` expression must evaluate to `true` or `false`.</span></span> <span data-ttu-id="3f7bf-107">Je-li `condition` vyhodnocen jako `true`, je vyhodnocen výraz `consequent` a jeho výsledek se projeví v důsledku operace.</span><span class="sxs-lookup"><span data-stu-id="3f7bf-107">If `condition` evaluates to `true`, the `consequent` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="3f7bf-108">Je-li `condition` vyhodnocen jako `false`, je vyhodnocen výraz `alternative` a jeho výsledek se projeví v důsledku operace.</span><span class="sxs-lookup"><span data-stu-id="3f7bf-108">If `condition` evaluates to `false`, the `alternative` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="3f7bf-109">Vyhodnotí se jenom `consequent` nebo `alternative`.</span><span class="sxs-lookup"><span data-stu-id="3f7bf-109">Only `consequent` or `alternative` is evaluated.</span></span>

<span data-ttu-id="3f7bf-110">Typ `consequent` a `alternative` musí být stejný, nebo musí být implicitní převod z jednoho typu na druhý.</span><span class="sxs-lookup"><span data-stu-id="3f7bf-110">The type of `consequent` and `alternative` must be the same, or there must be an implicit conversion from one type to the other.</span></span>

<span data-ttu-id="3f7bf-111">Podmíněný operátor je asociativní zprava, to znamená výraz formuláře.</span><span class="sxs-lookup"><span data-stu-id="3f7bf-111">The conditional operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ? b : c ? d : e
```

<span data-ttu-id="3f7bf-112">je vyhodnocen jako</span><span class="sxs-lookup"><span data-stu-id="3f7bf-112">is evaluated as</span></span>

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> <span data-ttu-id="3f7bf-113">K zapamatování, jak podmíněný operátor je vyhodnoceno, můžete použít následující symbolické zařízení:</span><span class="sxs-lookup"><span data-stu-id="3f7bf-113">You can use the following mnemonic device to remember how the conditional operator is evaluated:</span></span>
>
> ```text
> is this condition true ? yes : no
> ```

<span data-ttu-id="3f7bf-114">Následující příklad ukazuje použití podmíněného operátoru:</span><span class="sxs-lookup"><span data-stu-id="3f7bf-114">The following example demonstrates the usage of the conditional operator:</span></span>

[!code-csharp-interactive[non ref conditional](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a><span data-ttu-id="3f7bf-115">Podmíněný výraz ref</span><span class="sxs-lookup"><span data-stu-id="3f7bf-115">Conditional ref expression</span></span>

<span data-ttu-id="3f7bf-116">Počínaje C# 7,2 můžete použít výraz podmíněného odkazu k vrácení odkazu na výsledek jednoho ze dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="3f7bf-116">Beginning with C# 7.2, you can use the conditional ref expression to return the reference to the result of one of the two expressions.</span></span> <span data-ttu-id="3f7bf-117">Tento odkaz můžete přiřadit k místní proměnné [ref](../keywords/ref.md#ref-locals) nebo [ref jen pro čtení](../keywords/ref.md#ref-readonly-locals) nebo použít jako [návratovou hodnotu odkazu](../keywords/ref.md#reference-return-values) nebo jako [parametr metody`ref`](../keywords/ref.md#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="3f7bf-117">You can assign that reference to a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable, or use it as a [reference return value](../keywords/ref.md#reference-return-values) or as a [`ref` method parameter](../keywords/ref.md#passing-an-argument-by-reference).</span></span>

<span data-ttu-id="3f7bf-118">Syntaxe pro podmíněný výraz ref je následující:</span><span class="sxs-lookup"><span data-stu-id="3f7bf-118">The syntax for the conditional ref expression is as follows:</span></span>

```csharp
condition ? ref consequent : ref alternative
```

<span data-ttu-id="3f7bf-119">Podobně jako původní podmíněný operátor, podmíněný výraz ref vyhodnocuje pouze jeden ze dvou výrazů: buď `consequent`, nebo `alternative`.</span><span class="sxs-lookup"><span data-stu-id="3f7bf-119">Like the original conditional operator, the conditional ref expression evaluates only one of the two expressions: either `consequent` or `alternative`.</span></span>

<span data-ttu-id="3f7bf-120">V případě podmíněného výrazu ref musí být typ `consequent` a `alternative` stejný.</span><span class="sxs-lookup"><span data-stu-id="3f7bf-120">In the case of the conditional ref expression, the type of `consequent` and `alternative` must be the same.</span></span>

<span data-ttu-id="3f7bf-121">Následující příklad ukazuje použití podmíněného ref výrazu:</span><span class="sxs-lookup"><span data-stu-id="3f7bf-121">The following example demonstrates the usage of the conditional ref expression:</span></span>

[!code-csharp-interactive[conditional ref](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a><span data-ttu-id="3f7bf-122">Podmíněný operátor a příkaz `if..else`</span><span class="sxs-lookup"><span data-stu-id="3f7bf-122">Conditional operator and an `if..else` statement</span></span>

<span data-ttu-id="3f7bf-123">Použití podmíněného operátoru namísto příkazu [if-else](../keywords/if-else.md) může mít za následek výstižnější kód v případech, kdy budete potřebovat podmíněně k výpočtu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3f7bf-123">Use of the conditional operator instead of an [if-else](../keywords/if-else.md) statement might result in more concise code in cases when you need conditionally to compute a value.</span></span> <span data-ttu-id="3f7bf-124">Následující příklad ukazuje dva způsoby, jak klasifikovat celé číslo jako záporné nebo nezáporné:</span><span class="sxs-lookup"><span data-stu-id="3f7bf-124">The following example demonstrates two ways to classify an integer as negative or nonnegative:</span></span>

[!code-csharp[conditional and if-else](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a><span data-ttu-id="3f7bf-125">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="3f7bf-125">Operator overloadability</span></span>

<span data-ttu-id="3f7bf-126">Uživatelsky definovaný typ nemůže přetížit podmíněný operátor.</span><span class="sxs-lookup"><span data-stu-id="3f7bf-126">A user-defined type cannot overload the conditional operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3f7bf-127">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3f7bf-127">C# language specification</span></span>

<span data-ttu-id="3f7bf-128">Další informace naleznete v části [podmíněný operátor](~/_csharplang/spec/expressions.md#conditional-operator) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="3f7bf-128">For more information, see the [Conditional operator](~/_csharplang/spec/expressions.md#conditional-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="3f7bf-129">Další informace o podmíněném výrazu ref najdete v [poznámce k návrhu funkcí](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).</span><span class="sxs-lookup"><span data-stu-id="3f7bf-129">For more information about the conditional ref expression, see the [feature proposal note](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3f7bf-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3f7bf-130">See also</span></span>

- [<span data-ttu-id="3f7bf-131">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="3f7bf-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="3f7bf-132">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3f7bf-132">C# operators</span></span>](index.md)
- [<span data-ttu-id="3f7bf-133">if-else – příkaz</span><span class="sxs-lookup"><span data-stu-id="3f7bf-133">if-else statement</span></span>](../keywords/if-else.md)
- <span data-ttu-id="3f7bf-134">[?. ani? [] – operátory](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="3f7bf-134">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="3f7bf-135">?? a?? = – operátory</span><span class="sxs-lookup"><span data-stu-id="3f7bf-135">?? and ??= operators</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="3f7bf-136">ref – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="3f7bf-136">ref keyword</span></span>](../keywords/ref.md)
