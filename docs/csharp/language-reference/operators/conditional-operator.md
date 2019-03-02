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
ms.openlocfilehash: c3c875cf5b8d1b5e69cd76cb0ee4df0a989a35a0
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202896"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="85b3b-102">?: – Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="85b3b-102">?: Operator (C# Reference)</span></span>

<span data-ttu-id="85b3b-103">Podmiňovací operátor `?:`, běžně označované jako Ternární podmiňovací operátor vyhodnocuje logický výraz a vrátí výsledek vyhodnocení výrazu jeden ze dvou výrazů v závislosti na tom, jestli logický výraz vyhodnocen jako `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="85b3b-103">The conditional operator `?:`, commonly known as the ternary conditional operator, evaluates a Boolean expression, and returns the result of evaluating one of two expressions, depending on whether the Boolean expression evaluates to `true` or `false`.</span></span> <span data-ttu-id="85b3b-104">Počínaje C# 7.2, [ref podmíněný výraz](#conditional-ref-expression) vrátí odkaz na výsledek jednoho ze dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="85b3b-104">Beginning with C# 7.2, the [conditional ref expression](#conditional-ref-expression) returns the reference to the result of one of the two expressions.</span></span>

<span data-ttu-id="85b3b-105">Syntaxe pro podmiňovací operátor je následující:</span><span class="sxs-lookup"><span data-stu-id="85b3b-105">The syntax for the conditional operator is as follows:</span></span>

```csharp
condition ? consequence : alternative
```

<span data-ttu-id="85b3b-106">`condition` Výraz se musí vyhodnotit na `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="85b3b-106">The `condition` expression must evaluate to `true` or `false`.</span></span> <span data-ttu-id="85b3b-107">Pokud `condition` vyhodnotí jako `true`, `consequence` výraz je vyhodnocen a výsledek bude výsledek operace.</span><span class="sxs-lookup"><span data-stu-id="85b3b-107">If `condition` evaluates to `true`, the `consequence` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="85b3b-108">Pokud `condition` vyhodnotí jako `false`, `alternative` výraz je vyhodnocen a výsledek bude výsledek operace.</span><span class="sxs-lookup"><span data-stu-id="85b3b-108">If `condition` evaluates to `false`, the `alternative` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="85b3b-109">Pouze `consequence` nebo `alternative` vyhodnocena.</span><span class="sxs-lookup"><span data-stu-id="85b3b-109">Only `consequence` or `alternative` is evaluated.</span></span>

<span data-ttu-id="85b3b-110">Typ `consequence` a `alternative` musí být musí být stejné nebo existovat implicitní převod z jednoho typu na druhý.</span><span class="sxs-lookup"><span data-stu-id="85b3b-110">The type of `consequence` and `alternative` must be the same, or there must be an implicit conversion from one type to the other.</span></span>

<span data-ttu-id="85b3b-111">Podmíněný operátor je asociativní zprava, to znamená, výraz ve tvaru</span><span class="sxs-lookup"><span data-stu-id="85b3b-111">The conditional operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ? b : c ? d : e
```

<span data-ttu-id="85b3b-112">je vyhodnocen jako</span><span class="sxs-lookup"><span data-stu-id="85b3b-112">is evaluated as</span></span>

```csharp
a ? b : (c ? d : e)
```

<span data-ttu-id="85b3b-113">Následující příklad ukazuje použití podmíněný operátor:</span><span class="sxs-lookup"><span data-stu-id="85b3b-113">The following example demonstrates the usage of the conditional operator:</span></span>

[!code-csharp[non ref conditional](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a><span data-ttu-id="85b3b-114">Ref podmíněný výraz</span><span class="sxs-lookup"><span data-stu-id="85b3b-114">Conditional ref expression</span></span>

<span data-ttu-id="85b3b-115">Počínaje C# 7.2, vám pomůže ref podmíněný výraz vrátí odkaz na výsledek jednoho ze dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="85b3b-115">Beginning with C# 7.2, you can use the conditional ref expression to return the reference to the result of one of the two expressions.</span></span> <span data-ttu-id="85b3b-116">Přiřadíte tento odkaz na [lokální proměnná podle odkazu](../keywords/ref.md#ref-locals) nebo [lokální proměnná podle odkazu jen pro čtení](../keywords/ref.md#ref-readonly-locals) proměnnou, nebo jej použít jako [odkazovat na návratovou hodnotu](../keywords/ref.md#reference-return-values) nebo jako [ `ref` – metoda Parametr](../keywords/ref.md#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="85b3b-116">You can assign that reference to a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable, or use it as a [reference return value](../keywords/ref.md#reference-return-values) or as a [`ref` method parameter](../keywords/ref.md#passing-an-argument-by-reference).</span></span>

<span data-ttu-id="85b3b-117">Syntaxe ref podmíněného výrazu je následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="85b3b-117">The syntax for the conditional ref expression is as follows:</span></span>

```csharp
condition ? ref consequence : ref alternative
```

<span data-ttu-id="85b3b-118">Stejně jako původní podmíněný operátor ref podmíněný výraz je vyhodnocen jako pouze jeden ze dvou výrazů: buď `consequence` nebo `alternative`.</span><span class="sxs-lookup"><span data-stu-id="85b3b-118">Like the original conditional operator, the conditional ref expression evaluates only one of the two expressions: either `consequence` or `alternative`.</span></span>

<span data-ttu-id="85b3b-119">V případě ref podmíněný výraz typu `consequence` a `alternative` se musí shodovat.</span><span class="sxs-lookup"><span data-stu-id="85b3b-119">In the case of the conditional ref expression, the type of `consequence` and `alternative` must be the same.</span></span>

<span data-ttu-id="85b3b-120">Následující příklad ukazuje použití ref podmíněný výraz:</span><span class="sxs-lookup"><span data-stu-id="85b3b-120">The following example demonstrates the usage of the conditional ref expression:</span></span>

[!code-csharp[conditional ref](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalRef)]

<span data-ttu-id="85b3b-121">Další informace najdete v tématu [Poznámka návrh funkce](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.2/conditional-ref.md).</span><span class="sxs-lookup"><span data-stu-id="85b3b-121">For more information, see the [feature proposal note](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.2/conditional-ref.md).</span></span>

## <a name="conditional-operator-and-an-ifelse-statement"></a><span data-ttu-id="85b3b-122">Podmíněný operátor a `if..else` – příkaz</span><span class="sxs-lookup"><span data-stu-id="85b3b-122">Conditional operator and an `if..else` statement</span></span>

<span data-ttu-id="85b3b-123">Použití podmíněného operátoru přes [if-else](../keywords/if-else.md) příkaz může způsobit stručnější kód v případech, když potřebujete podmíněně k výpočtu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="85b3b-123">Use of the conditional operator over an [if-else](../keywords/if-else.md) statement might result in more concise code in cases when you need conditionally to compute a value.</span></span> <span data-ttu-id="85b3b-124">Následující příklad ukazuje dva způsoby, jak klasifikovat jako záporné nebo nezáporné celé číslo:</span><span class="sxs-lookup"><span data-stu-id="85b3b-124">The following example demonstrates two ways to classify an integer as negative or nonnegative:</span></span>

[!code-csharp[conditional and if-else](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#CompareWithIf)]

## <a name="operator-overloadability"></a><span data-ttu-id="85b3b-125">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="85b3b-125">Operator overloadability</span></span>

<span data-ttu-id="85b3b-126">Podmiňovací operátor nelze přetížit.</span><span class="sxs-lookup"><span data-stu-id="85b3b-126">The conditional operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="85b3b-127">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="85b3b-127">C# language specification</span></span>

<span data-ttu-id="85b3b-128">Další informace najdete v tématu [Podmiňovací operátor](~/_csharplang/spec/expressions.md#conditional-operator) část [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="85b3b-128">For more information, see the [Conditional operator](~/_csharplang/spec/expressions.md#conditional-operator) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="85b3b-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="85b3b-129">See also</span></span>

- [<span data-ttu-id="85b3b-130">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="85b3b-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="85b3b-131">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="85b3b-131">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="85b3b-132">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="85b3b-132">C# Operators</span></span>](index.md)
- [<span data-ttu-id="85b3b-133">if-else – příkaz</span><span class="sxs-lookup"><span data-stu-id="85b3b-133">if-else statement</span></span>](../keywords/if-else.md)
- <span data-ttu-id="85b3b-134">[Operátory ?. a ?[]](null-conditional-operators.md)</span><span class="sxs-lookup"><span data-stu-id="85b3b-134">[?. and ?[] Operators](null-conditional-operators.md)</span></span>
- [<span data-ttu-id="85b3b-135">?? – operátor</span><span class="sxs-lookup"><span data-stu-id="85b3b-135">?? Operator</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="85b3b-136">ref keyword</span><span class="sxs-lookup"><span data-stu-id="85b3b-136">ref keyword</span></span>](../keywords/ref.md)
