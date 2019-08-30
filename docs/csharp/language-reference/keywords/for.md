---
title: C#příkaz for
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: 61315a04ca8d5a619a3dcaf43b15a309919d3c42
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2019
ms.locfileid: "70167873"
---
# <a name="for-c-reference"></a><span data-ttu-id="80fa2-102">for (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="80fa2-102">for (C# reference)</span></span>

<span data-ttu-id="80fa2-103">Příkaz provede příkaz nebo blok příkazů, zatímco se zadaný logický výraz vyhodnotí `true`jako. `for`</span><span class="sxs-lookup"><span data-stu-id="80fa2-103">The `for` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span>

<span data-ttu-id="80fa2-104">V jakémkoli bodě `for` bloku příkazu můžete přerušit smyčku pomocí příkazu [Break](break.md) nebo krokovat s další iterací ve smyčce pomocí příkazu [Continue](continue.md) .</span><span class="sxs-lookup"><span data-stu-id="80fa2-104">At any point within the `for` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="80fa2-105">`for` Můžete také ukončit smyčku příkazy [goto](goto.md), [return](return.md)nebo [throw](throw.md) .</span><span class="sxs-lookup"><span data-stu-id="80fa2-105">You also can exit a `for` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="structure-of-the-for-statement"></a><span data-ttu-id="80fa2-106">`for` Struktura příkazu</span><span class="sxs-lookup"><span data-stu-id="80fa2-106">Structure of the `for` statement</span></span>

<span data-ttu-id="80fa2-107">Příkaz definuje oddíly *inicializátoru*, *podmínky*a *iterátoru* : `for`</span><span class="sxs-lookup"><span data-stu-id="80fa2-107">The `for` statement defines *initializer*, *condition*, and *iterator* sections:</span></span>

```csharp
for (initializer; condition; iterator)
    body
```

<span data-ttu-id="80fa2-108">Všechny tři oddíly jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="80fa2-108">All three sections are optional.</span></span> <span data-ttu-id="80fa2-109">Tělo smyčky je buď příkaz, nebo blok příkazů.</span><span class="sxs-lookup"><span data-stu-id="80fa2-109">The body of the loop is either a statement or a block of statements.</span></span>

<span data-ttu-id="80fa2-110">Následující příklad ukazuje `for` příkaz se všemi definovanými oddíly:</span><span class="sxs-lookup"><span data-stu-id="80fa2-110">The following example shows the `for` statement with all of the sections defined:</span></span>

[!code-csharp-interactive[for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a><span data-ttu-id="80fa2-111">Oddíl *inicializátoru*</span><span class="sxs-lookup"><span data-stu-id="80fa2-111">The *initializer* section</span></span>

<span data-ttu-id="80fa2-112">Příkazy v sekci *inicializátoru* jsou spouštěny pouze jednou před vstupem do smyčky.</span><span class="sxs-lookup"><span data-stu-id="80fa2-112">The statements in the *initializer* section are executed only once, before entering the loop.</span></span> <span data-ttu-id="80fa2-113">Oddíl *inicializátoru* je jedním z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="80fa2-113">The *initializer* section is either of the following:</span></span>

- <span data-ttu-id="80fa2-114">Deklarace a inicializace proměnné lokální smyčky, k nimž nelze přicházet z vnější smyčky.</span><span class="sxs-lookup"><span data-stu-id="80fa2-114">The declaration and initialization of a local loop variable, which can't be accessed from outside the loop.</span></span>

- <span data-ttu-id="80fa2-115">Nula nebo více výrazů příkazů z následujícího seznamu oddělených čárkami:</span><span class="sxs-lookup"><span data-stu-id="80fa2-115">Zero or more statement expressions from the following list, separated by commas:</span></span>

  - <span data-ttu-id="80fa2-116">příkaz [přiřazení](../operators/assignment-operator.md)</span><span class="sxs-lookup"><span data-stu-id="80fa2-116">[assignment](../operators/assignment-operator.md) statement</span></span>

  - <span data-ttu-id="80fa2-117">vyvolání metody</span><span class="sxs-lookup"><span data-stu-id="80fa2-117">invocation of a method</span></span>

  - <span data-ttu-id="80fa2-118">výraz pro `++i` [přírůstek](../operators/arithmetic-operators.md#increment-operator-) předpony nebo přípony, například nebo`i++`</span><span class="sxs-lookup"><span data-stu-id="80fa2-118">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

  - <span data-ttu-id="80fa2-119">výraz pro `--i` [snížení](../operators/arithmetic-operators.md#decrement-operator---) předpony nebo přípony, například nebo`i--`</span><span class="sxs-lookup"><span data-stu-id="80fa2-119">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

  - <span data-ttu-id="80fa2-120">Vytvoření objektu pomocí operátoru [New](../operators/new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="80fa2-120">creation of an object by using the [new](../operators/new-operator.md) operator</span></span>

  - <span data-ttu-id="80fa2-121">výraz [await](../operators/await.md)</span><span class="sxs-lookup"><span data-stu-id="80fa2-121">[await](../operators/await.md) expression</span></span>

<span data-ttu-id="80fa2-122">Oddíl *inicializátoru* v předchozím příkladu deklaruje a inicializuje proměnnou `i`lokální smyčky:</span><span class="sxs-lookup"><span data-stu-id="80fa2-122">The *initializer* section in the example above declares and initializes the local loop variable `i`:</span></span>

```csharp
int i = 0
```

### <a name="the-condition-section"></a><span data-ttu-id="80fa2-123">Oddíl *Condition*</span><span class="sxs-lookup"><span data-stu-id="80fa2-123">The *condition* section</span></span>

<span data-ttu-id="80fa2-124">Oddíl *podmínky* , pokud je přítomen, musí být logický výraz.</span><span class="sxs-lookup"><span data-stu-id="80fa2-124">The *condition* section, if present, must be a boolean expression.</span></span> <span data-ttu-id="80fa2-125">Tento výraz je vyhodnocen před každou iterací smyčky.</span><span class="sxs-lookup"><span data-stu-id="80fa2-125">That expression is evaluated before every loop iteration.</span></span> <span data-ttu-id="80fa2-126">Pokud oddíl *Podmínka* není přítomen nebo je logický výraz vyhodnocen `true`jako, je provedena iterace další smyčky. v opačném případě se smyčka ukončí.</span><span class="sxs-lookup"><span data-stu-id="80fa2-126">If the *condition* section is not present or the boolean expression evaluates to `true`, the next loop iteration is executed; otherwise, the loop is exited.</span></span>

<span data-ttu-id="80fa2-127">Oddíl *Condition* v předchozím příkladu určuje, zda se smyčka ukončí na základě hodnoty proměnné lokální smyčky:</span><span class="sxs-lookup"><span data-stu-id="80fa2-127">The *condition* section in the example above determines if the loop terminates based on the value of the local loop variable:</span></span>

```csharp
i < 5
```

### <a name="the-iterator-section"></a><span data-ttu-id="80fa2-128">Oddíl *iterátoru*</span><span class="sxs-lookup"><span data-stu-id="80fa2-128">The *iterator* section</span></span>

<span data-ttu-id="80fa2-129">Oddíl *iterátor* určuje, co se stane po každé iteraci těla smyčky.</span><span class="sxs-lookup"><span data-stu-id="80fa2-129">The *iterator* section defines what happens after each iteration of the body of the loop.</span></span> <span data-ttu-id="80fa2-130">Oddíl *iterátoru* obsahuje nula nebo více následujících výrazů příkazu, které jsou odděleny čárkami:</span><span class="sxs-lookup"><span data-stu-id="80fa2-130">The *iterator* section contains zero or more of the following statement expressions, separated by commas:</span></span>

- <span data-ttu-id="80fa2-131">příkaz [přiřazení](../operators/assignment-operator.md)</span><span class="sxs-lookup"><span data-stu-id="80fa2-131">[assignment](../operators/assignment-operator.md) statement</span></span>

- <span data-ttu-id="80fa2-132">vyvolání metody</span><span class="sxs-lookup"><span data-stu-id="80fa2-132">invocation of a method</span></span>

- <span data-ttu-id="80fa2-133">výraz pro `++i` [přírůstek](../operators/arithmetic-operators.md#increment-operator-) předpony nebo přípony, například nebo`i++`</span><span class="sxs-lookup"><span data-stu-id="80fa2-133">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

- <span data-ttu-id="80fa2-134">výraz pro `--i` [snížení](../operators/arithmetic-operators.md#decrement-operator---) předpony nebo přípony, například nebo`i--`</span><span class="sxs-lookup"><span data-stu-id="80fa2-134">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

- <span data-ttu-id="80fa2-135">Vytvoření objektu pomocí operátoru [New](../operators/new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="80fa2-135">creation of an object by using the [new](../operators/new-operator.md) operator</span></span>

- <span data-ttu-id="80fa2-136">výraz [await](../operators/await.md)</span><span class="sxs-lookup"><span data-stu-id="80fa2-136">[await](../operators/await.md) expression</span></span>

<span data-ttu-id="80fa2-137">Oddíl *iterátoru* v příkladu výše zvyšuje proměnnou místní smyčky:</span><span class="sxs-lookup"><span data-stu-id="80fa2-137">The *iterator* section in the example above increments the local loop variable:</span></span>

```csharp
i++
```

## <a name="examples"></a><span data-ttu-id="80fa2-138">Příklady</span><span class="sxs-lookup"><span data-stu-id="80fa2-138">Examples</span></span>

<span data-ttu-id="80fa2-139">Následující příklad znázorňuje několik méně běžných použití `for` oddílu příkazu: přiřazení hodnoty k proměnné vnější smyčky v sekci *inicializátoru* , vyvolání metody v *inicializátoru* a *iterátoru* oddíly a změny hodnot dvou proměnných v části *iterátor* .</span><span class="sxs-lookup"><span data-stu-id="80fa2-139">The following example illustrates several less common usages of the `for` statement sections: assigning a value to an external loop variable in the *initializer* section, invoking a method in both the *initializer* and the *iterator* sections, and changing the values of two variables in the *iterator* section.</span></span> <span data-ttu-id="80fa2-140">Vyberte **Spustit** a spusťte ukázkový kód.</span><span class="sxs-lookup"><span data-stu-id="80fa2-140">Select **Run** to run the example code.</span></span> <span data-ttu-id="80fa2-141">Potom můžete kód upravit a znovu spustit.</span><span class="sxs-lookup"><span data-stu-id="80fa2-141">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[not typical for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#6)]

<span data-ttu-id="80fa2-142">Následující příklad definuje nekonečnou `for` smyčku:</span><span class="sxs-lookup"><span data-stu-id="80fa2-142">The following example defines the infinite `for` loop:</span></span>

[!code-csharp[infinite for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#7)]

## <a name="c-language-specification"></a><span data-ttu-id="80fa2-143">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="80fa2-143">C# language specification</span></span>

<span data-ttu-id="80fa2-144">Další informace naleznete v části [for Statement](~/_csharplang/spec/statements.md#the-for-statement) tématu [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="80fa2-144">For more information, see [The for statement](~/_csharplang/spec/statements.md#the-for-statement) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="80fa2-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="80fa2-145">See also</span></span>

- [<span data-ttu-id="80fa2-146">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="80fa2-146">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="80fa2-147">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="80fa2-147">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="80fa2-148">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="80fa2-148">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="80fa2-149">foreach, in</span><span class="sxs-lookup"><span data-stu-id="80fa2-149">foreach, in</span></span>](foreach-in.md)
