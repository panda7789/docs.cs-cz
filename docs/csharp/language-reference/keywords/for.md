---
title: C#příkaz for
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: 5ebc478f8840173cacc0bc211061f3013379abd9
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422795"
---
# <a name="for-c-reference"></a><span data-ttu-id="77ef3-102">pro (C# referenční)</span><span class="sxs-lookup"><span data-stu-id="77ef3-102">for (C# reference)</span></span>

<span data-ttu-id="77ef3-103">Příkaz `for` spustí příkaz nebo blok příkazů, zatímco se zadaný logický výraz vyhodnotí jako `true`.</span><span class="sxs-lookup"><span data-stu-id="77ef3-103">The `for` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span>

<span data-ttu-id="77ef3-104">V jakémkoli okamžiku v rámci bloku příkazu `for` lze rozdělit smyčku pomocí příkazu [Break](break.md) nebo krokovat s další iterací ve smyčce pomocí příkazu [Continue](continue.md) .</span><span class="sxs-lookup"><span data-stu-id="77ef3-104">At any point within the `for` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="77ef3-105">Můžete také ukončit `for` smyčkou příkazy [goto](goto.md), [return](return.md)nebo [throw](throw.md) .</span><span class="sxs-lookup"><span data-stu-id="77ef3-105">You also can exit a `for` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="structure-of-the-for-statement"></a><span data-ttu-id="77ef3-106">Struktura příkazu `for`</span><span class="sxs-lookup"><span data-stu-id="77ef3-106">Structure of the `for` statement</span></span>

<span data-ttu-id="77ef3-107">Příkaz `for` definuje oddíly *inicializátoru*, *podmínky*a *iterátoru* :</span><span class="sxs-lookup"><span data-stu-id="77ef3-107">The `for` statement defines *initializer*, *condition*, and *iterator* sections:</span></span>

```csharp
for (initializer; condition; iterator)
    body
```

<span data-ttu-id="77ef3-108">Všechny tři oddíly jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="77ef3-108">All three sections are optional.</span></span> <span data-ttu-id="77ef3-109">Tělo smyčky je buď příkaz, nebo blok příkazů.</span><span class="sxs-lookup"><span data-stu-id="77ef3-109">The body of the loop is either a statement or a block of statements.</span></span>

<span data-ttu-id="77ef3-110">Následující příklad ukazuje příkaz `for` se všemi definovanými oddíly:</span><span class="sxs-lookup"><span data-stu-id="77ef3-110">The following example shows the `for` statement with all of the sections defined:</span></span>

[!code-csharp-interactive[for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a><span data-ttu-id="77ef3-111">Oddíl *inicializátoru*</span><span class="sxs-lookup"><span data-stu-id="77ef3-111">The *initializer* section</span></span>

<span data-ttu-id="77ef3-112">Příkazy v sekci *inicializátoru* jsou spouštěny pouze jednou před vstupem do smyčky.</span><span class="sxs-lookup"><span data-stu-id="77ef3-112">The statements in the *initializer* section are executed only once, before entering the loop.</span></span> <span data-ttu-id="77ef3-113">Oddíl *inicializátoru* je jedním z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="77ef3-113">The *initializer* section is either of the following:</span></span>

- <span data-ttu-id="77ef3-114">Deklarace a inicializace proměnné lokální smyčky, k nimž nelze přicházet z vnější smyčky.</span><span class="sxs-lookup"><span data-stu-id="77ef3-114">The declaration and initialization of a local loop variable, which can't be accessed from outside the loop.</span></span>

- <span data-ttu-id="77ef3-115">Nula nebo více výrazů příkazů z následujícího seznamu oddělených čárkami:</span><span class="sxs-lookup"><span data-stu-id="77ef3-115">Zero or more statement expressions from the following list, separated by commas:</span></span>

  - <span data-ttu-id="77ef3-116">příkaz [přiřazení](../operators/assignment-operator.md)</span><span class="sxs-lookup"><span data-stu-id="77ef3-116">[assignment](../operators/assignment-operator.md) statement</span></span>

  - <span data-ttu-id="77ef3-117">vyvolání metody</span><span class="sxs-lookup"><span data-stu-id="77ef3-117">invocation of a method</span></span>

  - <span data-ttu-id="77ef3-118">výraz pro [přírůstek](../operators/arithmetic-operators.md#increment-operator-) předpony nebo přípony, například `++i` nebo `i++`</span><span class="sxs-lookup"><span data-stu-id="77ef3-118">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

  - <span data-ttu-id="77ef3-119">výraz [snížení](../operators/arithmetic-operators.md#decrement-operator---) předpony nebo přípony, například `--i` nebo `i--`</span><span class="sxs-lookup"><span data-stu-id="77ef3-119">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

  - <span data-ttu-id="77ef3-120">Vytvoření objektu pomocí operátoru [New](../operators/new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="77ef3-120">creation of an object by using the [new](../operators/new-operator.md) operator</span></span>

  - <span data-ttu-id="77ef3-121">výraz [await](../operators/await.md)</span><span class="sxs-lookup"><span data-stu-id="77ef3-121">[await](../operators/await.md) expression</span></span>

<span data-ttu-id="77ef3-122">Oddíl *inicializátoru* v předchozím příkladu deklaruje a inicializuje proměnnou místní smyčky `i`:</span><span class="sxs-lookup"><span data-stu-id="77ef3-122">The *initializer* section in the example above declares and initializes the local loop variable `i`:</span></span>

```csharp
int i = 0
```

### <a name="the-condition-section"></a><span data-ttu-id="77ef3-123">Oddíl *Condition*</span><span class="sxs-lookup"><span data-stu-id="77ef3-123">The *condition* section</span></span>

<span data-ttu-id="77ef3-124">Oddíl *podmínky* , pokud je přítomen, musí být logický výraz.</span><span class="sxs-lookup"><span data-stu-id="77ef3-124">The *condition* section, if present, must be a boolean expression.</span></span> <span data-ttu-id="77ef3-125">Tento výraz je vyhodnocen před každou iterací smyčky.</span><span class="sxs-lookup"><span data-stu-id="77ef3-125">That expression is evaluated before every loop iteration.</span></span> <span data-ttu-id="77ef3-126">Pokud oddíl *Podmínka* není přítomen nebo je logický výraz vyhodnocen jako `true`, je provedena iterace další smyčky; v opačném případě se smyčka ukončí.</span><span class="sxs-lookup"><span data-stu-id="77ef3-126">If the *condition* section is not present or the boolean expression evaluates to `true`, the next loop iteration is executed; otherwise, the loop is exited.</span></span>

<span data-ttu-id="77ef3-127">Oddíl *Condition* v předchozím příkladu určuje, zda se smyčka ukončí na základě hodnoty proměnné lokální smyčky:</span><span class="sxs-lookup"><span data-stu-id="77ef3-127">The *condition* section in the example above determines if the loop terminates based on the value of the local loop variable:</span></span>

```csharp
i < 5
```

### <a name="the-iterator-section"></a><span data-ttu-id="77ef3-128">Oddíl *iterátoru*</span><span class="sxs-lookup"><span data-stu-id="77ef3-128">The *iterator* section</span></span>

<span data-ttu-id="77ef3-129">Oddíl *iterátor* určuje, co se stane po každé iteraci těla smyčky.</span><span class="sxs-lookup"><span data-stu-id="77ef3-129">The *iterator* section defines what happens after each iteration of the body of the loop.</span></span> <span data-ttu-id="77ef3-130">Oddíl *iterátoru* obsahuje nula nebo více následujících výrazů příkazu, které jsou odděleny čárkami:</span><span class="sxs-lookup"><span data-stu-id="77ef3-130">The *iterator* section contains zero or more of the following statement expressions, separated by commas:</span></span>

- <span data-ttu-id="77ef3-131">příkaz [přiřazení](../operators/assignment-operator.md)</span><span class="sxs-lookup"><span data-stu-id="77ef3-131">[assignment](../operators/assignment-operator.md) statement</span></span>

- <span data-ttu-id="77ef3-132">vyvolání metody</span><span class="sxs-lookup"><span data-stu-id="77ef3-132">invocation of a method</span></span>

- <span data-ttu-id="77ef3-133">výraz pro [přírůstek](../operators/arithmetic-operators.md#increment-operator-) předpony nebo přípony, například `++i` nebo `i++`</span><span class="sxs-lookup"><span data-stu-id="77ef3-133">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

- <span data-ttu-id="77ef3-134">výraz [snížení](../operators/arithmetic-operators.md#decrement-operator---) předpony nebo přípony, například `--i` nebo `i--`</span><span class="sxs-lookup"><span data-stu-id="77ef3-134">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

- <span data-ttu-id="77ef3-135">Vytvoření objektu pomocí operátoru [New](../operators/new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="77ef3-135">creation of an object by using the [new](../operators/new-operator.md) operator</span></span>

- <span data-ttu-id="77ef3-136">výraz [await](../operators/await.md)</span><span class="sxs-lookup"><span data-stu-id="77ef3-136">[await](../operators/await.md) expression</span></span>

<span data-ttu-id="77ef3-137">Oddíl *iterátoru* v příkladu výše zvyšuje proměnnou místní smyčky:</span><span class="sxs-lookup"><span data-stu-id="77ef3-137">The *iterator* section in the example above increments the local loop variable:</span></span>

```csharp
i++
```

## <a name="examples"></a><span data-ttu-id="77ef3-138">Příklady</span><span class="sxs-lookup"><span data-stu-id="77ef3-138">Examples</span></span>

<span data-ttu-id="77ef3-139">Následující příklad znázorňuje několik méně běžných použití oddílu `for` příkazu: přiřazení hodnoty k proměnné vnější smyčky v sekci *inicializátoru* , vyvolání metody v *inicializátoru* a *iterátoru* oddíly a změny hodnot dvou proměnných v části *iterátor* .</span><span class="sxs-lookup"><span data-stu-id="77ef3-139">The following example illustrates several less common usages of the `for` statement sections: assigning a value to an external loop variable in the *initializer* section, invoking a method in both the *initializer* and the *iterator* sections, and changing the values of two variables in the *iterator* section.</span></span> <span data-ttu-id="77ef3-140">Vyberte **Spustit** a spusťte ukázkový kód.</span><span class="sxs-lookup"><span data-stu-id="77ef3-140">Select **Run** to run the example code.</span></span> <span data-ttu-id="77ef3-141">Potom můžete kód upravit a znovu spustit.</span><span class="sxs-lookup"><span data-stu-id="77ef3-141">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[not typical for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#6)]

<span data-ttu-id="77ef3-142">Následující příklad definuje cyklus nekonečné `for`:</span><span class="sxs-lookup"><span data-stu-id="77ef3-142">The following example defines the infinite `for` loop:</span></span>

[!code-csharp[infinite for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#7)]

## <a name="c-language-specification"></a><span data-ttu-id="77ef3-143">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="77ef3-143">C# language specification</span></span>

<span data-ttu-id="77ef3-144">Další informace naleznete v části [for Statement](~/_csharplang/spec/statements.md#the-for-statement) tématu [ C# specifikace jazyka](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="77ef3-144">For more information, see [The for statement](~/_csharplang/spec/statements.md#the-for-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="77ef3-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="77ef3-145">See also</span></span>

- [<span data-ttu-id="77ef3-146">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="77ef3-146">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="77ef3-147">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="77ef3-147">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="77ef3-148">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="77ef3-148">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="77ef3-149">foreach, in</span><span class="sxs-lookup"><span data-stu-id="77ef3-149">foreach, in</span></span>](foreach-in.md)
