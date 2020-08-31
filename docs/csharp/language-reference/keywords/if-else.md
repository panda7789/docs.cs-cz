---
description: Reference if-else-C#
title: Reference if-else-C#
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
ms.openlocfilehash: e2de84807a049bd47ea277db9fb010d0c2e4857d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118504"
---
# <a name="if-else-c-reference"></a><span data-ttu-id="6acb3-103">if-else (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="6acb3-103">if-else (C# Reference)</span></span>

<span data-ttu-id="6acb3-104">`if`Příkaz určuje, který příkaz se má spustit na základě hodnoty logického výrazu.</span><span class="sxs-lookup"><span data-stu-id="6acb3-104">An `if` statement identifies which statement to run based on the value of a Boolean expression.</span></span> <span data-ttu-id="6acb3-105">V následujícím příkladu `bool` `condition` je proměnná nastavena na `true` a poté vrácena do `if` příkazu.</span><span class="sxs-lookup"><span data-stu-id="6acb3-105">In the following example, the `bool` variable `condition` is set to `true` and then checked in the `if` statement.</span></span> <span data-ttu-id="6acb3-106">Výstup je `The variable is set to true.`.</span><span class="sxs-lookup"><span data-stu-id="6acb3-106">The output is `The variable is set to true.`.</span></span>

[!code-csharp[csrefKeywordsSelection#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#1)]

<span data-ttu-id="6acb3-107">Příklady v tomto tématu můžete spustit tak, že je umístíte do `Main` metody konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="6acb3-107">You can run the examples in this topic by placing them in the `Main` method of a console app.</span></span>

<span data-ttu-id="6acb3-108">`if`Příkaz v jazyce C# může přijmout dva formuláře, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="6acb3-108">An `if` statement in C# can take two forms, as the following example shows.</span></span>

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

<span data-ttu-id="6acb3-109">V `if-else` příkazu, pokud se `condition` vyhodnotí jako true, `then-statement` spustí se.</span><span class="sxs-lookup"><span data-stu-id="6acb3-109">In an `if-else` statement, if `condition` evaluates to true, the `then-statement` runs.</span></span> <span data-ttu-id="6acb3-110">Pokud `condition` je hodnota false, `else-statement` spuštění.</span><span class="sxs-lookup"><span data-stu-id="6acb3-110">If `condition` is false, the `else-statement` runs.</span></span> <span data-ttu-id="6acb3-111">Vzhledem k tomu `condition` , že nemohou být současně true a false, nemůže být `then-statement` `else-statement` příkaz a `if-else` příkazu nikdy spouštěn současně.</span><span class="sxs-lookup"><span data-stu-id="6acb3-111">Because `condition` can’t be simultaneously true and false, the `then-statement` and the `else-statement` of an `if-else` statement can never both run.</span></span> <span data-ttu-id="6acb3-112">Po `then-statement` `else-statement` spuštění nebo je ovládací prvek převeden na další příkaz po `if` příkazu.</span><span class="sxs-lookup"><span data-stu-id="6acb3-112">After the `then-statement` or the `else-statement` runs, control is transferred to the next statement after the `if` statement.</span></span>

<span data-ttu-id="6acb3-113">V `if` příkazu, který neobsahuje `else` příkaz, pokud `condition` je true, `then-statement` spustí se.</span><span class="sxs-lookup"><span data-stu-id="6acb3-113">In an `if` statement that doesn’t include an `else` statement, if `condition` is true, the `then-statement` runs.</span></span> <span data-ttu-id="6acb3-114">Pokud `condition` je hodnota false, ovládací prvek bude převeden na další příkaz po `if` příkazu.</span><span class="sxs-lookup"><span data-stu-id="6acb3-114">If `condition` is false, control is transferred to the next statement after the `if` statement.</span></span>

<span data-ttu-id="6acb3-115">Jak `then-statement` a `else-statement` může sestávat z jediného příkazu nebo více příkazů, které jsou uzavřeny v závorkách ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="6acb3-115">Both the `then-statement` and the `else-statement` can consist of a single statement or multiple statements that are enclosed in braces (`{}`).</span></span> <span data-ttu-id="6acb3-116">V případě jednoho příkazu jsou složené závorky volitelné, ale doporučené.</span><span class="sxs-lookup"><span data-stu-id="6acb3-116">For a single statement, the braces are optional but recommended.</span></span>

<span data-ttu-id="6acb3-117">Příkazy nebo příkazy v `then-statement` a `else-statement` mohou být libovolného druhu, včetně jiného `if` příkazu vnořeného uvnitř původního `if` příkazu.</span><span class="sxs-lookup"><span data-stu-id="6acb3-117">The statement or statements in the `then-statement` and the `else-statement` can be of any kind, including another `if` statement nested inside the original `if` statement.</span></span> <span data-ttu-id="6acb3-118">Ve vnořených `if` příkazech `else` patří každá klauzule k poslednímu `if` , který nemá odpovídající `else` .</span><span class="sxs-lookup"><span data-stu-id="6acb3-118">In nested `if` statements, each `else` clause belongs to the last `if` that doesn’t have a corresponding `else`.</span></span> <span data-ttu-id="6acb3-119">V následujícím příkladu `Result1` se zobrazí, pokud je `m > 10` a `n > 20` vyhodnocen na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="6acb3-119">In the following example, `Result1` appears if both `m > 10` and `n > 20` evaluate to true.</span></span> <span data-ttu-id="6acb3-120">Pokud `m > 10` má hodnotu true `n > 20` , ale je false, `Result2` zobrazí se.</span><span class="sxs-lookup"><span data-stu-id="6acb3-120">If `m > 10` is true but `n > 20` is false, `Result2` appears.</span></span>

[!code-csharp[csrefKeywordsSelection#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#2)]

<span data-ttu-id="6acb3-121">Pokud místo toho chcete zobrazit, `Result2` Pokud `(m > 10)` je false, můžete zadat toto přidružení pomocí složených závorek pro vytvoření začátku a konce vnořeného `if` příkazu, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="6acb3-121">If, instead, you want `Result2` to appear when `(m > 10)` is false, you can specify that association by using braces to establish the start and end of the nested `if` statement, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsSelection#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#3)]

<span data-ttu-id="6acb3-122">`Result2` zobrazí se, pokud je podmínka `(m > 10)` vyhodnocena jako NEPRAVDA.</span><span class="sxs-lookup"><span data-stu-id="6acb3-122">`Result2` appears if the condition `(m > 10)` evaluates to false.</span></span>

## <a name="example"></a><span data-ttu-id="6acb3-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="6acb3-123">Example</span></span>

<span data-ttu-id="6acb3-124">V následujícím příkladu zadáte znak z klávesnice a program použije vnořený `if` příkaz k určení, zda je vstupním znakem abecední znak.</span><span class="sxs-lookup"><span data-stu-id="6acb3-124">In the following example, you enter a character from the keyboard, and the program uses a nested `if` statement to determine whether the input character is an alphabetic character.</span></span> <span data-ttu-id="6acb3-125">Pokud je vstupním znakem abecední znak, program zkontroluje, zda je vstupní znak malý nebo malý.</span><span class="sxs-lookup"><span data-stu-id="6acb3-125">If the input character is an alphabetic character, the program checks whether the input character is lowercase or uppercase.</span></span> <span data-ttu-id="6acb3-126">Pro každý případ se zobrazí zpráva.</span><span class="sxs-lookup"><span data-stu-id="6acb3-126">A message appears for each case.</span></span>

[!code-csharp[csrefKeywordsSelection#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#4)]

## <a name="example"></a><span data-ttu-id="6acb3-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="6acb3-127">Example</span></span>

<span data-ttu-id="6acb3-128">Příkaz lze také vnořit `if` do bloku else, jak ukazuje následující částečný kód.</span><span class="sxs-lookup"><span data-stu-id="6acb3-128">You can also nest an `if` statement inside an else block, as the following partial code shows.</span></span> <span data-ttu-id="6acb3-129">Příklad vnořovat `if` příkazy uvnitř dvou bloků else a jeden blok po bloku.</span><span class="sxs-lookup"><span data-stu-id="6acb3-129">The example nests `if` statements inside two else blocks and one then block.</span></span> <span data-ttu-id="6acb3-130">Komentáře určují, které podmínky jsou v každém bloku pravdivé nebo nepravdivé.</span><span class="sxs-lookup"><span data-stu-id="6acb3-130">The comments specify which conditions are true or false in each block.</span></span>

[!code-csharp[csrefKeywordsSelection#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#5)]

## <a name="example"></a><span data-ttu-id="6acb3-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="6acb3-131">Example</span></span>

<span data-ttu-id="6acb3-132">Následující příklad určuje, zda je vstupní znak malé písmeno, velké písmeno nebo číslo.</span><span class="sxs-lookup"><span data-stu-id="6acb3-132">The following example determines whether an input character is a lowercase letter, an uppercase letter, or a number.</span></span> <span data-ttu-id="6acb3-133">Pokud jsou všechny tři podmínky false, znak není alfanumerický znak.</span><span class="sxs-lookup"><span data-stu-id="6acb3-133">If all three conditions are false, the character isn’t an alphanumeric character.</span></span> <span data-ttu-id="6acb3-134">V příkladu se zobrazí zpráva pro každý případ.</span><span class="sxs-lookup"><span data-stu-id="6acb3-134">The example displays a message for each case.</span></span>

[!code-csharp[csrefKeywordsSelection#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#6)]

<span data-ttu-id="6acb3-135">Stejně jako příkaz v bloku else nebo blok, který může být libovolným platným příkazem, můžete pro podmínku použít libovolný platný logický výraz.</span><span class="sxs-lookup"><span data-stu-id="6acb3-135">Just as a statement in the else block or the then block can be any valid statement, you can use any valid Boolean expression for the condition.</span></span> <span data-ttu-id="6acb3-136">Pomocí [logických operátorů](../operators/boolean-logical-operators.md) , jako jsou,,, `!` `&&` `||` `&` , `|` a, lze `^` provádět složené podmínky.</span><span class="sxs-lookup"><span data-stu-id="6acb3-136">You can use [logical operators](../operators/boolean-logical-operators.md) such as `!`, `&&`, `||`, `&`, `|`, and `^` to make compound conditions.</span></span> <span data-ttu-id="6acb3-137">Následující kód ukazuje příklady.</span><span class="sxs-lookup"><span data-stu-id="6acb3-137">The following code shows examples.</span></span>

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

## <a name="c-language-specification"></a><span data-ttu-id="6acb3-138">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6acb3-138">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="6acb3-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="6acb3-139">See also</span></span>

- [<span data-ttu-id="6acb3-140">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6acb3-140">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6acb3-141">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="6acb3-141">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6acb3-142">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6acb3-142">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="6acb3-143">?: – Operátor</span><span class="sxs-lookup"><span data-stu-id="6acb3-143">?: Operator</span></span>](../operators/conditional-operator.md)
- [<span data-ttu-id="6acb3-144">if-else – příkaz (C++)</span><span class="sxs-lookup"><span data-stu-id="6acb3-144">if-else Statement (C++)</span></span>](/cpp/cpp/if-else-statement-cpp)
- [<span data-ttu-id="6acb3-145">přepnutí</span><span class="sxs-lookup"><span data-stu-id="6acb3-145">switch</span></span>](switch.md)
