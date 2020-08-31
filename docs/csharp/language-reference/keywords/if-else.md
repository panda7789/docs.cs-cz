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
# <a name="if-else-c-reference"></a>if-else (Referenční dokumentace jazyka C#)

`if`Příkaz určuje, který příkaz se má spustit na základě hodnoty logického výrazu. V následujícím příkladu `bool` `condition` je proměnná nastavena na `true` a poté vrácena do `if` příkazu. Výstup je `The variable is set to true.`.

[!code-csharp[csrefKeywordsSelection#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#1)]

Příklady v tomto tématu můžete spustit tak, že je umístíte do `Main` metody konzolové aplikace.

`if`Příkaz v jazyce C# může přijmout dva formuláře, jak ukazuje následující příklad.

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

V `if-else` příkazu, pokud se `condition` vyhodnotí jako true, `then-statement` spustí se. Pokud `condition` je hodnota false, `else-statement` spuštění. Vzhledem k tomu `condition` , že nemohou být současně true a false, nemůže být `then-statement` `else-statement` příkaz a `if-else` příkazu nikdy spouštěn současně. Po `then-statement` `else-statement` spuštění nebo je ovládací prvek převeden na další příkaz po `if` příkazu.

V `if` příkazu, který neobsahuje `else` příkaz, pokud `condition` je true, `then-statement` spustí se. Pokud `condition` je hodnota false, ovládací prvek bude převeden na další příkaz po `if` příkazu.

Jak `then-statement` a `else-statement` může sestávat z jediného příkazu nebo více příkazů, které jsou uzavřeny v závorkách ( `{}` ). V případě jednoho příkazu jsou složené závorky volitelné, ale doporučené.

Příkazy nebo příkazy v `then-statement` a `else-statement` mohou být libovolného druhu, včetně jiného `if` příkazu vnořeného uvnitř původního `if` příkazu. Ve vnořených `if` příkazech `else` patří každá klauzule k poslednímu `if` , který nemá odpovídající `else` . V následujícím příkladu `Result1` se zobrazí, pokud je `m > 10` a `n > 20` vyhodnocen na hodnotu true. Pokud `m > 10` má hodnotu true `n > 20` , ale je false, `Result2` zobrazí se.

[!code-csharp[csrefKeywordsSelection#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#2)]

Pokud místo toho chcete zobrazit, `Result2` Pokud `(m > 10)` je false, můžete zadat toto přidružení pomocí složených závorek pro vytvoření začátku a konce vnořeného `if` příkazu, jak ukazuje následující příklad.

[!code-csharp[csrefKeywordsSelection#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#3)]

`Result2` zobrazí se, pokud je podmínka `(m > 10)` vyhodnocena jako NEPRAVDA.

## <a name="example"></a>Příklad

V následujícím příkladu zadáte znak z klávesnice a program použije vnořený `if` příkaz k určení, zda je vstupním znakem abecední znak. Pokud je vstupním znakem abecední znak, program zkontroluje, zda je vstupní znak malý nebo malý. Pro každý případ se zobrazí zpráva.

[!code-csharp[csrefKeywordsSelection#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#4)]

## <a name="example"></a>Příklad

Příkaz lze také vnořit `if` do bloku else, jak ukazuje následující částečný kód. Příklad vnořovat `if` příkazy uvnitř dvou bloků else a jeden blok po bloku. Komentáře určují, které podmínky jsou v každém bloku pravdivé nebo nepravdivé.

[!code-csharp[csrefKeywordsSelection#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#5)]

## <a name="example"></a>Příklad

Následující příklad určuje, zda je vstupní znak malé písmeno, velké písmeno nebo číslo. Pokud jsou všechny tři podmínky false, znak není alfanumerický znak. V příkladu se zobrazí zpráva pro každý případ.

[!code-csharp[csrefKeywordsSelection#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#6)]

Stejně jako příkaz v bloku else nebo blok, který může být libovolným platným příkazem, můžete pro podmínku použít libovolný platný logický výraz. Pomocí [logických operátorů](../operators/boolean-logical-operators.md) , jako jsou,,, `!` `&&` `||` `&` , `|` a, lze `^` provádět složené podmínky. Následující kód ukazuje příklady.

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

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [?: – Operátor](../operators/conditional-operator.md)
- [if-else – příkaz (C++)](/cpp/cpp/if-else-statement-cpp)
- [přepnutí](switch.md)
