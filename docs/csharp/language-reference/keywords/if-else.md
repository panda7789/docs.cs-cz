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
# <a name="if-else-c-reference"></a>if-else (Referenční dokumentace jazyka C#)
`if` Příkaz identifikuje, který příkaz ke spuštění na základě hodnoty z `Boolean` výraz. V následujícím příkladu `Boolean` proměnné `result` je nastaven na `true` a pak vrátit se změnami `if` příkaz. Výstupem je `The condition is true`.  
  
 [!code-csharp[csrefKeywordsSelection#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_1.cs)]  
  
 V příkladech v tomto tématu můžete spustit tím, že je `Main` metoda konzolovou aplikaci.  
  
 `if` Příkaz v jazyce C# může mít dvě formy, jak ukazuje následující příklad.  
  
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
  
 V `if-else` příkaz, pokud `condition` vyhodnotí jako true, `then-statement` běží. Pokud `condition` je nastavena hodnota false, `else-statement` běží. Protože `condition` nemůže být zároveň true a false, `then-statement` a `else-statement` z `if-else` příkaz nikdy obě spuštěním. Po `then-statement` nebo `else-statement` spustí, řízení se přenese do další příkaz po `if` příkaz.  
  
 V `if` příkaz, který neobsahuje `else` příkaz, pokud `condition` má hodnotu true, `then-statement` běží. Pokud `condition` je nastavena hodnota false, ovládací prvek je přenesen na další příkaz po `if` příkaz.  
  
 Jak `then-statement` a `else-statement` se může skládat z jedné příkaz nebo více příkazů, které jsou uzavřené do složených závorek (`{}`). Pro jediný příkaz složené závorky jsou volitelné, ale doporučené.  
  
 Příkaz nebo příkazy v `then-statement` a `else-statement` může být libovolného typu, včetně jiné `if` příkaz vnořit původní `if` příkaz. Ve vnořených `if` příkazy, každý `else` klauzule patří na poslední `if` , nemá odpovídající `else`. V následujícím příkladu `Result1` se zobrazí, pokud obě `m > 10` a `n > 20` vyhodnotit na hodnotu true. Pokud `m > 10` hodnotu true, ale `n > 20` je nastavena hodnota false, `Result2` se zobrazí.  
  
 [!code-csharp[csrefKeywordsSelection#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_2.cs)]  
  
 Pokud chcete místo toho `Result2` se objeví při `(m > 10)` je nastavena hodnota false, můžete toto přidružení pomocí složené závorky k vytvoření počáteční a koncová vnořeného `if` příkaz, jak ukazuje následující příklad.  
  
 [!code-csharp[csrefKeywordsSelection#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_3.cs)]  
  
 `Result2`se zobrazí v případě podmínku `(m > 10)` vyhodnocena jako false.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu, zadejte znak z klávesnice, a program používá vnořený `if` příkaz k určení, zda vstupní znak je znak abecedy. Pokud vstupní znak je znak abecedy, program zkontroluje, zda vstupní znak je malá nebo velká písmena. Zobrazí se zpráva, pro každý případ.  
  
 [!code-csharp[csrefKeywordsSelection#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_4.cs)]  
  
## <a name="example"></a>Příklad  
 Také lze vnořit `if` příkaz uvnitř jiného bloku, jak ukazuje následující částečné kódu. Příklad vnoří `if` příkazy uvnitř dva else bloky a pak jeden blok. Komentáře zadejte, které podmínky jsou true nebo false v každém bloku.  
  
 [!code-csharp[csrefKeywordsSelection#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_5.cs)]  
  
## <a name="example"></a>Příklad  
 Následující příklad určuje, zda je vstupní znak malé písmeno, velké písmeno nebo číslo. Pokud jsou všechny tři podmínky false, není znak alfanumerický znak. V příkladu se zobrazí zprávu pro každý případ.  
  
 [!code-csharp[csrefKeywordsSelection#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_6.cs)]  
  
 Stejně jako příkaz v else bloku nebo pak bloku může být libovolný platný příkaz, můžete použít libovolný platný logický výraz pro podmínku. Logické operátory můžete použít jako [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md), [ & ](../../../csharp/language-reference/operators/and-operator.md), [&#124; &#124;](../../../csharp/language-reference/operators/conditional-or-operator.md), [&#124;](../../../csharp/language-reference/operators/or-operator.md) a [!](../../../csharp/language-reference/operators/logical-negation-operator.md) Chcete-li složené podmínky. Následující kód ukazuje příklady.  
  
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
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [?: – Operátor](../../../csharp/language-reference/operators/conditional-operator.md)  
 [if-else – příkaz (C++)](/cpp/cpp/if-else-statement-cpp)  
 [přepínače](../../../csharp/language-reference/keywords/switch.md)
