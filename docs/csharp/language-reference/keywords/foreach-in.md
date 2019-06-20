---
title: Příkaz foreach jazyka C#
ms.date: 05/17/2019
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: af4850b4c33727c818fb5a67d17fb6146627fa06
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/20/2019
ms.locfileid: "67267734"
---
# <a name="foreach-in-c-reference"></a>foreach, in (referenční dokumentace jazyka C#)

`foreach` Příkaz opakuje příkaz nebo blok příkazů pro každý prvek v instanci typu, který implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> nebo <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> rozhraní. `foreach` Příkaz není omezena pouze na tyto typy které můžou uplatnit na instanci typu, který splňuje následující podmínky:

- nemá veřejný konstruktor bez parametrů `GetEnumerator` metoda, jejíž návratový typ je třída, struktura nebo typ rozhraní
- Návratový typ `GetEnumerator` metoda má veřejnou `Current` vlastnost a veřejný konstruktor bez parametrů `MoveNext` metoda, jejíž návratový typ je <xref:System.Boolean>.

Od verze C# 7.3, pokud čítače výčtu `Current` vrátí vlastnost [odkazovat na návratovou hodnotu](ref.md#reference-return-values) (`ref T` kde `T` je typ prvku kolekce), můžete deklarovat proměnnou iterace `ref` nebo `ref readonly` modifikátor.

Na libovolný bod v rámci `foreach` blok příkazů, můžete přerušit ze smyčky s použitím [přerušení](break.md) příkazu nebo kroku na následující iteraci ve smyčce pomocí [pokračovat](continue.md) příkazu. Také můžete ukončit `foreach` smyčky pomocí [goto](goto.md), [vrátit](return.md), nebo [throw](throw.md) příkazy.

Pokud `foreach` příkazu je použita na `null`, <xref:System.NullReferenceException> je vyvolána výjimka. Pokud zdrojové kolekce `foreach` příkaz je prázdný, text `foreach` smyčky není spuštěn a přeskočí.

## <a name="examples"></a>Příklady

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Následující příklad ukazuje použití `foreach` příkaz s instancí <xref:System.Collections.Generic.List%601> typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní:

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

Následující příklad používá `foreach` příkaz s instancí <xref:System.Span%601?displayProperty=nameWithType> typ, který neimplementuje žádné rozhraní:

[!code-csharp[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

Následující příklad používá `ref` iterační proměnné a hodnotu každé položky v poli Výraz stackalloc. `ref readonly` Verze iterace kolekce, kterou chcete vytisknout všechny hodnoty. `readonly` Deklarace používá implicitní deklarace lokální proměnné. Implicitní deklarace proměnných je možné buď pomocí `ref` nebo `ref readonly` deklarace, jak můžete explicitně zadané deklarace proměnných.

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [příkazu foreach](~/_csharplang/spec/statements.md#the-foreach-statement) část [ C# specifikace jazyka](../language-specification/index.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Použití příkazu foreach s poli](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [For – příkaz](for.md)
