---
title: foreach, in (Referenční dokumentace jazyka C#)
ms.date: 05/24/2018
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: b6b7dc0a4d3970ddfbbb6635ccebbbd5b75671e4
ms.sourcegitcommit: 54231aa56fca059e9297888a96fbca1d4cf3746c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/25/2018
---
# <a name="foreach-in-c-reference"></a>foreach, in (Referenční dokumentace jazyka C#)

`foreach` Příkaz spustí příkaz nebo blok příkazů pro jednotlivé elementy v instanci typu, který implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> nebo <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> rozhraní. `foreach` Příkaz není omezen na tyto typy a dají se použít k instanci žádný typ, který splňuje tyto podmínky:

- má public bez parametrů `GetEnumerator` metoda, jejíž návratový typ je třída, struktura nebo typ rozhraní
- Návratový typ `GetEnumerator` metoda má veřejnosti `Current` vlastnost a public bez parametrů `MoveNext` metoda s návratovým typem <xref:System.Boolean>.

Kdykoli bodu v rámci `foreach` příkaz bloku, může dojít k narušení mimo smyčky pomocí [zalomení](break.md) – klíčové slovo nebo krok do další iterace ve smyčce pomocí [pokračovat](continue.md) – klíčové slovo. Také můžete ukončit `foreach` cykly pomocí [goto](goto.md), [vrátit](return.md), nebo [throw](throw.md) příkazy.

## <a name="examples"></a>Příklady

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Následující příklad ukazuje použití `foreach` příkaz s instanci <xref:System.Collections.Generic.List%601> typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní:

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

Další příklad používá `foreach` příkaz s instanci <xref:System.Span%601?displayProperty=nameWithType> typu, který neimplementuje žádné rozhraní:

[!code-csharp-interactive[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

## <a name="c-language-specification"></a>Specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

[Foreach – příkaz (specifikace jazyka C#)](/dotnet/csharp/language-reference/language-specification/statements#the-foreach-statement)  
[Použití příkazu foreach s poli](../../programming-guide/arrays/using-foreach-with-arrays.md)  
[for](for.md)  
[Příkazy iterace](iteration-statements.md)  
[Klíčová slova jazyka C#](index.md)  
[Referenční dokumentace jazyka C#](../index.md)  
[Průvodce programováním v jazyce C#](../../programming-guide/index.md)  