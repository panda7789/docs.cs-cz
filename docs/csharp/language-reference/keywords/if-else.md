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
# <a name="if-else-c-reference"></a>if-else (Referenční dokumentace jazyka C#)

Příkaz `if` identifikuje, který příkaz má být spuštěn na základě hodnoty logického výrazu. V následujícím příkladu `bool` `condition` je proměnná nastavena `true` na `if` a poté v příkazu zaškrtnuta. Výstup je `The variable is set to true.`.

[!code-csharp[csrefKeywordsSelection#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#1)]

Příklady v tomto tématu můžete spustit `Main` tak, že je umístíte do metody konzolové aplikace.

Příkaz `if` v C# může mít dvě formy, jak ukazuje následující příklad.

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

V `if-else` prohlášení, `condition` pokud vyhodnotí `then-statement` true, spustí. Pokud `condition` je false, `else-statement` běží. Protože `condition` nemůže být současně pravdivé a `then-statement` nepravdivé, `else-statement` a `if-else` prohlášení nemůže nikdy oba spustit. Po `then-statement` `else-statement` spuštění nebo ovládací prvek je převedena na `if` další příkaz po příkazu.

V `if` prohlášení, které neobsahuje `else` příkaz, `condition` pokud je `then-statement` true, spustí. Pokud `condition` je false, ovládací prvek je převedena na další příkaz po příkazu. `if`

`then-statement` A `else-statement` může se skládat z jednoho příkazu nebo více příkazů, které jsou uzavřeny v závorkách (`{}`). Pro jeden příkaz jsou závorky volitelné, ale doporučené.

Příkaz nebo příkazy `then-statement` v `else-statement` a může být jakéhokoli `if` druhu, včetně `if` jiného příkazu vnořené uvnitř původní ho příkazu. `if` V nosných `else` příkazech patří `if` každá klauzule poslední `else`klauzuli, která nemá odpovídající . V následujícím příkladu se `m > 10` `n > 20` zobrazí, `Result1` pokud oba a vyhodnotit na true. Pokud `m > 10` je `n > 20` pravda, `Result2` ale je nepravdivé, se objeví.

[!code-csharp[csrefKeywordsSelection#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#2)]

Pokud se místo `Result2` toho chcete `(m > 10)` zobrazit, když je false, můžete určit, že přidružení pomocí `if` závorek k vytvoření začátku a konce vnořený příkaz, jak ukazuje následující příklad.

[!code-csharp[csrefKeywordsSelection#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#3)]

`Result2`pokud se `(m > 10)` stav vyhodnotí jako nepravdivý.

## <a name="example"></a>Příklad

V následujícím příkladu zadáte znak z klávesnice a program použije `if` vnořený příkaz k určení, zda je vstupní znak abecední znak. Pokud je vstupní znak abecední znak, program zkontroluje, zda je vstupní znak malá nebo velká. Pro každý případ se zobrazí zpráva.

[!code-csharp[csrefKeywordsSelection#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#4)]

## <a name="example"></a>Příklad

Můžete také vnořit `if` příkaz uvnitř bloku else, jak ukazuje následující částečný kód. Příklad vnoří příkazy `if` uvnitř dva bloky else a jeden pak blokovat. Komentáře určují, které podmínky jsou v každém bloku pravdivé nebo nepravdivé.

[!code-csharp[csrefKeywordsSelection#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#5)]

## <a name="example"></a>Příklad

Následující příklad určuje, zda je vstupní znak malé písmeno, velké písmeno nebo číslo. Pokud jsou všechny tři podmínky false, znak není alfanumerický znak. Příklad zobrazí zprávu pro každý případ.

[!code-csharp[csrefKeywordsSelection#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#6)]

Stejně jako příkaz v bloku else nebo pak blok může být libovolný platný příkaz, můžete použít libovolný platný logický výraz pro podmínku. Můžete použít [logické operátory,](../operators/boolean-logical-operators.md) například `!`, `&&` `||`, `&` `|`, a `^` vytvořit složené podmínky. Následující kód ukazuje příklady.

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

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](index.md)
- [?: Operátor](../operators/conditional-operator.md)
- [if-else – příkaz (C++)](/cpp/cpp/if-else-statement-cpp)
- [Přepnout](switch.md)
