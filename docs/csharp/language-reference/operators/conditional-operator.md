---
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
ms.openlocfilehash: 8e6753a08bbd96f980b3c5901e763f2dfad055c6
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555354"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="44b5e-102">?: – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="44b5e-102">?: operator (C# reference)</span></span>

<span data-ttu-id="44b5e-103">Podmíněný operátor `?:` , označovaný také jako Ternární podmíněný operátor, vyhodnocuje logický výraz a vrátí výsledek jednoho ze dvou výrazů, v závislosti na tom, zda je logický výraz vyhodnocen jako `true` nebo `false` .</span><span class="sxs-lookup"><span data-stu-id="44b5e-103">The conditional operator `?:`, also known as the ternary conditional operator, evaluates a Boolean expression and returns the result of one of the two expressions, depending on whether the Boolean expression evaluates to `true` or `false`.</span></span>

<span data-ttu-id="44b5e-104">Syntaxe podmíněného operátoru je následující:</span><span class="sxs-lookup"><span data-stu-id="44b5e-104">The syntax for the conditional operator is as follows:</span></span>

```csharp
condition ? consequent : alternative
```

<span data-ttu-id="44b5e-105">`condition`Výraz musí být vyhodnocen jako `true` nebo `false` .</span><span class="sxs-lookup"><span data-stu-id="44b5e-105">The `condition` expression must evaluate to `true` or `false`.</span></span> <span data-ttu-id="44b5e-106">Pokud se `condition` vyhodnotí jako `true` , `consequent` vyhodnotí se výraz a jeho výsledek se projeví v důsledku operace.</span><span class="sxs-lookup"><span data-stu-id="44b5e-106">If `condition` evaluates to `true`, the `consequent` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="44b5e-107">Pokud se `condition` vyhodnotí jako `false` , `alternative` vyhodnotí se výraz a jeho výsledek se projeví v důsledku operace.</span><span class="sxs-lookup"><span data-stu-id="44b5e-107">If `condition` evaluates to `false`, the `alternative` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="44b5e-108">`consequent` `alternative` Je vyhodnocena pouze nebo.</span><span class="sxs-lookup"><span data-stu-id="44b5e-108">Only `consequent` or `alternative` is evaluated.</span></span>

<span data-ttu-id="44b5e-109">Typ `consequent` a `alternative` musí být stejný, nebo musí být implicitní převod z jednoho typu na druhý.</span><span class="sxs-lookup"><span data-stu-id="44b5e-109">The type of `consequent` and `alternative` must be the same, or there must be an implicit conversion from one type to the other.</span></span>

<span data-ttu-id="44b5e-110">Podmíněný operátor je asociativní zprava, to znamená výraz formuláře.</span><span class="sxs-lookup"><span data-stu-id="44b5e-110">The conditional operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ? b : c ? d : e
```

<span data-ttu-id="44b5e-111">je vyhodnocen jako</span><span class="sxs-lookup"><span data-stu-id="44b5e-111">is evaluated as</span></span>

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> <span data-ttu-id="44b5e-112">K zapamatování, jak podmíněný operátor je vyhodnoceno, můžete použít následující symbolické zařízení:</span><span class="sxs-lookup"><span data-stu-id="44b5e-112">You can use the following mnemonic device to remember how the conditional operator is evaluated:</span></span>
>
> ```text
> is this condition true ? yes : no
> ```

<span data-ttu-id="44b5e-113">Následující příklad ukazuje použití podmíněného operátoru:</span><span class="sxs-lookup"><span data-stu-id="44b5e-113">The following example demonstrates the usage of the conditional operator:</span></span>

[!code-csharp-interactive[non ref conditional](snippets/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a><span data-ttu-id="44b5e-114">Podmíněný výraz ref</span><span class="sxs-lookup"><span data-stu-id="44b5e-114">Conditional ref expression</span></span>

<span data-ttu-id="44b5e-115">Počínaje jazykem C# 7,2 lze místně přiřadit místní proměnnou ref nebo [ref pouze pro](../keywords/ref.md#ref-readonly-locals) [místní](../keywords/ref.md#ref-locals) proměnnou s podmíněným výrazem ref.</span><span class="sxs-lookup"><span data-stu-id="44b5e-115">Beginning with C# 7.2, a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable can be assigned conditionally with the conditional ref expression.</span></span> <span data-ttu-id="44b5e-116">Podmíněný výraz ref můžete použít také jako [návratovou hodnotu odkazu](../keywords/ref.md#reference-return-values) nebo jako [ `ref` argument metody](../keywords/ref.md#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="44b5e-116">You can also use the conditional ref expression as a [reference return value](../keywords/ref.md#reference-return-values) or as a [`ref` method argument](../keywords/ref.md#passing-an-argument-by-reference).</span></span>

<span data-ttu-id="44b5e-117">Syntaxe pro podmíněný výraz ref je následující:</span><span class="sxs-lookup"><span data-stu-id="44b5e-117">The syntax for the conditional ref expression is as follows:</span></span>

```csharp
condition ? ref consequent : ref alternative
```

<span data-ttu-id="44b5e-118">Podobně jako původní podmíněný operátor, podmíněný výraz ref vyhodnocuje pouze jeden ze dvou výrazů: `consequent` nebo `alternative` .</span><span class="sxs-lookup"><span data-stu-id="44b5e-118">Like the original conditional operator, the conditional ref expression evaluates only one of the two expressions: either `consequent` or `alternative`.</span></span>

<span data-ttu-id="44b5e-119">V případě podmíněného výrazu ref `consequent` `alternative` musí být typ a.</span><span class="sxs-lookup"><span data-stu-id="44b5e-119">In the case of the conditional ref expression, the type of `consequent` and `alternative` must be the same.</span></span>

<span data-ttu-id="44b5e-120">Následující příklad ukazuje použití podmíněného ref výrazu:</span><span class="sxs-lookup"><span data-stu-id="44b5e-120">The following example demonstrates the usage of the conditional ref expression:</span></span>

[!code-csharp-interactive[conditional ref](snippets/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a><span data-ttu-id="44b5e-121">Podmíněný operátor a `if..else` příkaz</span><span class="sxs-lookup"><span data-stu-id="44b5e-121">Conditional operator and an `if..else` statement</span></span>

<span data-ttu-id="44b5e-122">Použití podmíněného operátoru namísto příkazu [if-else](../keywords/if-else.md) může mít za následek výstižnější kód v případech, kdy budete potřebovat podmíněně k výpočtu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="44b5e-122">Use of the conditional operator instead of an [if-else](../keywords/if-else.md) statement might result in more concise code in cases when you need conditionally to compute a value.</span></span> <span data-ttu-id="44b5e-123">Následující příklad ukazuje dva způsoby, jak klasifikovat celé číslo jako záporné nebo nezáporné:</span><span class="sxs-lookup"><span data-stu-id="44b5e-123">The following example demonstrates two ways to classify an integer as negative or nonnegative:</span></span>

[!code-csharp[conditional and if-else](snippets/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a><span data-ttu-id="44b5e-124">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="44b5e-124">Operator overloadability</span></span>

<span data-ttu-id="44b5e-125">Uživatelsky definovaný typ nemůže přetížit podmíněný operátor.</span><span class="sxs-lookup"><span data-stu-id="44b5e-125">A user-defined type cannot overload the conditional operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="44b5e-126">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="44b5e-126">C# language specification</span></span>

<span data-ttu-id="44b5e-127">Další informace naleznete v části [podmíněný operátor](~/_csharplang/spec/expressions.md#conditional-operator) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="44b5e-127">For more information, see the [Conditional operator](~/_csharplang/spec/expressions.md#conditional-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="44b5e-128">Další informace o podmíněném výrazu ref najdete v [poznámce k návrhu funkcí](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).</span><span class="sxs-lookup"><span data-stu-id="44b5e-128">For more information about the conditional ref expression, see the [feature proposal note](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="44b5e-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="44b5e-129">See also</span></span>

- [<span data-ttu-id="44b5e-130">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="44b5e-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="44b5e-131">Operátory a výrazy v C#</span><span class="sxs-lookup"><span data-stu-id="44b5e-131">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="44b5e-132">if-else – příkaz</span><span class="sxs-lookup"><span data-stu-id="44b5e-132">if-else statement</span></span>](../keywords/if-else.md)
- <span data-ttu-id="44b5e-133">[?. ani? [] – operátory](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="44b5e-133">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="44b5e-134">?? a?? = – operátory</span><span class="sxs-lookup"><span data-stu-id="44b5e-134">?? and ??= operators</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="44b5e-135">ref – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="44b5e-135">ref keyword</span></span>](../keywords/ref.md)
