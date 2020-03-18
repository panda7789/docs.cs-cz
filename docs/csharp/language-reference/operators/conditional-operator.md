---
title: '?: operátor - c# odkaz'
ms.date: 03/06/2020
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 1a17ba092d4228ba909c8774a2f7e15c2c50cfdc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399516"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="d2b05-102">?: operátor (odkaz C#)</span><span class="sxs-lookup"><span data-stu-id="d2b05-102">?: operator (C# reference)</span></span>

<span data-ttu-id="d2b05-103">Podmíněný operátor `?:`, označovaný také jako ternární podmíněný operátor, vyhodnotí logický výraz a vrátí výsledek jednoho ze dvou `true` výrazů v závislosti na tom, zda je logický výraz vyhodnocen nebo . `false`</span><span class="sxs-lookup"><span data-stu-id="d2b05-103">The conditional operator `?:`, also known as the ternary conditional operator, evaluates a Boolean expression and returns the result of one of the two expressions, depending on whether the Boolean expression evaluates to `true` or `false`.</span></span>

<span data-ttu-id="d2b05-104">Syntaxe podmíněného operátoru je následující:</span><span class="sxs-lookup"><span data-stu-id="d2b05-104">The syntax for the conditional operator is as follows:</span></span>

```csharp
condition ? consequent : alternative
```

<span data-ttu-id="d2b05-105">Výraz `condition` musí vyhodnotit `false`nebo `true` .</span><span class="sxs-lookup"><span data-stu-id="d2b05-105">The `condition` expression must evaluate to `true` or `false`.</span></span> <span data-ttu-id="d2b05-106">Pokud `condition` je `true`vyhodnocen a výraz `consequent` je vyhodnocen a jeho výsledek se stane výsledkem operace.</span><span class="sxs-lookup"><span data-stu-id="d2b05-106">If `condition` evaluates to `true`, the `consequent` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="d2b05-107">Pokud `condition` je `false`vyhodnocen a výraz `alternative` je vyhodnocen a jeho výsledek se stane výsledkem operace.</span><span class="sxs-lookup"><span data-stu-id="d2b05-107">If `condition` evaluates to `false`, the `alternative` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="d2b05-108">Pouze `consequent` `alternative` nebo je vyhodnocováno.</span><span class="sxs-lookup"><span data-stu-id="d2b05-108">Only `consequent` or `alternative` is evaluated.</span></span>

<span data-ttu-id="d2b05-109">Typ `consequent` a `alternative` musí být stejný nebo musí být implicitní převod z jednoho typu na druhý.</span><span class="sxs-lookup"><span data-stu-id="d2b05-109">The type of `consequent` and `alternative` must be the same, or there must be an implicit conversion from one type to the other.</span></span>

<span data-ttu-id="d2b05-110">Podmíněný operátor je právo-asociativní, to znamená výraz formuláře</span><span class="sxs-lookup"><span data-stu-id="d2b05-110">The conditional operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ? b : c ? d : e
```

<span data-ttu-id="d2b05-111">je vyhodnocována jako</span><span class="sxs-lookup"><span data-stu-id="d2b05-111">is evaluated as</span></span>

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> <span data-ttu-id="d2b05-112">Pomocí následujícího mnemotechnického zařízení si můžete zapamatovat, jak je podmíněný operátor vyhodnocován:</span><span class="sxs-lookup"><span data-stu-id="d2b05-112">You can use the following mnemonic device to remember how the conditional operator is evaluated:</span></span>
>
> ```text
> is this condition true ? yes : no
> ```

<span data-ttu-id="d2b05-113">Následující příklad ukazuje použití podmíněného operátoru:</span><span class="sxs-lookup"><span data-stu-id="d2b05-113">The following example demonstrates the usage of the conditional operator:</span></span>

[!code-csharp-interactive[non ref conditional](snippets/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a><span data-ttu-id="d2b05-114">Podmíněný výraz ref</span><span class="sxs-lookup"><span data-stu-id="d2b05-114">Conditional ref expression</span></span>

<span data-ttu-id="d2b05-115">Počínaje C# 7.2, [ref místní](../keywords/ref.md#ref-locals) nebo ref pouze pro čtení [místní](../keywords/ref.md#ref-readonly-locals) proměnné lze přiřadit podmíněně s podmíněným ref výraz.</span><span class="sxs-lookup"><span data-stu-id="d2b05-115">Beginning with C# 7.2, a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable can be assigned conditionally with the conditional ref expression.</span></span> <span data-ttu-id="d2b05-116">Podmíněný výraz ref můžete také použít jako [referenční vrácenou hodnotu](../keywords/ref.md#reference-return-values) nebo jako [ `ref` argument metody](../keywords/ref.md#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="d2b05-116">You can also use the conditional ref expression as a [reference return value](../keywords/ref.md#reference-return-values) or as a [`ref` method argument](../keywords/ref.md#passing-an-argument-by-reference).</span></span>

<span data-ttu-id="d2b05-117">Syntaxe podmíněného výrazu ref je následující:</span><span class="sxs-lookup"><span data-stu-id="d2b05-117">The syntax for the conditional ref expression is as follows:</span></span>

```csharp
condition ? ref consequent : ref alternative
```

<span data-ttu-id="d2b05-118">Stejně jako původní podmíněný operátor vyhodnotí podmíněný ref výraz `consequent` pouze `alternative`jeden ze dvou výrazů: nebo .</span><span class="sxs-lookup"><span data-stu-id="d2b05-118">Like the original conditional operator, the conditional ref expression evaluates only one of the two expressions: either `consequent` or `alternative`.</span></span>

<span data-ttu-id="d2b05-119">V případě podmíněného ref výrazu `consequent` musí `alternative` být stejný typ a musí být stejný.</span><span class="sxs-lookup"><span data-stu-id="d2b05-119">In the case of the conditional ref expression, the type of `consequent` and `alternative` must be the same.</span></span>

<span data-ttu-id="d2b05-120">Následující příklad ukazuje použití podmíněného výrazu ref:</span><span class="sxs-lookup"><span data-stu-id="d2b05-120">The following example demonstrates the usage of the conditional ref expression:</span></span>

[!code-csharp-interactive[conditional ref](snippets/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a><span data-ttu-id="d2b05-121">Podmíněný operátor `if..else` a příkaz</span><span class="sxs-lookup"><span data-stu-id="d2b05-121">Conditional operator and an `if..else` statement</span></span>

<span data-ttu-id="d2b05-122">Použití podmíněného operátoru namísto příkazu [if-else](../keywords/if-else.md) může mít za následek stručnější kód v případech, kdy potřebujete podmíněně vypočítat hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d2b05-122">Use of the conditional operator instead of an [if-else](../keywords/if-else.md) statement might result in more concise code in cases when you need conditionally to compute a value.</span></span> <span data-ttu-id="d2b05-123">Následující příklad ukazuje dva způsoby klasifikace celé číslo jako negativní nebo nenegativní:</span><span class="sxs-lookup"><span data-stu-id="d2b05-123">The following example demonstrates two ways to classify an integer as negative or nonnegative:</span></span>

[!code-csharp[conditional and if-else](snippets/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a><span data-ttu-id="d2b05-124">Přetížení obsluhy</span><span class="sxs-lookup"><span data-stu-id="d2b05-124">Operator overloadability</span></span>

<span data-ttu-id="d2b05-125">Uživatelem definovaný typ nemůže přetížit podmíněný operátor.</span><span class="sxs-lookup"><span data-stu-id="d2b05-125">A user-defined type cannot overload the conditional operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d2b05-126">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d2b05-126">C# language specification</span></span>

<span data-ttu-id="d2b05-127">Další informace naleznete v části [Podmíněný operátor](~/_csharplang/spec/expressions.md#conditional-operator) specifikace [jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="d2b05-127">For more information, see the [Conditional operator](~/_csharplang/spec/expressions.md#conditional-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="d2b05-128">Další informace o podmíněném výrazu ref naleznete v [poznámce k návrhu funkce](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).</span><span class="sxs-lookup"><span data-stu-id="d2b05-128">For more information about the conditional ref expression, see the [feature proposal note](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d2b05-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="d2b05-129">See also</span></span>

- [<span data-ttu-id="d2b05-130">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="d2b05-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d2b05-131">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d2b05-131">C# operators</span></span>](index.md)
- [<span data-ttu-id="d2b05-132">if-else prohlášení</span><span class="sxs-lookup"><span data-stu-id="d2b05-132">if-else statement</span></span>](../keywords/if-else.md)
- <span data-ttu-id="d2b05-133">[?. A? [] operátory](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="d2b05-133">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="d2b05-134">?? A?? = operátory</span><span class="sxs-lookup"><span data-stu-id="d2b05-134">?? and ??= operators</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="d2b05-135">klíčové slovo ref</span><span class="sxs-lookup"><span data-stu-id="d2b05-135">ref keyword</span></span>](../keywords/ref.md)
