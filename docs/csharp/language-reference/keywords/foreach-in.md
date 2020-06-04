---
title: Příkaz C# foreach
ms.date: 06/03/2020
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 1645a246c9feee2a92c0d4e4bbeda47f0afde7d9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401885"
---
# <a name="foreach-in-c-reference"></a>foreach, in (Referenční dokumentace jazyka C#)

`foreach`Příkaz spustí příkaz nebo blok příkazů pro každý prvek v instanci typu, který implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> rozhraní nebo. `foreach`Příkaz není omezen na tyto typy a lze jej použít na instanci libovolného typu, který splňuje následující podmínky:

- má veřejnou metodu bez parametrů `GetEnumerator` , jejíž návratový typ je buď třída, struktura, nebo typ rozhraní.
- návratový typ `GetEnumerator` metody má veřejnou `Current` vlastnost a metodu public bez parametrů, `MoveNext` jejíž návratový typ je <xref:System.Boolean> .

Ve většině případů používá `foreach` iteraci `IEnumerable<T>` výraz, ve kterém je každý element typu `T` . Prvky však mohou být libovolného typu, který má implicitní nebo explicitní převod z typu `Current` Vlastnosti. Pokud se `Current` vlastnost vrátí `SomeType` , může být typ prvků:

- Jakékoli základní třídy `SomeType` .
- Jakákoli rozhraní implementovaná `SomeType` .

Kromě toho, pokud `SomeType` je `class` nebo `interface` a nikoli `sealed` , může typ prvků zahrnovat:

- Jakýkoli typ odvozený z `SomeType` .
- Jakékoli libovolné rozhraní. Jakékoli rozhraní je povoleno, protože jakékoli rozhraní může být implementováno třídou odvozenou z nebo implementací `SomeType` .

Proměnnou iterace můžete deklarovat pomocí libovolného typu, který odpovídá předchozím pravidlům. Pokud převod z `SomeType` na typ proměnné iterace vyžaduje explicitní přetypování, může tato operace vyvolat výjimku, <xref:System.InvalidCastException> když se převod nezdařil.

Počínaje jazykem C# 7,3, pokud vlastnost enumerátoru `Current` vrátí [návratovou hodnotu odkazu](ref.md#reference-return-values) ( `ref T` kde `T` je typ prvku kolekce), můžete proměnnou iterace deklarovat pomocí `ref` `ref readonly` modifikátoru or.

Počínaje jazykem C# 8,0 `await` může být operátor aplikován na `foreach` příkaz, když typ kolekce implementuje <xref:System.Collections.Generic.IAsyncEnumerable%601> rozhraní. Každá iterace smyčky může být pozastavena, zatímco je další prvek načten asynchronně. Ve výchozím nastavení jsou prvky Stream zpracovávány v zachyceném kontextu. Pokud chcete zakázat zachycování kontextu, použijte <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> metodu rozšíření. Další informace o kontextech synchronizace a zaznamenávání aktuálního kontextu naleznete v článku o [využívání asynchronního vzoru založeného na úlohách](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).

V jakémkoli bodě `foreach` bloku příkazu můžete přerušit smyčku pomocí příkazu [Break](break.md) nebo krokovat s další iterací ve smyčce pomocí příkazu [Continue](continue.md) . Můžete také ukončit `foreach` smyčku příkazy [goto](goto.md), [return](return.md)nebo [throw](throw.md) .

Pokud `foreach` je příkaz použit na `null` , <xref:System.NullReferenceException> je vyvolána. Pokud je zdrojová kolekce `foreach` příkazu prázdná, tělo `foreach` smyčky se neprovede a přeskočí.

## <a name="examples"></a>Příklady

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Následující příklad ukazuje použití `foreach` příkazu s instancí <xref:System.Collections.Generic.List%601> typu, který implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní:

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="1" interactive="try-dotnet-method" :::

Následující příklad používá `foreach` příkaz s instancí <xref:System.Span%601?displayProperty=nameWithType> typu, který neimplementuje žádná rozhraní:

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="2" :::

Následující příklad používá `ref` proměnnou iterace k nastavení hodnoty každé položky v poli stackalloc. `ref readonly`Verze projde kolekci pro tisk všech hodnot. `readonly`Deklarace používá implicitní deklaraci lokální proměnné. Deklarace implicitních proměnných lze použít s `ref` `ref readonly` deklaracemi nebo, jako lze explicitně napsat deklarace proměnných.

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="RefSpan" :::

Následující příklad používá `await foreach` k iteraci kolekce, která generuje každý prvek asynchronně:

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="AwaitForeach"  :::

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v oddílu [foreach příkazu](~/_csharplang/spec/statements.md#the-foreach-statement) [specifikace jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction).

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Použití příkazu foreach s poli](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [for – příkaz](for.md)
