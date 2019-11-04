---
title: C#příkaz foreach
ms.date: 05/17/2019
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 9c1521f39dea72b51801a81b13e8a0203956731c
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422796"
---
# <a name="foreach-in-c-reference"></a>foreach, in (C# referenční)

Příkaz `foreach` spustí příkaz nebo blok příkazů pro každý prvek v instanci typu, který implementuje rozhraní <xref:System.Collections.IEnumerable?displayProperty=nameWithType> nebo <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>. Příkaz `foreach` není omezen na tyto typy a lze jej použít na instanci libovolného typu, který splňuje následující podmínky:

- má veřejnou `GetEnumerator` metodu bez parametrů, jejíž návratový typ je buď třída, struktura, nebo typ rozhraní.
- návratový typ metody `GetEnumerator` má vlastnost Public `Current` a veřejnou metodu `MoveNext` bez parametrů, jejíž návratový typ je <xref:System.Boolean>.

Počínaje C# 7,3, pokud vlastnost `Current` čítače vrátí [návratovou hodnotu odkazu](ref.md#reference-return-values) (`ref T` kde `T` je typ prvku kolekce), můžete proměnnou iterace deklarovat pomocí modifikátoru `ref` nebo `ref readonly`.

V jakémkoli okamžiku v rámci bloku příkazu `foreach` lze rozdělit smyčku pomocí příkazu [Break](break.md) nebo krokovat s další iterací ve smyčce pomocí příkazu [Continue](continue.md) . Můžete také ukončit `foreach` smyčkou příkazy [goto](goto.md), [return](return.md)nebo [throw](throw.md) .

Pokud je pro `null`použit příkaz `foreach`, je vyvolána <xref:System.NullReferenceException>. Pokud je zdrojová kolekce příkazu `foreach` prázdná, tělo `foreach` smyčky se neprovede a přeskočí.

## <a name="examples"></a>Příklady

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Následující příklad ukazuje použití příkazu `foreach` s instancí typu <xref:System.Collections.Generic.List%601>, která implementuje rozhraní <xref:System.Collections.Generic.IEnumerable%601>:

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

V dalším příkladu se používá příkaz `foreach` s instancí typu <xref:System.Span%601?displayProperty=nameWithType>, která neimplementuje žádná rozhraní:

[!code-csharp[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

Následující příklad používá proměnnou iterace `ref` k nastavení hodnoty každé položky v poli stackalloc. Verze `ref readonly` provede iteraci kolekce pro tisk všech hodnot. Deklarace `readonly` používá implicitní deklaraci lokální proměnné. Deklarace implicitních proměnných lze použít s deklaracemi `ref` nebo `ref readonly`, jako lze explicitně napsat deklarace proměnných.

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [příkazu foreach](~/_csharplang/spec/statements.md#the-foreach-statement) [ C# specifikace jazyka](/dotnet/csharp/language-reference/language-specification/introduction).

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Použití příkazu foreach s poli](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [příkaz for](for.md)
