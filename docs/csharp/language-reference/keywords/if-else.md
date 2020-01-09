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
# <a name="if-else-c-reference"></a>if-else (Referenční dokumentace jazyka C#)

Příkaz `if` identifikuje, který příkaz se má spustit na základě hodnoty logického výrazu. V následujícím příkladu je proměnná `bool` `condition` nastavená na `true` a pak se vrátila do příkazu `if`. Výstup je `The variable is set to true.`.

[!code-csharp[csrefKeywordsSelection#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#1)]

Příklady v tomto tématu můžete spustit tak, že je umístíte do metody `Main` konzolové aplikace.

Příkaz `if` v C# nástroji může přijmout dvě formy, jak ukazuje následující příklad.

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

Pokud se v příkazu `if-else` `condition` vyhodnotí jako true, `then-statement` se spustí. Pokud je `condition` false, `else-statement` se spustí. Vzhledem k tomu, že `condition` nemůže být současně true a false, `then-statement` a `else-statement` příkazu `if-else` nikdy nejdou spustit současně. Po `then-statement` nebo spuštění `else-statement` je ovládací prvek převeden na další příkaz po příkazu `if`.

V příkazu `if`, který neobsahuje příkaz `else`, pokud `condition` má hodnotu true, `then-statement` se spustí. Pokud je `condition` false, ovládací prvek se převede na další příkaz po příkazu `if`.

`then-statement` i `else-statement` se mohou skládat z jednoho příkazu nebo více příkazů, které jsou uzavřeny v závorkách (`{}`). V případě jednoho příkazu jsou složené závorky volitelné, ale doporučené.

Příkaz nebo příkazy v `then-statement` a `else-statement` mohou být libovolného druhu, včetně jiného příkazu `if` vnořeného v původním příkazu `if`. Ve vnořených příkazech `if` každá klauzule `else` patří do posledního `if`, který nemá odpovídající `else`. V následujícím příkladu se `Result1` zobrazí, pokud jsou obě `m > 10` a `n > 20` vyhodnoceny jako true. Pokud je `m > 10` true, ale `n > 20` je false, `Result2` se zobrazí.

[!code-csharp[csrefKeywordsSelection#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#2)]

Pokud místo toho chcete, aby se `Result2` zobrazovaly, když `(m > 10)` je false, můžete zadat toto přidružení pomocí složených závorek pro vytvoření začátku a konce vnořeného příkazu `if`, jak ukazuje následující příklad.

[!code-csharp[csrefKeywordsSelection#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#3)]

`Result2` se zobrazí, pokud je podmínka `(m > 10)` vyhodnocena jako NEPRAVDA.

## <a name="example"></a>Příklad

V následujícím příkladu zadáte znak z klávesnice a program použije vnořený příkaz `if` k určení, zda je vstupním znakem abecední znak. Pokud je vstupním znakem abecední znak, program zkontroluje, zda je vstupní znak malý nebo malý. Pro každý případ se zobrazí zpráva.

[!code-csharp[csrefKeywordsSelection#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#4)]

## <a name="example"></a>Příklad

Můžete také vnořit příkaz `if` do bloku else, jak ukazuje následující částečný kód. Příklad vnořování `if` příkazy uvnitř dvou bloků else a jednom bloku. Komentáře určují, které podmínky jsou v každém bloku pravdivé nebo nepravdivé.

[!code-csharp[csrefKeywordsSelection#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#5)]

## <a name="example"></a>Příklad

Následující příklad určuje, zda je vstupní znak malé písmeno, velké písmeno nebo číslo. Pokud jsou všechny tři podmínky false, znak není alfanumerický znak. V příkladu se zobrazí zpráva pro každý případ.

[!code-csharp[csrefKeywordsSelection#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#6)]

Stejně jako příkaz v bloku else nebo blok, který může být libovolným platným příkazem, můžete pro podmínku použít libovolný platný logický výraz. Složené podmínky můžete provádět pomocí [logických operátorů](../operators/boolean-logical-operators.md) , jako jsou `!`, `&&`, `||`, `&`, `|`a `^`. Následující kód ukazuje příklady.

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

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [?: – operátor](../operators/conditional-operator.md)
- [if-else – příkaz (C++)](/cpp/cpp/if-else-statement-cpp)
- [switch](switch.md)
