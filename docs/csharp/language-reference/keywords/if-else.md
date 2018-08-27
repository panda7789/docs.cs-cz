---
title: if-else (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- if_CSharpKeyword
- else
- else_CSharpKeyword
- if
helpviewer_keywords:
- else keyword [C#]
- if keyword [C#]
ms.assetid: d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2
ms.openlocfilehash: 77ee6e86017eb24d565842b3401533ebda1add35
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42932368"
---
# <a name="if-else-c-reference"></a><span data-ttu-id="444d3-102">if-else (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="444d3-102">if-else (C# Reference)</span></span>

<span data-ttu-id="444d3-103">`if` Příkaz určuje, který příkaz ke spuštění podle hodnoty `Boolean` výrazu.</span><span class="sxs-lookup"><span data-stu-id="444d3-103">An `if` statement identifies which statement to run based on the value of a `Boolean` expression.</span></span> <span data-ttu-id="444d3-104">V následujícím příkladu `Boolean` proměnné `result` je nastavena na `true` a pak se změnami `if` příkaz.</span><span class="sxs-lookup"><span data-stu-id="444d3-104">In the following example, the `Boolean` variable `result` is set to `true` and then checked in the `if` statement.</span></span> <span data-ttu-id="444d3-105">Výstup je `The variable is set to true.`.</span><span class="sxs-lookup"><span data-stu-id="444d3-105">The output is `The variable is set to true.`.</span></span>

[!code-csharp[csrefKeywordsSelection#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#1)]

<span data-ttu-id="444d3-106">V příkladech v tomto tématu můžete spustit tak, že je `Main` metoda Konzolová aplikace.</span><span class="sxs-lookup"><span data-stu-id="444d3-106">You can run the examples in this topic by placing them in the `Main` method of a console app.</span></span>

<span data-ttu-id="444d3-107">`if` Příkaz v jazyce C# může mít dvě formy, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="444d3-107">An `if` statement in C# can take two forms, as the following example shows.</span></span>

```csharp
// if-else statement
if (condition)
{
    then-statement;
}
else
{
    else-statement;
}
// Next statement in the program.

// if statement without an else
if (condition)
{
    then-statement;
}
// Next statement in the program.
```

<span data-ttu-id="444d3-108">V `if-else` příkazu, pokud `condition` vyhodnotí jako true, `then-statement` běží.</span><span class="sxs-lookup"><span data-stu-id="444d3-108">In an `if-else` statement, if `condition` evaluates to true, the `then-statement` runs.</span></span> <span data-ttu-id="444d3-109">Pokud `condition` má hodnotu false, `else-statement` běží.</span><span class="sxs-lookup"><span data-stu-id="444d3-109">If `condition` is false, the `else-statement` runs.</span></span> <span data-ttu-id="444d3-110">Protože `condition` nemůže být zároveň true a false, `then-statement` a `else-statement` z `if-else` příkazu můžete oba nespouštět.</span><span class="sxs-lookup"><span data-stu-id="444d3-110">Because `condition` can’t be simultaneously true and false, the `then-statement` and the `else-statement` of an `if-else` statement can never both run.</span></span> <span data-ttu-id="444d3-111">Po `then-statement` nebo `else-statement` spuštění, ovládací prvek bude převeden na příkaz následující po `if` příkazu.</span><span class="sxs-lookup"><span data-stu-id="444d3-111">After the `then-statement` or the `else-statement` runs, control is transferred to the next statement after the `if` statement.</span></span>

<span data-ttu-id="444d3-112">V `if` příkaz, který neobsahuje `else` příkazu, pokud `condition` má hodnotu true, `then-statement` běží.</span><span class="sxs-lookup"><span data-stu-id="444d3-112">In an `if` statement that doesn’t include an `else` statement, if `condition` is true, the `then-statement` runs.</span></span> <span data-ttu-id="444d3-113">Pokud `condition` má hodnotu false, je kontrola předána dalšímu příkazu po `if` příkazu.</span><span class="sxs-lookup"><span data-stu-id="444d3-113">If `condition` is false, control is transferred to the next statement after the `if` statement.</span></span>

<span data-ttu-id="444d3-114">Jak `then-statement` a `else-statement` se může skládat z jednoho příkazu nebo více příkazů, které jsou uzavřeny ve složených závorkách (`{}`).</span><span class="sxs-lookup"><span data-stu-id="444d3-114">Both the `then-statement` and the `else-statement` can consist of a single statement or multiple statements that are enclosed in braces (`{}`).</span></span> <span data-ttu-id="444d3-115">Pro jeden příkaz složené závorky jsou nepovinné, ale doporučený.</span><span class="sxs-lookup"><span data-stu-id="444d3-115">For a single statement, the braces are optional but recommended.</span></span>

<span data-ttu-id="444d3-116">Příkaz nebo příkazy v `then-statement` a `else-statement` mohou být jakéhokoli typu, včetně jiného `if` příkaz vnořit do původní `if` příkazu.</span><span class="sxs-lookup"><span data-stu-id="444d3-116">The statement or statements in the `then-statement` and the `else-statement` can be of any kind, including another `if` statement nested inside the original `if` statement.</span></span> <span data-ttu-id="444d3-117">Ve vnořené `if` příkazy, každý `else` klauzule patří na poslední `if` , který nemá odpovídající `else`.</span><span class="sxs-lookup"><span data-stu-id="444d3-117">In nested `if` statements, each `else` clause belongs to the last `if` that doesn’t have a corresponding `else`.</span></span> <span data-ttu-id="444d3-118">V následujícím příkladu `Result1` se zobrazí, pokud obě `m > 10` a `n > 20` vyhodnocen na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="444d3-118">In the following example, `Result1` appears if both `m > 10` and `n > 20` evaluate to true.</span></span> <span data-ttu-id="444d3-119">Pokud `m > 10` má hodnotu true, ale `n > 20` má hodnotu false, `Result2` se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="444d3-119">If `m > 10` is true but `n > 20` is false, `Result2` appears.</span></span>

[!code-csharp[csrefKeywordsSelection#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#2)]

<span data-ttu-id="444d3-120">Pokud místo toho chcete `Result2` se zobrazí, když `(m > 10)` má hodnotu false, můžete zadat toto přidružení pomocí závorek k navázání začátku a konce ve vnořeném `if` příkaz, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="444d3-120">If, instead, you want `Result2` to appear when `(m > 10)` is false, you can specify that association by using braces to establish the start and end of the nested `if` statement, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsSelection#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#3)]

<span data-ttu-id="444d3-121">`Result2` se zobrazí, pokud podmínka `(m > 10)` nevyhodnotí jako false.</span><span class="sxs-lookup"><span data-stu-id="444d3-121">`Result2` appears if the condition `(m > 10)` evaluates to false.</span></span>

## <a name="example"></a><span data-ttu-id="444d3-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="444d3-122">Example</span></span>

<span data-ttu-id="444d3-123">V následujícím příkladu, zadejte znak z klávesnice a program používá vnořený `if` příkaz k určení, zda je vstupní znak abecední znak.</span><span class="sxs-lookup"><span data-stu-id="444d3-123">In the following example, you enter a character from the keyboard, and the program uses a nested `if` statement to determine whether the input character is an alphabetic character.</span></span> <span data-ttu-id="444d3-124">Pokud vstupní znak je znak abecedy, program zkontroluje, zda je vstupní znak malé nebo velké písmeno.</span><span class="sxs-lookup"><span data-stu-id="444d3-124">If the input character is an alphabetic character, the program checks whether the input character is lowercase or uppercase.</span></span> <span data-ttu-id="444d3-125">Zobrazí se zpráva pro každý případ.</span><span class="sxs-lookup"><span data-stu-id="444d3-125">A message appears for each case.</span></span>

[!code-csharp[csrefKeywordsSelection#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#4)]

## <a name="example"></a><span data-ttu-id="444d3-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="444d3-126">Example</span></span>

<span data-ttu-id="444d3-127">Také můžete vnořit `if` výroku uvnitř jiného bloku, jak ukazuje následující kód částečné.</span><span class="sxs-lookup"><span data-stu-id="444d3-127">You also can nest an `if` statement inside an else block, as the following partial code shows.</span></span> <span data-ttu-id="444d3-128">Příklad používá vnořené `if` příkazy uvnitř jiného dvou bloků a pak jeden blok.</span><span class="sxs-lookup"><span data-stu-id="444d3-128">The example nests `if` statements inside two else blocks and one then block.</span></span> <span data-ttu-id="444d3-129">Komentáře zadejte podmínky, které jsou true nebo false v každém bloku.</span><span class="sxs-lookup"><span data-stu-id="444d3-129">The comments specify which conditions are true or false in each block.</span></span>

[!code-csharp[csrefKeywordsSelection#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#5)]

## <a name="example"></a><span data-ttu-id="444d3-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="444d3-130">Example</span></span>

<span data-ttu-id="444d3-131">Následující příklad určuje, zda je vstupní znak malé písmeno, velké písmeno nebo číslo.</span><span class="sxs-lookup"><span data-stu-id="444d3-131">The following example determines whether an input character is a lowercase letter, an uppercase letter, or a number.</span></span> <span data-ttu-id="444d3-132">Pokud jsou všechny tři podmínky hodnotu false, není znak alfanumerický znak.</span><span class="sxs-lookup"><span data-stu-id="444d3-132">If all three conditions are false, the character isn’t an alphanumeric character.</span></span> <span data-ttu-id="444d3-133">V příkladu se zobrazí zprávu pro každý případ.</span><span class="sxs-lookup"><span data-stu-id="444d3-133">The example displays a message for each case.</span></span>

[!code-csharp[csrefKeywordsSelection#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#6)]

<span data-ttu-id="444d3-134">Stejně jako příkaz v jiného bloku nebo bloku pak může být libovolný platný příkaz, můžete použít libovolný platný výraz logickou podmínku.</span><span class="sxs-lookup"><span data-stu-id="444d3-134">Just as a statement in the else block or the then block can be any valid statement, you can use any valid Boolean expression for the condition.</span></span> <span data-ttu-id="444d3-135">Můžete například použít logické operátory [ && ](../operators/conditional-and-operator.md), [ & ](../operators/and-operator.md), [ &#124; &#124; ](../operators/conditional-or-operator.md), [ &#124; ](../operators/or-operator.md) a [!](../operators/logical-negation-operator.md)</span><span class="sxs-lookup"><span data-stu-id="444d3-135">You can use logical operators such as [&&](../operators/conditional-and-operator.md), [&](../operators/and-operator.md), [&#124;&#124;](../operators/conditional-or-operator.md), [&#124;](../operators/or-operator.md) and [!](../operators/logical-negation-operator.md)</span></span> <span data-ttu-id="444d3-136">Chcete-li složených podmínek.</span><span class="sxs-lookup"><span data-stu-id="444d3-136">to make compound conditions.</span></span> <span data-ttu-id="444d3-137">Následující kód ukazuje příklady.</span><span class="sxs-lookup"><span data-stu-id="444d3-137">The following code shows examples.</span></span>

```csharp
// NOT
bool result = true;
if (!result)
{
    Console.WriteLine("The condition is true (result is false).");
}
else
{
    Console.WriteLine("The condition is false (result is true).");
}

// Short-circuit AND
int m = 9;
int n = 7;
int p = 5;
if (m >= n && m >= p)
{
    Console.WriteLine("Nothing is larger than m.");
}

// AND and NOT
if (m >= n && !(p > m))
{
    Console.WriteLine("Nothing is larger than m.");
}

// Short-circuit OR
if (m > n || m > p)
{
    Console.WriteLine("m isn't the smallest.");
}

// NOT and OR
m = 4;
if (!(m >= n || m >= p))
{
    Console.WriteLine("Now m is the smallest.");
}
// Output:
// The condition is false (result is true).
// Nothing is larger than m.
// Nothing is larger than m.
// m isn't the smallest.
// Now m is the smallest.
```

## <a name="c-language-specification"></a><span data-ttu-id="444d3-138">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="444d3-138">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="444d3-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="444d3-139">See Also</span></span>

- [<span data-ttu-id="444d3-140">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="444d3-140">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="444d3-141">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="444d3-141">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="444d3-142">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="444d3-142">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="444d3-143">?: – operátor</span><span class="sxs-lookup"><span data-stu-id="444d3-143">?: Operator</span></span>](../operators/conditional-operator.md)  
- [<span data-ttu-id="444d3-144">if-else – příkaz (C++)</span><span class="sxs-lookup"><span data-stu-id="444d3-144">if-else Statement (C++)</span></span>](/cpp/cpp/if-else-statement-cpp)  
- [<span data-ttu-id="444d3-145">switch</span><span class="sxs-lookup"><span data-stu-id="444d3-145">switch</span></span>](switch.md)  
