---
title: if-else - C# Reference
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715267"
---
# <a name="if-else-c-reference"></a><span data-ttu-id="01b96-102">if-else (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="01b96-102">if-else (C# Reference)</span></span>

<span data-ttu-id="01b96-103">Příkaz `if` identifikuje, který příkaz má být spuštěn na základě hodnoty logického výrazu.</span><span class="sxs-lookup"><span data-stu-id="01b96-103">An `if` statement identifies which statement to run based on the value of a Boolean expression.</span></span> <span data-ttu-id="01b96-104">V následujícím příkladu `bool` `condition` je proměnná nastavena `true` na `if` a poté v příkazu zaškrtnuta.</span><span class="sxs-lookup"><span data-stu-id="01b96-104">In the following example, the `bool` variable `condition` is set to `true` and then checked in the `if` statement.</span></span> <span data-ttu-id="01b96-105">Výstup je `The variable is set to true.`.</span><span class="sxs-lookup"><span data-stu-id="01b96-105">The output is `The variable is set to true.`.</span></span>

[!code-csharp[csrefKeywordsSelection#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#1)]

<span data-ttu-id="01b96-106">Příklady v tomto tématu můžete spustit `Main` tak, že je umístíte do metody konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="01b96-106">You can run the examples in this topic by placing them in the `Main` method of a console app.</span></span>

<span data-ttu-id="01b96-107">Příkaz `if` v C# může mít dvě formy, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="01b96-107">An `if` statement in C# can take two forms, as the following example shows.</span></span>

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

<span data-ttu-id="01b96-108">V `if-else` prohlášení, `condition` pokud vyhodnotí `then-statement` true, spustí.</span><span class="sxs-lookup"><span data-stu-id="01b96-108">In an `if-else` statement, if `condition` evaluates to true, the `then-statement` runs.</span></span> <span data-ttu-id="01b96-109">Pokud `condition` je false, `else-statement` běží.</span><span class="sxs-lookup"><span data-stu-id="01b96-109">If `condition` is false, the `else-statement` runs.</span></span> <span data-ttu-id="01b96-110">Protože `condition` nemůže být současně pravdivé a `then-statement` nepravdivé, `else-statement` a `if-else` prohlášení nemůže nikdy oba spustit.</span><span class="sxs-lookup"><span data-stu-id="01b96-110">Because `condition` can’t be simultaneously true and false, the `then-statement` and the `else-statement` of an `if-else` statement can never both run.</span></span> <span data-ttu-id="01b96-111">Po `then-statement` `else-statement` spuštění nebo ovládací prvek je převedena na `if` další příkaz po příkazu.</span><span class="sxs-lookup"><span data-stu-id="01b96-111">After the `then-statement` or the `else-statement` runs, control is transferred to the next statement after the `if` statement.</span></span>

<span data-ttu-id="01b96-112">V `if` prohlášení, které neobsahuje `else` příkaz, `condition` pokud je `then-statement` true, spustí.</span><span class="sxs-lookup"><span data-stu-id="01b96-112">In an `if` statement that doesn’t include an `else` statement, if `condition` is true, the `then-statement` runs.</span></span> <span data-ttu-id="01b96-113">Pokud `condition` je false, ovládací prvek je převedena na další příkaz po příkazu. `if`</span><span class="sxs-lookup"><span data-stu-id="01b96-113">If `condition` is false, control is transferred to the next statement after the `if` statement.</span></span>

<span data-ttu-id="01b96-114">`then-statement` A `else-statement` může se skládat z jednoho příkazu nebo více příkazů, které jsou uzavřeny v závorkách (`{}`).</span><span class="sxs-lookup"><span data-stu-id="01b96-114">Both the `then-statement` and the `else-statement` can consist of a single statement or multiple statements that are enclosed in braces (`{}`).</span></span> <span data-ttu-id="01b96-115">Pro jeden příkaz jsou závorky volitelné, ale doporučené.</span><span class="sxs-lookup"><span data-stu-id="01b96-115">For a single statement, the braces are optional but recommended.</span></span>

<span data-ttu-id="01b96-116">Příkaz nebo příkazy `then-statement` v `else-statement` a může být jakéhokoli `if` druhu, včetně `if` jiného příkazu vnořené uvnitř původní ho příkazu.</span><span class="sxs-lookup"><span data-stu-id="01b96-116">The statement or statements in the `then-statement` and the `else-statement` can be of any kind, including another `if` statement nested inside the original `if` statement.</span></span> <span data-ttu-id="01b96-117">`if` V nosných `else` příkazech patří `if` každá klauzule poslední `else`klauzuli, která nemá odpovídající .</span><span class="sxs-lookup"><span data-stu-id="01b96-117">In nested `if` statements, each `else` clause belongs to the last `if` that doesn’t have a corresponding `else`.</span></span> <span data-ttu-id="01b96-118">V následujícím příkladu se `m > 10` `n > 20` zobrazí, `Result1` pokud oba a vyhodnotit na true.</span><span class="sxs-lookup"><span data-stu-id="01b96-118">In the following example, `Result1` appears if both `m > 10` and `n > 20` evaluate to true.</span></span> <span data-ttu-id="01b96-119">Pokud `m > 10` je `n > 20` pravda, `Result2` ale je nepravdivé, se objeví.</span><span class="sxs-lookup"><span data-stu-id="01b96-119">If `m > 10` is true but `n > 20` is false, `Result2` appears.</span></span>

[!code-csharp[csrefKeywordsSelection#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#2)]

<span data-ttu-id="01b96-120">Pokud se místo `Result2` toho chcete `(m > 10)` zobrazit, když je false, můžete určit, že přidružení pomocí `if` závorek k vytvoření začátku a konce vnořený příkaz, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="01b96-120">If, instead, you want `Result2` to appear when `(m > 10)` is false, you can specify that association by using braces to establish the start and end of the nested `if` statement, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsSelection#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#3)]

<span data-ttu-id="01b96-121">`Result2`pokud se `(m > 10)` stav vyhodnotí jako nepravdivý.</span><span class="sxs-lookup"><span data-stu-id="01b96-121">`Result2` appears if the condition `(m > 10)` evaluates to false.</span></span>

## <a name="example"></a><span data-ttu-id="01b96-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="01b96-122">Example</span></span>

<span data-ttu-id="01b96-123">V následujícím příkladu zadáte znak z klávesnice a program použije `if` vnořený příkaz k určení, zda je vstupní znak abecední znak.</span><span class="sxs-lookup"><span data-stu-id="01b96-123">In the following example, you enter a character from the keyboard, and the program uses a nested `if` statement to determine whether the input character is an alphabetic character.</span></span> <span data-ttu-id="01b96-124">Pokud je vstupní znak abecední znak, program zkontroluje, zda je vstupní znak malá nebo velká.</span><span class="sxs-lookup"><span data-stu-id="01b96-124">If the input character is an alphabetic character, the program checks whether the input character is lowercase or uppercase.</span></span> <span data-ttu-id="01b96-125">Pro každý případ se zobrazí zpráva.</span><span class="sxs-lookup"><span data-stu-id="01b96-125">A message appears for each case.</span></span>

[!code-csharp[csrefKeywordsSelection#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#4)]

## <a name="example"></a><span data-ttu-id="01b96-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="01b96-126">Example</span></span>

<span data-ttu-id="01b96-127">Můžete také vnořit `if` příkaz uvnitř bloku else, jak ukazuje následující částečný kód.</span><span class="sxs-lookup"><span data-stu-id="01b96-127">You also can nest an `if` statement inside an else block, as the following partial code shows.</span></span> <span data-ttu-id="01b96-128">Příklad vnoří příkazy `if` uvnitř dva bloky else a jeden pak blokovat.</span><span class="sxs-lookup"><span data-stu-id="01b96-128">The example nests `if` statements inside two else blocks and one then block.</span></span> <span data-ttu-id="01b96-129">Komentáře určují, které podmínky jsou v každém bloku pravdivé nebo nepravdivé.</span><span class="sxs-lookup"><span data-stu-id="01b96-129">The comments specify which conditions are true or false in each block.</span></span>

[!code-csharp[csrefKeywordsSelection#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#5)]

## <a name="example"></a><span data-ttu-id="01b96-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="01b96-130">Example</span></span>

<span data-ttu-id="01b96-131">Následující příklad určuje, zda je vstupní znak malé písmeno, velké písmeno nebo číslo.</span><span class="sxs-lookup"><span data-stu-id="01b96-131">The following example determines whether an input character is a lowercase letter, an uppercase letter, or a number.</span></span> <span data-ttu-id="01b96-132">Pokud jsou všechny tři podmínky false, znak není alfanumerický znak.</span><span class="sxs-lookup"><span data-stu-id="01b96-132">If all three conditions are false, the character isn’t an alphanumeric character.</span></span> <span data-ttu-id="01b96-133">Příklad zobrazí zprávu pro každý případ.</span><span class="sxs-lookup"><span data-stu-id="01b96-133">The example displays a message for each case.</span></span>

[!code-csharp[csrefKeywordsSelection#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#6)]

<span data-ttu-id="01b96-134">Stejně jako příkaz v bloku else nebo pak blok může být libovolný platný příkaz, můžete použít libovolný platný logický výraz pro podmínku.</span><span class="sxs-lookup"><span data-stu-id="01b96-134">Just as a statement in the else block or the then block can be any valid statement, you can use any valid Boolean expression for the condition.</span></span> <span data-ttu-id="01b96-135">Můžete použít [logické operátory,](../operators/boolean-logical-operators.md) například `!`, `&&` `||`, `&` `|`, a `^` vytvořit složené podmínky.</span><span class="sxs-lookup"><span data-stu-id="01b96-135">You can use [logical operators](../operators/boolean-logical-operators.md) such as `!`, `&&`, `||`, `&`, `|`, and `^` to make compound conditions.</span></span> <span data-ttu-id="01b96-136">Následující kód ukazuje příklady.</span><span class="sxs-lookup"><span data-stu-id="01b96-136">The following code shows examples.</span></span>

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

## <a name="c-language-specification"></a><span data-ttu-id="01b96-137">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="01b96-137">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="01b96-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="01b96-138">See also</span></span>

- [<span data-ttu-id="01b96-139">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="01b96-139">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="01b96-140">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="01b96-140">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="01b96-141">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="01b96-141">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="01b96-142">?: Operátor</span><span class="sxs-lookup"><span data-stu-id="01b96-142">?: Operator</span></span>](../operators/conditional-operator.md)
- [<span data-ttu-id="01b96-143">if-else – příkaz (C++)</span><span class="sxs-lookup"><span data-stu-id="01b96-143">if-else Statement (C++)</span></span>](/cpp/cpp/if-else-statement-cpp)
- [<span data-ttu-id="01b96-144">Přepnout</span><span class="sxs-lookup"><span data-stu-id="01b96-144">switch</span></span>](switch.md)
