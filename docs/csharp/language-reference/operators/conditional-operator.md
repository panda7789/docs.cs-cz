---
description: '?: operator-reference jazyka C#'
title: '?: operator-reference jazyka C#'
ms.date: 03/06/2020
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 0efa6de2b537fd3af76807938ac2b50a2716561f
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89122352"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="61012-103">?: – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="61012-103">?: operator (C# reference)</span></span>

<span data-ttu-id="61012-104">Podmíněný operátor `?:` , označovaný také jako Ternární podmíněný operátor, vyhodnocuje logický výraz a vrátí výsledek jednoho ze dvou výrazů, v závislosti na tom, zda je logický výraz vyhodnocen jako `true` nebo `false` .</span><span class="sxs-lookup"><span data-stu-id="61012-104">The conditional operator `?:`, also known as the ternary conditional operator, evaluates a Boolean expression and returns the result of one of the two expressions, depending on whether the Boolean expression evaluates to `true` or `false`.</span></span>

<span data-ttu-id="61012-105">Syntaxe podmíněného operátoru je následující:</span><span class="sxs-lookup"><span data-stu-id="61012-105">The syntax for the conditional operator is as follows:</span></span>

```csharp
condition ? consequent : alternative
```

<span data-ttu-id="61012-106">`condition`Výraz musí být vyhodnocen jako `true` nebo `false` .</span><span class="sxs-lookup"><span data-stu-id="61012-106">The `condition` expression must evaluate to `true` or `false`.</span></span> <span data-ttu-id="61012-107">Pokud se `condition` vyhodnotí jako `true` , `consequent` vyhodnotí se výraz a jeho výsledek se projeví v důsledku operace.</span><span class="sxs-lookup"><span data-stu-id="61012-107">If `condition` evaluates to `true`, the `consequent` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="61012-108">Pokud se `condition` vyhodnotí jako `false` , `alternative` vyhodnotí se výraz a jeho výsledek se projeví v důsledku operace.</span><span class="sxs-lookup"><span data-stu-id="61012-108">If `condition` evaluates to `false`, the `alternative` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="61012-109">`consequent` `alternative` Je vyhodnocena pouze nebo.</span><span class="sxs-lookup"><span data-stu-id="61012-109">Only `consequent` or `alternative` is evaluated.</span></span>

<span data-ttu-id="61012-110">Typ `consequent` a `alternative` musí být stejný, nebo musí být implicitní převod z jednoho typu na druhý.</span><span class="sxs-lookup"><span data-stu-id="61012-110">The type of `consequent` and `alternative` must be the same, or there must be an implicit conversion from one type to the other.</span></span>

<span data-ttu-id="61012-111">Podmíněný operátor je asociativní zprava, to znamená výraz formuláře.</span><span class="sxs-lookup"><span data-stu-id="61012-111">The conditional operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ? b : c ? d : e
```

<span data-ttu-id="61012-112">je vyhodnocen jako</span><span class="sxs-lookup"><span data-stu-id="61012-112">is evaluated as</span></span>

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> <span data-ttu-id="61012-113">K zapamatování, jak podmíněný operátor je vyhodnoceno, můžete použít následující symbolické zařízení:</span><span class="sxs-lookup"><span data-stu-id="61012-113">You can use the following mnemonic device to remember how the conditional operator is evaluated:</span></span>
>
> ```text
> is this condition true ? yes : no
> ```

<span data-ttu-id="61012-114">Následující příklad ukazuje použití podmíněného operátoru:</span><span class="sxs-lookup"><span data-stu-id="61012-114">The following example demonstrates the usage of the conditional operator:</span></span>

[!code-csharp-interactive[non ref conditional](snippets/shared/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a><span data-ttu-id="61012-115">Podmíněný výraz ref</span><span class="sxs-lookup"><span data-stu-id="61012-115">Conditional ref expression</span></span>

<span data-ttu-id="61012-116">Počínaje jazykem C# 7,2 lze místně přiřadit místní proměnnou ref nebo [ref pouze pro](../keywords/ref.md#ref-readonly-locals) [místní](../keywords/ref.md#ref-locals) proměnnou s podmíněným výrazem ref.</span><span class="sxs-lookup"><span data-stu-id="61012-116">Beginning with C# 7.2, a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable can be assigned conditionally with the conditional ref expression.</span></span> <span data-ttu-id="61012-117">Podmíněný výraz ref můžete použít také jako [návratovou hodnotu odkazu](../keywords/ref.md#reference-return-values) nebo jako [ `ref` argument metody](../keywords/ref.md#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="61012-117">You can also use the conditional ref expression as a [reference return value](../keywords/ref.md#reference-return-values) or as a [`ref` method argument](../keywords/ref.md#passing-an-argument-by-reference).</span></span>

<span data-ttu-id="61012-118">Syntaxe pro podmíněný výraz ref je následující:</span><span class="sxs-lookup"><span data-stu-id="61012-118">The syntax for the conditional ref expression is as follows:</span></span>

```csharp
condition ? ref consequent : ref alternative
```

<span data-ttu-id="61012-119">Podobně jako původní podmíněný operátor, podmíněný výraz ref vyhodnocuje pouze jeden ze dvou výrazů: `consequent` nebo `alternative` .</span><span class="sxs-lookup"><span data-stu-id="61012-119">Like the original conditional operator, the conditional ref expression evaluates only one of the two expressions: either `consequent` or `alternative`.</span></span>

<span data-ttu-id="61012-120">V případě podmíněného výrazu ref `consequent` `alternative` musí být typ a.</span><span class="sxs-lookup"><span data-stu-id="61012-120">In the case of the conditional ref expression, the type of `consequent` and `alternative` must be the same.</span></span>

<span data-ttu-id="61012-121">Následující příklad ukazuje použití podmíněného ref výrazu:</span><span class="sxs-lookup"><span data-stu-id="61012-121">The following example demonstrates the usage of the conditional ref expression:</span></span>

[!code-csharp-interactive[conditional ref](snippets/shared/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a><span data-ttu-id="61012-122">Podmíněný operátor a `if..else` příkaz</span><span class="sxs-lookup"><span data-stu-id="61012-122">Conditional operator and an `if..else` statement</span></span>

<span data-ttu-id="61012-123">Použití podmíněného operátoru namísto příkazu [if-else](../keywords/if-else.md) může mít za následek výstižnější kód v případech, kdy budete potřebovat podmíněně k výpočtu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="61012-123">Use of the conditional operator instead of an [if-else](../keywords/if-else.md) statement might result in more concise code in cases when you need conditionally to compute a value.</span></span> <span data-ttu-id="61012-124">Následující příklad ukazuje dva způsoby, jak klasifikovat celé číslo jako záporné nebo nezáporné:</span><span class="sxs-lookup"><span data-stu-id="61012-124">The following example demonstrates two ways to classify an integer as negative or nonnegative:</span></span>

[!code-csharp[conditional and if-else](snippets/shared/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a><span data-ttu-id="61012-125">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="61012-125">Operator overloadability</span></span>

<span data-ttu-id="61012-126">Uživatelsky definovaný typ nemůže přetížit podmíněný operátor.</span><span class="sxs-lookup"><span data-stu-id="61012-126">A user-defined type cannot overload the conditional operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="61012-127">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="61012-127">C# language specification</span></span>

<span data-ttu-id="61012-128">Další informace naleznete v části [podmíněný operátor](~/_csharplang/spec/expressions.md#conditional-operator) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="61012-128">For more information, see the [Conditional operator](~/_csharplang/spec/expressions.md#conditional-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="61012-129">Další informace o podmíněném výrazu ref najdete v [poznámce k návrhu funkcí](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).</span><span class="sxs-lookup"><span data-stu-id="61012-129">For more information about the conditional ref expression, see the [feature proposal note](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="61012-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="61012-130">See also</span></span>

- [<span data-ttu-id="61012-131">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="61012-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="61012-132">Operátory a výrazy v C#</span><span class="sxs-lookup"><span data-stu-id="61012-132">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="61012-133">if-else – příkaz</span><span class="sxs-lookup"><span data-stu-id="61012-133">if-else statement</span></span>](../keywords/if-else.md)
- <span data-ttu-id="61012-134">[?. ani? [] – operátory](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="61012-134">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="61012-135">?? a?? = – operátory</span><span class="sxs-lookup"><span data-stu-id="61012-135">?? and ??= operators</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="61012-136">ref – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="61012-136">ref keyword</span></span>](../keywords/ref.md)
