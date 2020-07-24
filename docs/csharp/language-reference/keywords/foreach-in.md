---
title: Příkaz C# foreach
ms.date: 07/22/2020
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 4af431d29e538c1516efeaad3008eaa3b2229ece
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104240"
---
# <a name="foreach-in-c-reference"></a>foreach, in (Referenční dokumentace jazyka C#)

`foreach`Příkaz spustí příkaz nebo blok příkazů pro každý prvek v instanci typu, který implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> rozhraní nebo, jak ukazuje následující příklad:

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="1" interactive="try-dotnet-method" :::

`foreach`Příkaz není omezen na tyto typy. Můžete ji použít s instancí libovolného typu, který splňuje následující podmínky:

- typ má metodu public bez parametrů `GetEnumerator` , jejíž návratový typ je buď třída, struktura, nebo typ rozhraní.
- návratový typ `GetEnumerator` metody má veřejnou `Current` vlastnost a metodu public bez parametrů, `MoveNext` jejíž návratový typ je <xref:System.Boolean> .

Následující příklad používá `foreach` příkaz s instancí <xref:System.Span%601?displayProperty=nameWithType> typu, který neimplementuje žádná rozhraní:

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="2" :::

Počínaje jazykem C# 7,3, pokud vlastnost enumerátoru `Current` vrátí [návratovou hodnotu odkazu](ref.md#reference-return-values) ( `ref T` kde `T` je typ prvku kolekce), můžete deklarovat proměnnou iterace pomocí `ref` `ref readonly` modifikátoru nebo, jak ukazuje následující příklad:

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="RefSpan" :::

Počínaje jazykem C# 8,0 můžete použít `await foreach` příkaz pro využívání asynchronního datového proudu dat, tedy typu kolekce, který implementuje <xref:System.Collections.Generic.IAsyncEnumerable%601> rozhraní. Každá iterace smyčky může být pozastavena, zatímco je další prvek načten asynchronně. Následující příklad ukazuje, jak použít `await foreach` příkaz:

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="AwaitForeach" :::

Ve výchozím nastavení jsou prvky Stream zpracovávány v zachyceném kontextu. Pokud chcete zakázat zachycování kontextu, použijte <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> metodu rozšíření. Další informace o kontextech synchronizace a záznamech aktuálního kontextu naleznete v tématu [spotřebovávání asynchronního vzoru založeného na úlohách](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md). Další informace o asynchronních datových proudech naleznete v části [asynchronní datové proudy](../../whats-new/csharp-8.md#asynchronous-streams) [v článku novinky v C# 8,0](../../whats-new/csharp-8.md) .

V jakémkoli bodě `foreach` bloku příkazu můžete přerušit smyčku pomocí příkazu [Break](break.md) nebo krokovat s další iterací ve smyčce pomocí příkazu [Continue](continue.md) . Můžete také ukončit `foreach` smyčku příkazy [goto](goto.md), [return](return.md)nebo [throw](throw.md) .

Pokud `foreach` je příkaz použit na `null` , <xref:System.NullReferenceException> je vyvolána. Pokud je zdrojová kolekce `foreach` příkazu prázdná, tělo `foreach` smyčky se neprovede a přeskočí.

## <a name="type-of-an-iteration-variable"></a>Typ proměnné iterace

Klíčové slovo lze použít `var` k umožnění kompilátoru odvodit typ iterační proměnné v `foreach` příkazu, jak ukazuje následující kód:

```csharp
foreach (var item in collection) { }
```

Můžete také explicitně zadat typ proměnné iterace, jak ukazuje následující kód:

```csharp
IEnumerable<T> collection = new T[5];
foreach (V item in collection) { }
```

V předchozím formuláři `T` musí být typ elementu kolekce implicitně nebo explicitně převoditelné na typ `V` proměnné iterace. Pokud explicitní převod z `T` na `V` neuspěje v době běhu, `foreach` příkaz vyvolá výjimku <xref:System.InvalidCastException> . Například pokud `T` je typ třídy, který není zapečetěný, `V` může být libovolný typ rozhraní, a to i ten, který `T` neimplementuje. V době běhu může být typ elementu kolekce ten, který je odvozen z `T` a skutečně implementuje `V` . V takovém případě <xref:System.InvalidCastException> je vyvolána výjimka.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v oddílu [foreach příkazu](~/_csharplang/spec/statements.md#the-foreach-statement) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Klíčová slova jazyka C#](index.md)
- [Použití příkazu foreach s poli](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [for – příkaz](for.md)
