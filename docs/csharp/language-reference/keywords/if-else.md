---
title: if-else- C# reference
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
ms.openlocfilehash: 98c1a8dceec3e5a47627841988e2d722c56fc36c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715267"
---
# <a name="if-else-c-reference"></a><span data-ttu-id="69527-102">if-else (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="69527-102">if-else (C# Reference)</span></span>

<span data-ttu-id="69527-103">Příkaz `if` identifikuje, který příkaz se má spustit na základě hodnoty logického výrazu.</span><span class="sxs-lookup"><span data-stu-id="69527-103">An `if` statement identifies which statement to run based on the value of a Boolean expression.</span></span> <span data-ttu-id="69527-104">V následujícím příkladu je proměnná `bool` `condition` nastavená na `true` a pak se vrátila do příkazu `if`.</span><span class="sxs-lookup"><span data-stu-id="69527-104">In the following example, the `bool` variable `condition` is set to `true` and then checked in the `if` statement.</span></span> <span data-ttu-id="69527-105">Výstup je `The variable is set to true.`.</span><span class="sxs-lookup"><span data-stu-id="69527-105">The output is `The variable is set to true.`.</span></span>

[!code-csharp[csrefKeywordsSelection#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#1)]

<span data-ttu-id="69527-106">Příklady v tomto tématu můžete spustit tak, že je umístíte do metody `Main` konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="69527-106">You can run the examples in this topic by placing them in the `Main` method of a console app.</span></span>

<span data-ttu-id="69527-107">Příkaz `if` v C# nástroji může přijmout dvě formy, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="69527-107">An `if` statement in C# can take two forms, as the following example shows.</span></span>

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

<span data-ttu-id="69527-108">Pokud se v příkazu `if-else` `condition` vyhodnotí jako true, `then-statement` se spustí.</span><span class="sxs-lookup"><span data-stu-id="69527-108">In an `if-else` statement, if `condition` evaluates to true, the `then-statement` runs.</span></span> <span data-ttu-id="69527-109">Pokud je `condition` false, `else-statement` se spustí.</span><span class="sxs-lookup"><span data-stu-id="69527-109">If `condition` is false, the `else-statement` runs.</span></span> <span data-ttu-id="69527-110">Vzhledem k tomu, že `condition` nemůže být současně true a false, `then-statement` a `else-statement` příkazu `if-else` nikdy nejdou spustit současně.</span><span class="sxs-lookup"><span data-stu-id="69527-110">Because `condition` can’t be simultaneously true and false, the `then-statement` and the `else-statement` of an `if-else` statement can never both run.</span></span> <span data-ttu-id="69527-111">Po `then-statement` nebo spuštění `else-statement` je ovládací prvek převeden na další příkaz po příkazu `if`.</span><span class="sxs-lookup"><span data-stu-id="69527-111">After the `then-statement` or the `else-statement` runs, control is transferred to the next statement after the `if` statement.</span></span>

<span data-ttu-id="69527-112">V příkazu `if`, který neobsahuje příkaz `else`, pokud `condition` má hodnotu true, `then-statement` se spustí.</span><span class="sxs-lookup"><span data-stu-id="69527-112">In an `if` statement that doesn’t include an `else` statement, if `condition` is true, the `then-statement` runs.</span></span> <span data-ttu-id="69527-113">Pokud je `condition` false, ovládací prvek se převede na další příkaz po příkazu `if`.</span><span class="sxs-lookup"><span data-stu-id="69527-113">If `condition` is false, control is transferred to the next statement after the `if` statement.</span></span>

<span data-ttu-id="69527-114">`then-statement` i `else-statement` se mohou skládat z jednoho příkazu nebo více příkazů, které jsou uzavřeny v závorkách (`{}`).</span><span class="sxs-lookup"><span data-stu-id="69527-114">Both the `then-statement` and the `else-statement` can consist of a single statement or multiple statements that are enclosed in braces (`{}`).</span></span> <span data-ttu-id="69527-115">V případě jednoho příkazu jsou složené závorky volitelné, ale doporučené.</span><span class="sxs-lookup"><span data-stu-id="69527-115">For a single statement, the braces are optional but recommended.</span></span>

<span data-ttu-id="69527-116">Příkaz nebo příkazy v `then-statement` a `else-statement` mohou být libovolného druhu, včetně jiného příkazu `if` vnořeného v původním příkazu `if`.</span><span class="sxs-lookup"><span data-stu-id="69527-116">The statement or statements in the `then-statement` and the `else-statement` can be of any kind, including another `if` statement nested inside the original `if` statement.</span></span> <span data-ttu-id="69527-117">Ve vnořených příkazech `if` každá klauzule `else` patří do posledního `if`, který nemá odpovídající `else`.</span><span class="sxs-lookup"><span data-stu-id="69527-117">In nested `if` statements, each `else` clause belongs to the last `if` that doesn’t have a corresponding `else`.</span></span> <span data-ttu-id="69527-118">V následujícím příkladu se `Result1` zobrazí, pokud jsou obě `m > 10` a `n > 20` vyhodnoceny jako true.</span><span class="sxs-lookup"><span data-stu-id="69527-118">In the following example, `Result1` appears if both `m > 10` and `n > 20` evaluate to true.</span></span> <span data-ttu-id="69527-119">Pokud je `m > 10` true, ale `n > 20` je false, `Result2` se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="69527-119">If `m > 10` is true but `n > 20` is false, `Result2` appears.</span></span>

[!code-csharp[csrefKeywordsSelection#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#2)]

<span data-ttu-id="69527-120">Pokud místo toho chcete, aby se `Result2` zobrazovaly, když `(m > 10)` je false, můžete zadat toto přidružení pomocí složených závorek pro vytvoření začátku a konce vnořeného příkazu `if`, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="69527-120">If, instead, you want `Result2` to appear when `(m > 10)` is false, you can specify that association by using braces to establish the start and end of the nested `if` statement, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsSelection#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#3)]

<span data-ttu-id="69527-121">`Result2` se zobrazí, pokud je podmínka `(m > 10)` vyhodnocena jako NEPRAVDA.</span><span class="sxs-lookup"><span data-stu-id="69527-121">`Result2` appears if the condition `(m > 10)` evaluates to false.</span></span>

## <a name="example"></a><span data-ttu-id="69527-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="69527-122">Example</span></span>

<span data-ttu-id="69527-123">V následujícím příkladu zadáte znak z klávesnice a program použije vnořený příkaz `if` k určení, zda je vstupním znakem abecední znak.</span><span class="sxs-lookup"><span data-stu-id="69527-123">In the following example, you enter a character from the keyboard, and the program uses a nested `if` statement to determine whether the input character is an alphabetic character.</span></span> <span data-ttu-id="69527-124">Pokud je vstupním znakem abecední znak, program zkontroluje, zda je vstupní znak malý nebo malý.</span><span class="sxs-lookup"><span data-stu-id="69527-124">If the input character is an alphabetic character, the program checks whether the input character is lowercase or uppercase.</span></span> <span data-ttu-id="69527-125">Pro každý případ se zobrazí zpráva.</span><span class="sxs-lookup"><span data-stu-id="69527-125">A message appears for each case.</span></span>

[!code-csharp[csrefKeywordsSelection#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#4)]

## <a name="example"></a><span data-ttu-id="69527-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="69527-126">Example</span></span>

<span data-ttu-id="69527-127">Můžete také vnořit příkaz `if` do bloku else, jak ukazuje následující částečný kód.</span><span class="sxs-lookup"><span data-stu-id="69527-127">You also can nest an `if` statement inside an else block, as the following partial code shows.</span></span> <span data-ttu-id="69527-128">Příklad vnořování `if` příkazy uvnitř dvou bloků else a jednom bloku.</span><span class="sxs-lookup"><span data-stu-id="69527-128">The example nests `if` statements inside two else blocks and one then block.</span></span> <span data-ttu-id="69527-129">Komentáře určují, které podmínky jsou v každém bloku pravdivé nebo nepravdivé.</span><span class="sxs-lookup"><span data-stu-id="69527-129">The comments specify which conditions are true or false in each block.</span></span>

[!code-csharp[csrefKeywordsSelection#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#5)]

## <a name="example"></a><span data-ttu-id="69527-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="69527-130">Example</span></span>

<span data-ttu-id="69527-131">Následující příklad určuje, zda je vstupní znak malé písmeno, velké písmeno nebo číslo.</span><span class="sxs-lookup"><span data-stu-id="69527-131">The following example determines whether an input character is a lowercase letter, an uppercase letter, or a number.</span></span> <span data-ttu-id="69527-132">Pokud jsou všechny tři podmínky false, znak není alfanumerický znak.</span><span class="sxs-lookup"><span data-stu-id="69527-132">If all three conditions are false, the character isn’t an alphanumeric character.</span></span> <span data-ttu-id="69527-133">V příkladu se zobrazí zpráva pro každý případ.</span><span class="sxs-lookup"><span data-stu-id="69527-133">The example displays a message for each case.</span></span>

[!code-csharp[csrefKeywordsSelection#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#6)]

<span data-ttu-id="69527-134">Stejně jako příkaz v bloku else nebo blok, který může být libovolným platným příkazem, můžete pro podmínku použít libovolný platný logický výraz.</span><span class="sxs-lookup"><span data-stu-id="69527-134">Just as a statement in the else block or the then block can be any valid statement, you can use any valid Boolean expression for the condition.</span></span> <span data-ttu-id="69527-135">Složené podmínky můžete provádět pomocí [logických operátorů](../operators/boolean-logical-operators.md) , jako jsou `!`, `&&`, `||`, `&`, `|`a `^`.</span><span class="sxs-lookup"><span data-stu-id="69527-135">You can use [logical operators](../operators/boolean-logical-operators.md) such as `!`, `&&`, `||`, `&`, `|`, and `^` to make compound conditions.</span></span> <span data-ttu-id="69527-136">Následující kód ukazuje příklady.</span><span class="sxs-lookup"><span data-stu-id="69527-136">The following code shows examples.</span></span>

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

## <a name="c-language-specification"></a><span data-ttu-id="69527-137">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="69527-137">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="69527-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="69527-138">See also</span></span>

- [<span data-ttu-id="69527-139">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="69527-139">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="69527-140">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="69527-140">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="69527-141">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="69527-141">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="69527-142">?: – operátor</span><span class="sxs-lookup"><span data-stu-id="69527-142">?: Operator</span></span>](../operators/conditional-operator.md)
- [<span data-ttu-id="69527-143">if-else – příkaz (C++)</span><span class="sxs-lookup"><span data-stu-id="69527-143">if-else Statement (C++)</span></span>](/cpp/cpp/if-else-statement-cpp)
- [<span data-ttu-id="69527-144">switch</span><span class="sxs-lookup"><span data-stu-id="69527-144">switch</span></span>](switch.md)
