---
title: for (Referenční dokumentace jazyka C#)
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: beac7727c8ce83d8ea20f0fc578f80ceef3053e7
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208358"
---
# <a name="for-c-reference"></a><span data-ttu-id="50c6e-102">pro (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="50c6e-102">for (C# reference)</span></span>

<span data-ttu-id="50c6e-103">`for` Příkaz spustí příkaz nebo blok příkazů při zadaný logický výraz vyhodnocen jako `true`.</span><span class="sxs-lookup"><span data-stu-id="50c6e-103">The `for` statement executes a statement or a block of statements while a specified boolean expression evaluates to `true`.</span></span>

<span data-ttu-id="50c6e-104">Kdykoli bodu v rámci `for` příkaz bloku, může dojít k narušení mimo smyčky pomocí [zalomení](break.md) příkaz nebo krok do další iterace ve smyčce pomocí [pokračovat](continue.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="50c6e-104">At any point within the `for` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="50c6e-105">Také můžete ukončit `for` cykly pomocí [goto](goto.md), [vrátit](return.md), nebo [throw](throw.md) příkazy.</span><span class="sxs-lookup"><span data-stu-id="50c6e-105">You also can exit a `for` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>
  
## <a name="structure-of-the-for-statement"></a><span data-ttu-id="50c6e-106">Struktura `for` – příkaz</span><span class="sxs-lookup"><span data-stu-id="50c6e-106">Structure of the `for` statement</span></span>

<span data-ttu-id="50c6e-107">`for` Definuje příkaz *inicializátoru*, *podmínku*, a *iterator* částech:</span><span class="sxs-lookup"><span data-stu-id="50c6e-107">The `for` statement defines *initializer*, *condition*, and *iterator* sections:</span></span>
  
```csharp
for (initializer; condition; iterator)  
    body  
```

<span data-ttu-id="50c6e-108">Všechny tři části jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="50c6e-108">All three sections are optional.</span></span> <span data-ttu-id="50c6e-109">Do těla smyčky je příkaz nebo blok příkazů.</span><span class="sxs-lookup"><span data-stu-id="50c6e-109">The body of the loop is either a statement or a block of statements.</span></span>

<span data-ttu-id="50c6e-110">Následující příklad ukazuje `for` příkaz s všechny oddíly definované:</span><span class="sxs-lookup"><span data-stu-id="50c6e-110">The following example shows the `for` statement with all of the sections defined:</span></span>

[!code-csharp-interactive[for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a><span data-ttu-id="50c6e-111">*Inicializátoru* části</span><span class="sxs-lookup"><span data-stu-id="50c6e-111">The *initializer* section</span></span>

<span data-ttu-id="50c6e-112">Příkazy v *inicializátoru* části jsou vykonány pouze jednou před vstupem smyčky.</span><span class="sxs-lookup"><span data-stu-id="50c6e-112">The statements in the *initializer* section are executed only once, before entering the loop.</span></span> <span data-ttu-id="50c6e-113">*Inicializátoru* část se z následujících:</span><span class="sxs-lookup"><span data-stu-id="50c6e-113">The *initializer* section is either of the following:</span></span>

- <span data-ttu-id="50c6e-114">Deklarace a inicializace proměnnou místní smyčky, která není přístupná z mimo smyčku.</span><span class="sxs-lookup"><span data-stu-id="50c6e-114">The declaration and initialization of a local loop variable, which can't be accessed from outside the loop.</span></span>

- <span data-ttu-id="50c6e-115">Nula nebo více výrazů příkaz z následujícího seznamu, oddělených čárkami:</span><span class="sxs-lookup"><span data-stu-id="50c6e-115">Zero or more statement expressions from the following list, separated by commas:</span></span>

  - <span data-ttu-id="50c6e-116">[přiřazení](../operators/assignment-operator.md) – příkaz</span><span class="sxs-lookup"><span data-stu-id="50c6e-116">[assignment](../operators/assignment-operator.md) statement</span></span>

  - <span data-ttu-id="50c6e-117">volání metody</span><span class="sxs-lookup"><span data-stu-id="50c6e-117">invocation of a method</span></span>  

  - <span data-ttu-id="50c6e-118">předpony nebo přípony [přírůstek](../operators/increment-operator.md) výrazu, jako například `++i` nebo `i++`</span><span class="sxs-lookup"><span data-stu-id="50c6e-118">prefix or postfix [increment](../operators/increment-operator.md) expression, such as `++i` or `i++`</span></span>  

  - <span data-ttu-id="50c6e-119">předpony nebo přípony [snížení](../operators/decrement-operator.md) výrazu, jako například `--i` nebo `i--`</span><span class="sxs-lookup"><span data-stu-id="50c6e-119">prefix or postfix [decrement](../operators/decrement-operator.md) expression, such as `--i` or `i--`</span></span>  

  - <span data-ttu-id="50c6e-120">Vytvoření objektu pomocí [nové](new-operator.md) – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="50c6e-120">creation of an object by using [new](new-operator.md) keyword</span></span>

  - <span data-ttu-id="50c6e-121">[await](await.md) výraz</span><span class="sxs-lookup"><span data-stu-id="50c6e-121">[await](await.md) expression</span></span>

<span data-ttu-id="50c6e-122">*Inicializátoru* část v předchozím příkladu deklaruje a inicializuje proměnnou místní smyčky `i`:</span><span class="sxs-lookup"><span data-stu-id="50c6e-122">The *initializer* section in the example above declares and initializes the local loop variable `i`:</span></span>

```csharp
int i = 0
```

### <a name="the-condition-section"></a><span data-ttu-id="50c6e-123">*Podmínku* části</span><span class="sxs-lookup"><span data-stu-id="50c6e-123">The *condition* section</span></span>

<span data-ttu-id="50c6e-124">*Podmínku* část, pokud existuje, musí být logický výraz.</span><span class="sxs-lookup"><span data-stu-id="50c6e-124">The *condition* section, if present, must be a boolean expression.</span></span> <span data-ttu-id="50c6e-125">Tento výraz se vyhodnocují před každou iteraci smyčky.</span><span class="sxs-lookup"><span data-stu-id="50c6e-125">That expression is evaluated before every loop iteration.</span></span> <span data-ttu-id="50c6e-126">Pokud *podmínku* části není k dispozici nebo je logický výraz vyhodnocen `true`další iterace smyčky je provedeno; jinak, smyčky je byl ukončen.</span><span class="sxs-lookup"><span data-stu-id="50c6e-126">If the *condition* section is not present or the boolean expression evaluates to `true`, the next loop iteration is executed; otherwise, the loop is exited.</span></span>

<span data-ttu-id="50c6e-127">*Podmínku* část v předchozím příkladu určuje Pokud smyčky ukončí na základě hodnoty proměnné místní smyčka:</span><span class="sxs-lookup"><span data-stu-id="50c6e-127">The *condition* section in the example above determines if the loop terminates based on the value of the local loop variable:</span></span>

```csharp
i < 5
```

### <a name="the-iterator-section"></a><span data-ttu-id="50c6e-128">*Iterator* části</span><span class="sxs-lookup"><span data-stu-id="50c6e-128">The *iterator* section</span></span>

<span data-ttu-id="50c6e-129">*Iterator* oddíl definuje, co se stane po každé iteraci těla smyčky.</span><span class="sxs-lookup"><span data-stu-id="50c6e-129">The *iterator* section defines what happens after each iteration of the body of the loop.</span></span> <span data-ttu-id="50c6e-130">*Iterator* část obsahuje nula nebo více z těchto výrazů příkaz oddělené čárkami:</span><span class="sxs-lookup"><span data-stu-id="50c6e-130">The *iterator* section contains zero or more of the following statement expressions, separated by commas:</span></span>  

- <span data-ttu-id="50c6e-131">[přiřazení](../operators/assignment-operator.md) – příkaz</span><span class="sxs-lookup"><span data-stu-id="50c6e-131">[assignment](../operators/assignment-operator.md) statement</span></span>

- <span data-ttu-id="50c6e-132">volání metody</span><span class="sxs-lookup"><span data-stu-id="50c6e-132">invocation of a method</span></span>  

- <span data-ttu-id="50c6e-133">předpony nebo přípony [přírůstek](../operators/increment-operator.md) výrazu, jako například `++i` nebo `i++`</span><span class="sxs-lookup"><span data-stu-id="50c6e-133">prefix or postfix [increment](../operators/increment-operator.md) expression, such as `++i` or `i++`</span></span>  

- <span data-ttu-id="50c6e-134">předpony nebo přípony [snížení](../operators/decrement-operator.md) výrazu, jako například `--i` nebo `i--`</span><span class="sxs-lookup"><span data-stu-id="50c6e-134">prefix or postfix [decrement](../operators/decrement-operator.md) expression, such as `--i` or `i--`</span></span>  

- <span data-ttu-id="50c6e-135">Vytvoření objektu pomocí [nové](new-operator.md) – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="50c6e-135">creation of an object by using [new](new-operator.md) keyword</span></span>

- <span data-ttu-id="50c6e-136">[await](await.md) výraz</span><span class="sxs-lookup"><span data-stu-id="50c6e-136">[await](await.md) expression</span></span>

<span data-ttu-id="50c6e-137">*Iterator* část v předchozím příkladu zvýší proměnnou místní smyčka:</span><span class="sxs-lookup"><span data-stu-id="50c6e-137">The *iterator* section in the example above increments the local loop variable:</span></span>

```csharp
i++
```

## <a name="examples"></a><span data-ttu-id="50c6e-138">Příklady</span><span class="sxs-lookup"><span data-stu-id="50c6e-138">Examples</span></span>

<span data-ttu-id="50c6e-139">Následující příklad ilustruje několik méně běžné použití `for` příkaz částech: přiřazení hodnoty proměnné externí smyčky v *inicializátoru* části volání metody v obou  *Inicializátor* a *iterator* části a změna hodnoty dvou proměnných ve *iterator* části.</span><span class="sxs-lookup"><span data-stu-id="50c6e-139">The following example illustrates several less common usages of the `for` statement sections: assigning a value to an external loop variable in the *initializer* section, invoking a method in both the *initializer* and the *iterator* sections, and changing the values of two variables in the *iterator* section.</span></span> <span data-ttu-id="50c6e-140">Vyberte **spustit** spustit ukázkový kód.</span><span class="sxs-lookup"><span data-stu-id="50c6e-140">Select **Run** to run the example code.</span></span> <span data-ttu-id="50c6e-141">Poté můžete upravit kód a potom ho spusťte znovu.</span><span class="sxs-lookup"><span data-stu-id="50c6e-141">After that you can modify the code and run it again.</span></span>
  
[!code-csharp-interactive[not typical for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#6)]
  
<span data-ttu-id="50c6e-142">V následujícím příkladu definuje nekonečné `for` smyčka:</span><span class="sxs-lookup"><span data-stu-id="50c6e-142">The following example defines the infinite `for` loop:</span></span>
  
[!code-csharp[infinite for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#7)]
  
## <a name="c-language-specification"></a><span data-ttu-id="50c6e-143">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="50c6e-143">C# language specification</span></span>  

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
  
## <a name="see-also"></a><span data-ttu-id="50c6e-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50c6e-144">See also</span></span>

[<span data-ttu-id="50c6e-145">Pro příkaz (specifikace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="50c6e-145">The for statement (C# language specification)</span></span>](/dotnet/csharp/language-reference/language-specification/statements#the-for-statement)  
[<span data-ttu-id="50c6e-146">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="50c6e-146">C# Reference</span></span>](../index.md)  
[<span data-ttu-id="50c6e-147">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="50c6e-147">C# Programming Guide</span></span>](../../programming-guide/index.md)  
[<span data-ttu-id="50c6e-148">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="50c6e-148">C# Keywords</span></span>](index.md)  
[<span data-ttu-id="50c6e-149">foreach, in</span><span class="sxs-lookup"><span data-stu-id="50c6e-149">foreach, in</span></span>](foreach-in.md)  
[<span data-ttu-id="50c6e-150">for – příkaz (C++)</span><span class="sxs-lookup"><span data-stu-id="50c6e-150">for Statement (C++)</span></span>](/cpp/cpp/for-statement-cpp)  
[<span data-ttu-id="50c6e-151">Příkazy iterace</span><span class="sxs-lookup"><span data-stu-id="50c6e-151">Iteration Statements</span></span>](iteration-statements.md)
