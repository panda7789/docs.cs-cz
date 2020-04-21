---
title: for statement - odkaz C#
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: cb83fa015eea19b156faebb5bed18cc1f0970cc1
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738798"
---
# <a name="for-c-reference"></a><span data-ttu-id="542d7-102">pro (odkaz C#)</span><span class="sxs-lookup"><span data-stu-id="542d7-102">for (C# reference)</span></span>

<span data-ttu-id="542d7-103">Příkaz `for` provede příkaz nebo blok příkazů, zatímco zadaný logický `true`výraz je vyhodnocen .</span><span class="sxs-lookup"><span data-stu-id="542d7-103">The `for` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span>

<span data-ttu-id="542d7-104">V libovolném `for` bodě v rámci bloku příkazu můžete vymanit ze smyčky pomocí [příkazu break](break.md) nebo krok k další iteraci ve smyčce pomocí [příkazu continue.](continue.md)</span><span class="sxs-lookup"><span data-stu-id="542d7-104">At any point within the `for` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="542d7-105">`for` Můžete také ukončit smyčku [příkazy goto](goto.md), [return](return.md)nebo [throw.](throw.md)</span><span class="sxs-lookup"><span data-stu-id="542d7-105">You can also exit a `for` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="structure-of-the-for-statement"></a><span data-ttu-id="542d7-106">Struktura `for` prohlášení</span><span class="sxs-lookup"><span data-stu-id="542d7-106">Structure of the `for` statement</span></span>

<span data-ttu-id="542d7-107">Příkaz `for` definuje *inicializátor*, *podmínku*a *oddíly iterátoru:*</span><span class="sxs-lookup"><span data-stu-id="542d7-107">The `for` statement defines *initializer*, *condition*, and *iterator* sections:</span></span>

```csharp
for (initializer; condition; iterator)
    body
```

<span data-ttu-id="542d7-108">Všechny tři části jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="542d7-108">All three sections are optional.</span></span> <span data-ttu-id="542d7-109">Tělo smyčky je buď příkaz nebo blok příkazů.</span><span class="sxs-lookup"><span data-stu-id="542d7-109">The body of the loop is either a statement or a block of statements.</span></span>

<span data-ttu-id="542d7-110">Následující příklad ukazuje `for` příkaz se všemi definovanými oddíly:</span><span class="sxs-lookup"><span data-stu-id="542d7-110">The following example shows the `for` statement with all of the sections defined:</span></span>

[!code-csharp-interactive[for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a><span data-ttu-id="542d7-111">*Inicializační* sekce</span><span class="sxs-lookup"><span data-stu-id="542d7-111">The *initializer* section</span></span>

<span data-ttu-id="542d7-112">Příkazy v *inicializační* části jsou provedeny pouze jednou před vstupem do smyčky.</span><span class="sxs-lookup"><span data-stu-id="542d7-112">The statements in the *initializer* section are executed only once, before entering the loop.</span></span> <span data-ttu-id="542d7-113">*Inicializační* část je buď z následujících:</span><span class="sxs-lookup"><span data-stu-id="542d7-113">The *initializer* section is either of the following:</span></span>

- <span data-ttu-id="542d7-114">Deklarace a inicializace proměnné účastnického vedení, ke které nelze získat přístup mimo smyčku.</span><span class="sxs-lookup"><span data-stu-id="542d7-114">The declaration and initialization of a local loop variable, which can't be accessed from outside the loop.</span></span>

- <span data-ttu-id="542d7-115">Nula nebo více výrazů příkazu z následujícího seznamu, oddělených čárkami:</span><span class="sxs-lookup"><span data-stu-id="542d7-115">Zero or more statement expressions from the following list, separated by commas:</span></span>

  - <span data-ttu-id="542d7-116">[příkaz přiřazení](../operators/assignment-operator.md)</span><span class="sxs-lookup"><span data-stu-id="542d7-116">[assignment](../operators/assignment-operator.md) statement</span></span>

  - <span data-ttu-id="542d7-117">vyvolání metody</span><span class="sxs-lookup"><span data-stu-id="542d7-117">invocation of a method</span></span>

  - <span data-ttu-id="542d7-118">výraz [přírůstek](../operators/arithmetic-operators.md#increment-operator-) předpony nebo přípony, například `++i` nebo`i++`</span><span class="sxs-lookup"><span data-stu-id="542d7-118">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

  - <span data-ttu-id="542d7-119">výraz [snížení](../operators/arithmetic-operators.md#decrement-operator---) předpony nebo postfixu, například `--i` nebo`i--`</span><span class="sxs-lookup"><span data-stu-id="542d7-119">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

  - <span data-ttu-id="542d7-120">vytvoření objektu pomocí [nového](../operators/new-operator.md) operátoru</span><span class="sxs-lookup"><span data-stu-id="542d7-120">creation of an object by using the [new](../operators/new-operator.md) operator</span></span>

  - <span data-ttu-id="542d7-121">[await](../operators/await.md) výraz</span><span class="sxs-lookup"><span data-stu-id="542d7-121">[await](../operators/await.md) expression</span></span>

<span data-ttu-id="542d7-122">*Inicializační* část ve výše uvedeném příkladu deklaruje a inicializuje proměnnou `i`účastnického připojení :</span><span class="sxs-lookup"><span data-stu-id="542d7-122">The *initializer* section in the example above declares and initializes the local loop variable `i`:</span></span>

```csharp
int i = 0
```

### <a name="the-condition-section"></a><span data-ttu-id="542d7-123">Část *podmínky*</span><span class="sxs-lookup"><span data-stu-id="542d7-123">The *condition* section</span></span>

<span data-ttu-id="542d7-124">Část *podmínky,* pokud je k dispozici, musí být logický výraz.</span><span class="sxs-lookup"><span data-stu-id="542d7-124">The *condition* section, if present, must be a boolean expression.</span></span> <span data-ttu-id="542d7-125">Tento výraz je vyhodnocen před každou iteraci smyčky.</span><span class="sxs-lookup"><span data-stu-id="542d7-125">That expression is evaluated before every loop iteration.</span></span> <span data-ttu-id="542d7-126">Pokud oddíl *podmínky* není k dispozici nebo logický `true`výraz vyhodnotí , provede se další iterace smyčky; v opačném případě je smyčka ukončena.</span><span class="sxs-lookup"><span data-stu-id="542d7-126">If the *condition* section is not present or the boolean expression evaluates to `true`, the next loop iteration is executed; otherwise, the loop is exited.</span></span>

<span data-ttu-id="542d7-127">Část *podmínky* ve výše uvedeném příkladu určuje, zda smyčka končí na základě hodnoty proměnné účastnického vedení:</span><span class="sxs-lookup"><span data-stu-id="542d7-127">The *condition* section in the example above determines if the loop terminates based on the value of the local loop variable:</span></span>

```csharp
i < 5
```

### <a name="the-iterator-section"></a><span data-ttu-id="542d7-128">Sekce *iterátoru*</span><span class="sxs-lookup"><span data-stu-id="542d7-128">The *iterator* section</span></span>

<span data-ttu-id="542d7-129">*Iterátor* část definuje, co se stane po každé iteraci těla smyčky.</span><span class="sxs-lookup"><span data-stu-id="542d7-129">The *iterator* section defines what happens after each iteration of the body of the loop.</span></span> <span data-ttu-id="542d7-130">Sekce *iterátoru* obsahuje nulu nebo více následujících výrazů příkazu oddělených čárkami:</span><span class="sxs-lookup"><span data-stu-id="542d7-130">The *iterator* section contains zero or more of the following statement expressions, separated by commas:</span></span>

- <span data-ttu-id="542d7-131">[příkaz přiřazení](../operators/assignment-operator.md)</span><span class="sxs-lookup"><span data-stu-id="542d7-131">[assignment](../operators/assignment-operator.md) statement</span></span>

- <span data-ttu-id="542d7-132">vyvolání metody</span><span class="sxs-lookup"><span data-stu-id="542d7-132">invocation of a method</span></span>

- <span data-ttu-id="542d7-133">výraz [přírůstek](../operators/arithmetic-operators.md#increment-operator-) předpony nebo přípony, například `++i` nebo`i++`</span><span class="sxs-lookup"><span data-stu-id="542d7-133">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

- <span data-ttu-id="542d7-134">výraz [snížení](../operators/arithmetic-operators.md#decrement-operator---) předpony nebo postfixu, například `--i` nebo`i--`</span><span class="sxs-lookup"><span data-stu-id="542d7-134">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

- <span data-ttu-id="542d7-135">vytvoření objektu pomocí [nového](../operators/new-operator.md) operátoru</span><span class="sxs-lookup"><span data-stu-id="542d7-135">creation of an object by using the [new](../operators/new-operator.md) operator</span></span>

- <span data-ttu-id="542d7-136">[await](../operators/await.md) výraz</span><span class="sxs-lookup"><span data-stu-id="542d7-136">[await](../operators/await.md) expression</span></span>

<span data-ttu-id="542d7-137">Část *iterátoru* ve výše uvedeném příkladu zintáží proměnnou účastnického vedení:</span><span class="sxs-lookup"><span data-stu-id="542d7-137">The *iterator* section in the example above increments the local loop variable:</span></span>

```csharp
i++
```

## <a name="examples"></a><span data-ttu-id="542d7-138">Příklady</span><span class="sxs-lookup"><span data-stu-id="542d7-138">Examples</span></span>

<span data-ttu-id="542d7-139">Následující příklad ilustruje několik méně běžných `for` použití oddílů příkazu: přiřazení hodnoty proměnné externí smyčky v části *inicializátoru,* vyvolání metody v oddílech *inicializátor* u *iterátoru* a změna hodnot dvou proměnných v části *iterátoru.*</span><span class="sxs-lookup"><span data-stu-id="542d7-139">The following example illustrates several less common usages of the `for` statement sections: assigning a value to an external loop variable in the *initializer* section, invoking a method in both the *initializer* and the *iterator* sections, and changing the values of two variables in the *iterator* section.</span></span> <span data-ttu-id="542d7-140">Chcete-li spustit ukázkový kód, vyberte **spustit.**</span><span class="sxs-lookup"><span data-stu-id="542d7-140">Select **Run** to run the example code.</span></span> <span data-ttu-id="542d7-141">Poté můžete kód upravit a znovu spustit.</span><span class="sxs-lookup"><span data-stu-id="542d7-141">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[not typical for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#6)]

<span data-ttu-id="542d7-142">Následující příklad definuje nekonečnou `for` smyčku:</span><span class="sxs-lookup"><span data-stu-id="542d7-142">The following example defines the infinite `for` loop:</span></span>

[!code-csharp[infinite for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#7)]

## <a name="c-language-specification"></a><span data-ttu-id="542d7-143">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="542d7-143">C# language specification</span></span>

<span data-ttu-id="542d7-144">Další informace naleznete v části [for statement](~/_csharplang/spec/statements.md#the-for-statement) ve [specifikaci jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="542d7-144">For more information, see [The for statement](~/_csharplang/spec/statements.md#the-for-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="542d7-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="542d7-145">See also</span></span>

- [<span data-ttu-id="542d7-146">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="542d7-146">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="542d7-147">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="542d7-147">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="542d7-148">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="542d7-148">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="542d7-149">foreach, in</span><span class="sxs-lookup"><span data-stu-id="542d7-149">foreach, in</span></span>](foreach-in.md)
