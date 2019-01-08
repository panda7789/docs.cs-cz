---
title: if-else – C# odkaz
ms.custom: seodec18
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
ms.openlocfilehash: ccb783d8d478b14078ab6fe09f12e480c12ac06b
ms.sourcegitcommit: d09c77414e9e4fc72c79b04deee7a756a120674e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2019
ms.locfileid: "54084768"
---
# <a name="if-else-c-reference"></a>if-else (Referenční dokumentace jazyka C#)

`if` Příkaz určuje, který příkaz ke spuštění na základě hodnoty logického výrazu. V následujícím příkladu `bool` proměnné `condition` je nastavena na `true` a pak se změnami `if` příkaz. Výstup je `The variable is set to true.`.

[!code-csharp[csrefKeywordsSelection#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#1)]

V příkladech v tomto tématu můžete spustit tak, že je `Main` metoda Konzolová aplikace.

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

V `if-else` příkazu, pokud `condition` vyhodnotí jako true, `then-statement` běží. Pokud `condition` má hodnotu false, `else-statement` běží. Protože `condition` nemůže být zároveň true a false, `then-statement` a `else-statement` z `if-else` příkazu můžete oba nespouštět. Po `then-statement` nebo `else-statement` spuštění, ovládací prvek bude převeden na příkaz následující po `if` příkazu.

V `if` příkaz, který neobsahuje `else` příkazu, pokud `condition` má hodnotu true, `then-statement` běží. Pokud `condition` má hodnotu false, je kontrola předána dalšímu příkazu po `if` příkazu.

Jak `then-statement` a `else-statement` se může skládat z jednoho příkazu nebo více příkazů, které jsou uzavřeny ve složených závorkách (`{}`). Pro jeden příkaz složené závorky jsou nepovinné, ale doporučený.

Příkaz nebo příkazy v `then-statement` a `else-statement` mohou být jakéhokoli typu, včetně jiného `if` příkaz vnořit do původní `if` příkazu. Ve vnořené `if` příkazy, každý `else` klauzule patří na poslední `if` , který nemá odpovídající `else`. V následujícím příkladu `Result1` se zobrazí, pokud obě `m > 10` a `n > 20` vyhodnocen na hodnotu true. Pokud `m > 10` má hodnotu true, ale `n > 20` má hodnotu false, `Result2` se zobrazí.

[!code-csharp[csrefKeywordsSelection#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#2)]

Pokud místo toho chcete `Result2` se zobrazí, když `(m > 10)` má hodnotu false, můžete zadat toto přidružení pomocí závorek k navázání začátku a konce ve vnořeném `if` příkaz, jak ukazuje následující příklad.

[!code-csharp[csrefKeywordsSelection#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#3)]

`Result2` se zobrazí, pokud podmínka `(m > 10)` nevyhodnotí jako false.

## <a name="example"></a>Příklad

V následujícím příkladu, zadejte znak z klávesnice a program používá vnořený `if` příkaz k určení, zda je vstupní znak abecední znak. Pokud vstupní znak je znak abecedy, program zkontroluje, zda je vstupní znak malé nebo velké písmeno. Zobrazí se zpráva pro každý případ.

[!code-csharp[csrefKeywordsSelection#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#4)]

## <a name="example"></a>Příklad

Také můžete vnořit `if` výroku uvnitř jiného bloku, jak ukazuje následující kód částečné. Příklad používá vnořené `if` příkazy uvnitř jiného dvou bloků a pak jeden blok. Komentáře zadejte podmínky, které jsou true nebo false v každém bloku.

[!code-csharp[csrefKeywordsSelection#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#5)]

## <a name="example"></a>Příklad

Následující příklad určuje, zda je vstupní znak malé písmeno, velké písmeno nebo číslo. Pokud jsou všechny tři podmínky hodnotu false, není znak alfanumerický znak. V příkladu se zobrazí zprávu pro každý případ.

[!code-csharp[csrefKeywordsSelection#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#6)]

Stejně jako příkaz v jiného bloku nebo bloku pak může být libovolný platný příkaz, můžete použít libovolný platný výraz logickou podmínku. Můžete například použít logické operátory [ && ](../operators/conditional-and-operator.md), [ & ](../operators/and-operator.md), [ &#124; &#124; ](../operators/conditional-or-operator.md), [ &#124; ](../operators/or-operator.md) a [!](../operators/logical-negation-operator.md) Chcete-li složených podmínek. Následující kód ukazuje příklady.

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

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../index.md)  
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)  
- [Klíčová slova jazyka C#](index.md)  
- [?: – operátor](../operators/conditional-operator.md)  
- [if-else – příkaz (C++)](/cpp/cpp/if-else-statement-cpp)  
- [switch](switch.md)  
