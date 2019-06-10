---
title: '?: Operator - C# odkaz'
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
ms.openlocfilehash: ae3039df2c1260211f4c7ec3e813db1d0c6cd42b
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2019
ms.locfileid: "66815932"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="6649f-102">?: – Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="6649f-102">?: Operator (C# Reference)</span></span>

<span data-ttu-id="6649f-103">Podmiňovací operátor `?:`, běžně označované jako Ternární podmiňovací operátor vyhodnocuje logický výraz a vrátí výsledek vyhodnocení výrazu jeden ze dvou výrazů v závislosti na tom, jestli logický výraz vyhodnocen jako `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="6649f-103">The conditional operator `?:`, commonly known as the ternary conditional operator, evaluates a Boolean expression, and returns the result of evaluating one of two expressions, depending on whether the Boolean expression evaluates to `true` or `false`.</span></span> <span data-ttu-id="6649f-104">Počínaje C# 7.2, [ref podmíněný výraz](#conditional-ref-expression) vrátí odkaz na výsledek jednoho ze dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="6649f-104">Beginning with C# 7.2, the [conditional ref expression](#conditional-ref-expression) returns the reference to the result of one of the two expressions.</span></span>

<span data-ttu-id="6649f-105">Syntaxe pro podmiňovací operátor je následující:</span><span class="sxs-lookup"><span data-stu-id="6649f-105">The syntax for the conditional operator is as follows:</span></span>

```csharp
condition ? consequent : alternative
```

<span data-ttu-id="6649f-106">`condition` Výraz se musí vyhodnotit na `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="6649f-106">The `condition` expression must evaluate to `true` or `false`.</span></span> <span data-ttu-id="6649f-107">Pokud `condition` vyhodnotí jako `true`, `consequent` výraz je vyhodnocen a výsledek bude výsledek operace.</span><span class="sxs-lookup"><span data-stu-id="6649f-107">If `condition` evaluates to `true`, the `consequent` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="6649f-108">Pokud `condition` vyhodnotí jako `false`, `alternative` výraz je vyhodnocen a výsledek bude výsledek operace.</span><span class="sxs-lookup"><span data-stu-id="6649f-108">If `condition` evaluates to `false`, the `alternative` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="6649f-109">Pouze `consequent` nebo `alternative` vyhodnocena.</span><span class="sxs-lookup"><span data-stu-id="6649f-109">Only `consequent` or `alternative` is evaluated.</span></span>

<span data-ttu-id="6649f-110">Typ `consequent` a `alternative` musí být musí být stejné nebo existovat implicitní převod z jednoho typu na druhý.</span><span class="sxs-lookup"><span data-stu-id="6649f-110">The type of `consequent` and `alternative` must be the same, or there must be an implicit conversion from one type to the other.</span></span>

<span data-ttu-id="6649f-111">Podmíněný operátor je asociativní zprava, to znamená, výraz ve tvaru</span><span class="sxs-lookup"><span data-stu-id="6649f-111">The conditional operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ? b : c ? d : e
```

<span data-ttu-id="6649f-112">je vyhodnocen jako</span><span class="sxs-lookup"><span data-stu-id="6649f-112">is evaluated as</span></span>

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> <span data-ttu-id="6649f-113">Vám pomůže následující mnemotechnická mějte na paměti, jak se vyhodnocují podmíněný operátor:</span><span class="sxs-lookup"><span data-stu-id="6649f-113">You can use the following mnemonic device to remember how the conditional operator is evaluated:</span></span>
>
> ```text
> is this condition true ? yes : no
> ```

<span data-ttu-id="6649f-114">Následující příklad ukazuje použití podmíněný operátor:</span><span class="sxs-lookup"><span data-stu-id="6649f-114">The following example demonstrates the usage of the conditional operator:</span></span>

[!code-csharp-interactive[non ref conditional](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a><span data-ttu-id="6649f-115">Ref podmíněný výraz</span><span class="sxs-lookup"><span data-stu-id="6649f-115">Conditional ref expression</span></span>

<span data-ttu-id="6649f-116">Počínaje C# 7.2, vám pomůže ref podmíněný výraz vrátí odkaz na výsledek jednoho ze dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="6649f-116">Beginning with C# 7.2, you can use the conditional ref expression to return the reference to the result of one of the two expressions.</span></span> <span data-ttu-id="6649f-117">Přiřadíte tento odkaz na [lokální proměnná podle odkazu](../keywords/ref.md#ref-locals) nebo [lokální proměnná podle odkazu jen pro čtení](../keywords/ref.md#ref-readonly-locals) proměnnou, nebo jej použít jako [odkazovat na návratovou hodnotu](../keywords/ref.md#reference-return-values) nebo jako [ `ref` – metoda Parametr](../keywords/ref.md#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="6649f-117">You can assign that reference to a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable, or use it as a [reference return value](../keywords/ref.md#reference-return-values) or as a [`ref` method parameter](../keywords/ref.md#passing-an-argument-by-reference).</span></span>

<span data-ttu-id="6649f-118">Syntaxe ref podmíněného výrazu je následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="6649f-118">The syntax for the conditional ref expression is as follows:</span></span>

```csharp
condition ? ref consequent : ref alternative
```

<span data-ttu-id="6649f-119">Stejně jako původní podmíněný operátor ref podmíněný výraz je vyhodnocen jako pouze jeden ze dvou výrazů: buď `consequent` nebo `alternative`.</span><span class="sxs-lookup"><span data-stu-id="6649f-119">Like the original conditional operator, the conditional ref expression evaluates only one of the two expressions: either `consequent` or `alternative`.</span></span>

<span data-ttu-id="6649f-120">V případě ref podmíněný výraz typu `consequent` a `alternative` se musí shodovat.</span><span class="sxs-lookup"><span data-stu-id="6649f-120">In the case of the conditional ref expression, the type of `consequent` and `alternative` must be the same.</span></span>

<span data-ttu-id="6649f-121">Následující příklad ukazuje použití ref podmíněný výraz:</span><span class="sxs-lookup"><span data-stu-id="6649f-121">The following example demonstrates the usage of the conditional ref expression:</span></span>

[!code-csharp-interactive[conditional ref](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#ConditionalRef)]

<span data-ttu-id="6649f-122">Další informace najdete v tématu [Poznámka návrh funkce](../../../../_csharplang/proposals/csharp-7.2/conditional-ref.md).</span><span class="sxs-lookup"><span data-stu-id="6649f-122">For more information, see the [feature proposal note](../../../../_csharplang/proposals/csharp-7.2/conditional-ref.md).</span></span>

## <a name="conditional-operator-and-an-ifelse-statement"></a><span data-ttu-id="6649f-123">Podmíněný operátor a `if..else` – příkaz</span><span class="sxs-lookup"><span data-stu-id="6649f-123">Conditional operator and an `if..else` statement</span></span>

<span data-ttu-id="6649f-124">Použití podmíněného operátoru přes [if-else](../keywords/if-else.md) příkaz může způsobit stručnější kód v případech, když potřebujete podmíněně k výpočtu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6649f-124">Use of the conditional operator over an [if-else](../keywords/if-else.md) statement might result in more concise code in cases when you need conditionally to compute a value.</span></span> <span data-ttu-id="6649f-125">Následující příklad ukazuje dva způsoby, jak klasifikovat jako záporné nebo nezáporné celé číslo:</span><span class="sxs-lookup"><span data-stu-id="6649f-125">The following example demonstrates two ways to classify an integer as negative or nonnegative:</span></span>

[!code-csharp[conditional and if-else](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a><span data-ttu-id="6649f-126">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="6649f-126">Operator overloadability</span></span>

<span data-ttu-id="6649f-127">Podmiňovací operátor nelze přetížit.</span><span class="sxs-lookup"><span data-stu-id="6649f-127">The conditional operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6649f-128">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6649f-128">C# language specification</span></span>

<span data-ttu-id="6649f-129">Další informace najdete v tématu [Podmiňovací operátor](~/_csharplang/spec/expressions.md#conditional-operator) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="6649f-129">For more information, see the [Conditional operator](~/_csharplang/spec/expressions.md#conditional-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6649f-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6649f-130">See also</span></span>

- [<span data-ttu-id="6649f-131">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6649f-131">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6649f-132">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="6649f-132">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6649f-133">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6649f-133">C# Operators</span></span>](index.md)
- [<span data-ttu-id="6649f-134">if-else – příkaz</span><span class="sxs-lookup"><span data-stu-id="6649f-134">if-else statement</span></span>](../keywords/if-else.md)
- <span data-ttu-id="6649f-135">[?. a? operátory]](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="6649f-135">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="6649f-136">?? – operátor</span><span class="sxs-lookup"><span data-stu-id="6649f-136">?? operator</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="6649f-137">ref keyword</span><span class="sxs-lookup"><span data-stu-id="6649f-137">ref keyword</span></span>](../keywords/ref.md)
