---
title: "if-else (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- if_CSharpKeyword
- else
- else_CSharpKeyword
- if
helpviewer_keywords:
- else keyword [C#]
- if keyword [C#]
ms.assetid: d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2
caps.latest.revision: "32"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a0ecc915af00caffeba92a8308a60bc24198d477
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="if-else-c-reference"></a><span data-ttu-id="85403-102">if-else (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="85403-102">if-else (C# Reference)</span></span>
<span data-ttu-id="85403-103">`if` Příkaz identifikuje, který příkaz ke spuštění na základě hodnoty z `Boolean` výraz.</span><span class="sxs-lookup"><span data-stu-id="85403-103">An `if` statement identifies which statement to run based on the value of a `Boolean` expression.</span></span> <span data-ttu-id="85403-104">V následujícím příkladu `Boolean` proměnné `result` je nastaven na `true` a pak vrátit se změnami `if` příkaz.</span><span class="sxs-lookup"><span data-stu-id="85403-104">In the following example, the `Boolean` variable `result` is set to `true` and then checked in the `if` statement.</span></span> <span data-ttu-id="85403-105">Výstupem je `The condition is true`.</span><span class="sxs-lookup"><span data-stu-id="85403-105">The output is `The condition is true`.</span></span>  
  
 [!code-csharp[csrefKeywordsSelection#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_1.cs)]  
  
 <span data-ttu-id="85403-106">V příkladech v tomto tématu můžete spustit tím, že je `Main` metoda konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="85403-106">You can run the examples in this topic by placing them in the `Main` method of a console app.</span></span>  
  
 <span data-ttu-id="85403-107">`if` Příkaz v jazyce C# může mít dvě formy, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="85403-107">An `if` statement in C# can take two forms, as the following example shows.</span></span>  
  
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
  
 <span data-ttu-id="85403-108">V `if-else` příkaz, pokud `condition` vyhodnotí jako true, `then-statement` běží.</span><span class="sxs-lookup"><span data-stu-id="85403-108">In an `if-else` statement, if `condition` evaluates to true, the `then-statement` runs.</span></span> <span data-ttu-id="85403-109">Pokud `condition` je nastavena hodnota false, `else-statement` běží.</span><span class="sxs-lookup"><span data-stu-id="85403-109">If `condition` is false, the `else-statement` runs.</span></span> <span data-ttu-id="85403-110">Protože `condition` nemůže být zároveň true a false, `then-statement` a `else-statement` z `if-else` příkaz nikdy obě spuštěním.</span><span class="sxs-lookup"><span data-stu-id="85403-110">Because `condition` can’t be simultaneously true and false, the `then-statement` and the `else-statement` of an `if-else` statement can never both run.</span></span> <span data-ttu-id="85403-111">Po `then-statement` nebo `else-statement` spustí, řízení se přenese do další příkaz po `if` příkaz.</span><span class="sxs-lookup"><span data-stu-id="85403-111">After the `then-statement` or the `else-statement` runs, control is transferred to the next statement after the `if` statement.</span></span>  
  
 <span data-ttu-id="85403-112">V `if` příkaz, který neobsahuje `else` příkaz, pokud `condition` má hodnotu true, `then-statement` běží.</span><span class="sxs-lookup"><span data-stu-id="85403-112">In an `if` statement that doesn’t include an `else` statement, if `condition` is true, the `then-statement` runs.</span></span> <span data-ttu-id="85403-113">Pokud `condition` je nastavena hodnota false, ovládací prvek je přenesen na další příkaz po `if` příkaz.</span><span class="sxs-lookup"><span data-stu-id="85403-113">If `condition` is false, control is transferred to the next statement after the `if` statement.</span></span>  
  
 <span data-ttu-id="85403-114">Jak `then-statement` a `else-statement` se může skládat z jedné příkaz nebo více příkazů, které jsou uzavřené do složených závorek (`{}`).</span><span class="sxs-lookup"><span data-stu-id="85403-114">Both the `then-statement` and the `else-statement` can consist of a single statement or multiple statements that are enclosed in braces (`{}`).</span></span> <span data-ttu-id="85403-115">Pro jediný příkaz složené závorky jsou volitelné, ale doporučené.</span><span class="sxs-lookup"><span data-stu-id="85403-115">For a single statement, the braces are optional but recommended.</span></span>  
  
 <span data-ttu-id="85403-116">Příkaz nebo příkazy v `then-statement` a `else-statement` může být libovolného typu, včetně jiné `if` příkaz vnořit původní `if` příkaz.</span><span class="sxs-lookup"><span data-stu-id="85403-116">The statement or statements in the `then-statement` and the `else-statement` can be of any kind, including another `if` statement nested inside the original `if` statement.</span></span> <span data-ttu-id="85403-117">Ve vnořených `if` příkazy, každý `else` klauzule patří na poslední `if` , nemá odpovídající `else`.</span><span class="sxs-lookup"><span data-stu-id="85403-117">In nested `if` statements, each `else` clause belongs to the last `if` that doesn’t have a corresponding `else`.</span></span> <span data-ttu-id="85403-118">V následujícím příkladu `Result1` se zobrazí, pokud obě `m > 10` a `n > 20` vyhodnotit na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="85403-118">In the following example, `Result1` appears if both `m > 10` and `n > 20` evaluate to true.</span></span> <span data-ttu-id="85403-119">Pokud `m > 10` hodnotu true, ale `n > 20` je nastavena hodnota false, `Result2` se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="85403-119">If `m > 10` is true but `n > 20` is false, `Result2` appears.</span></span>  
  
 [!code-csharp[csrefKeywordsSelection#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_2.cs)]  
  
 <span data-ttu-id="85403-120">Pokud chcete místo toho `Result2` se objeví při `(m > 10)` je nastavena hodnota false, můžete toto přidružení pomocí složené závorky k vytvoření počáteční a koncová vnořeného `if` příkaz, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="85403-120">If, instead, you want `Result2` to appear when `(m > 10)` is false, you can specify that association by using braces to establish the start and end of the nested `if` statement, as the following example shows.</span></span>  
  
 [!code-csharp[csrefKeywordsSelection#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_3.cs)]  
  
 <span data-ttu-id="85403-121">`Result2`se zobrazí v případě podmínku `(m > 10)` vyhodnocena jako false.</span><span class="sxs-lookup"><span data-stu-id="85403-121">`Result2` appears if the condition `(m > 10)` evaluates to false.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85403-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="85403-122">Example</span></span>  
 <span data-ttu-id="85403-123">V následujícím příkladu, zadejte znak z klávesnice, a program používá vnořený `if` příkaz k určení, zda vstupní znak je znak abecedy.</span><span class="sxs-lookup"><span data-stu-id="85403-123">In the following example, you enter a character from the keyboard, and the program uses a nested `if` statement to determine whether the input character is an alphabetic character.</span></span> <span data-ttu-id="85403-124">Pokud vstupní znak je znak abecedy, program zkontroluje, zda vstupní znak je malá nebo velká písmena.</span><span class="sxs-lookup"><span data-stu-id="85403-124">If the input character is an alphabetic character, the program checks whether the input character is lowercase or uppercase.</span></span> <span data-ttu-id="85403-125">Zobrazí se zpráva, pro každý případ.</span><span class="sxs-lookup"><span data-stu-id="85403-125">A message appears for each case.</span></span>  
  
 [!code-csharp[csrefKeywordsSelection#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_4.cs)]  
  
## <a name="example"></a><span data-ttu-id="85403-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="85403-126">Example</span></span>  
 <span data-ttu-id="85403-127">Také lze vnořit `if` příkaz uvnitř jiného bloku, jak ukazuje následující částečné kódu.</span><span class="sxs-lookup"><span data-stu-id="85403-127">You also can nest an `if` statement inside an else block, as the following partial code shows.</span></span> <span data-ttu-id="85403-128">Příklad vnoří `if` příkazy uvnitř dva else bloky a pak jeden blok.</span><span class="sxs-lookup"><span data-stu-id="85403-128">The example nests `if` statements inside two else blocks and one then block.</span></span> <span data-ttu-id="85403-129">Komentáře zadejte, které podmínky jsou true nebo false v každém bloku.</span><span class="sxs-lookup"><span data-stu-id="85403-129">The comments specify which conditions are true or false in each block.</span></span>  
  
 [!code-csharp[csrefKeywordsSelection#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_5.cs)]  
  
## <a name="example"></a><span data-ttu-id="85403-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="85403-130">Example</span></span>  
 <span data-ttu-id="85403-131">Následující příklad určuje, zda je vstupní znak malé písmeno, velké písmeno nebo číslo.</span><span class="sxs-lookup"><span data-stu-id="85403-131">The following example determines whether an input character is a lowercase letter, an uppercase letter, or a number.</span></span> <span data-ttu-id="85403-132">Pokud jsou všechny tři podmínky false, není znak alfanumerický znak.</span><span class="sxs-lookup"><span data-stu-id="85403-132">If all three conditions are false, the character isn’t an alphanumeric character.</span></span> <span data-ttu-id="85403-133">V příkladu se zobrazí zprávu pro každý případ.</span><span class="sxs-lookup"><span data-stu-id="85403-133">The example displays a message for each case.</span></span>  
  
 [!code-csharp[csrefKeywordsSelection#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_6.cs)]  
  
 <span data-ttu-id="85403-134">Stejně jako příkaz v else bloku nebo pak bloku může být libovolný platný příkaz, můžete použít libovolný platný logický výraz pro podmínku.</span><span class="sxs-lookup"><span data-stu-id="85403-134">Just as a statement in the else block or the then block can be any valid statement, you can use any valid Boolean expression for the condition.</span></span> <span data-ttu-id="85403-135">Logické operátory můžete použít jako [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md), [ & ](../../../csharp/language-reference/operators/and-operator.md), [&#124; &#124;](../../../csharp/language-reference/operators/conditional-or-operator.md), [&#124;](../../../csharp/language-reference/operators/or-operator.md) a [!](../../../csharp/language-reference/operators/logical-negation-operator.md)</span><span class="sxs-lookup"><span data-stu-id="85403-135">You can use logical operators such as [&&](../../../csharp/language-reference/operators/conditional-and-operator.md), [&](../../../csharp/language-reference/operators/and-operator.md), [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md), [&#124;](../../../csharp/language-reference/operators/or-operator.md) and [!](../../../csharp/language-reference/operators/logical-negation-operator.md)</span></span> <span data-ttu-id="85403-136">Chcete-li složené podmínky.</span><span class="sxs-lookup"><span data-stu-id="85403-136">to make compound conditions.</span></span> <span data-ttu-id="85403-137">Následující kód ukazuje příklady.</span><span class="sxs-lookup"><span data-stu-id="85403-137">The following code shows examples.</span></span>  
  
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
  
## <a name="c-language-specification"></a><span data-ttu-id="85403-138">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="85403-138">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="85403-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="85403-139">See Also</span></span>  
 [<span data-ttu-id="85403-140">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="85403-140">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="85403-141">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="85403-141">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="85403-142">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="85403-142">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="85403-143">?: – Operátor</span><span class="sxs-lookup"><span data-stu-id="85403-143">?: Operator</span></span>](../../../csharp/language-reference/operators/conditional-operator.md)  
 [<span data-ttu-id="85403-144">if-else – příkaz (C++)</span><span class="sxs-lookup"><span data-stu-id="85403-144">if-else Statement (C++)</span></span>](/cpp/cpp/if-else-statement-cpp)  
 [<span data-ttu-id="85403-145">přepínače</span><span class="sxs-lookup"><span data-stu-id="85403-145">switch</span></span>](../../../csharp/language-reference/keywords/switch.md)
