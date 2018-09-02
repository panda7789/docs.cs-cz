---
title: Příkaz foreach jazyka C#
ms.date: 06/29/2018
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: d84c68eb102d55b31ba20a6b6b5c01b96963924d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43405847"
---
# <a name="foreach-in-c-reference"></a>foreach, in (referenční dokumentace jazyka C#)

`foreach` Příkaz opakuje příkaz nebo blok příkazů pro každý prvek v instanci typu, který implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> nebo <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> rozhraní. `foreach` Příkaz není omezena pouze na tyto typy které můžou uplatnit na instanci typu, který splňuje následující podmínky:

- nemá veřejný konstruktor bez parametrů `GetEnumerator` metoda, jejíž návratový typ je třída, struktura nebo typ rozhraní
- Návratový typ `GetEnumerator` metoda má veřejnou `Current` vlastnost a veřejný konstruktor bez parametrů `MoveNext` metoda, jejíž návratový typ je <xref:System.Boolean>.

Na libovolný bod v rámci `foreach` blok příkazů, můžete přerušit ze smyčky s použitím [přerušení](break.md) příkazu nebo kroku na následující iteraci ve smyčce pomocí [pokračovat](continue.md) příkazu. Také můžete ukončit `foreach` smyčky pomocí [goto](goto.md), [vrátit](return.md), nebo [throw](throw.md) příkazy.

## <a name="examples"></a>Příklady

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Následující příklad ukazuje použití `foreach` příkaz s instancí <xref:System.Collections.Generic.List%601> typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní:

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

Následující příklad používá `foreach` příkaz s instancí <xref:System.Span%601?displayProperty=nameWithType> typ, který neimplementuje žádné rozhraní:

[!code-csharp-interactive[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

Od verze C# 7.3, pokud čítače výčtu `Current` vrátí vlastnost [odkazovat na návratovou hodnotu](../../programming-guide/classes-and-structs/ref-returns.md) (`ref T` kde `T` je typ prvku kolekce), můžete deklarovat proměnnou iterace `ref` nebo `ref readonly` modifikátor. Následující příklad používá `ref` iterační proměnné a hodnotu každé položky v poli Výraz stackalloc. `ref readonly` Verze iterace kolekce, kterou chcete vytisknout všechny hodnoty. `readonly` Deklarace používá implicitní deklarace lokální proměnné. Implicitní deklarace proměnných je možné buď pomocí `ref` nebo `ref readonly` deklarace, jak můžete explicitně zadané deklarace proměnných.

[!code-csharp-interactive[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Příkaz foreach (specifikace jazyka C#)](/dotnet/csharp/language-reference/language-specification/statements#the-foreach-statement)
- [Použití příkazu foreach s poli](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [for](for.md)
- [Příkazy iterace](iteration-statements.md)
- [Klíčová slova jazyka C#](index.md)
- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
