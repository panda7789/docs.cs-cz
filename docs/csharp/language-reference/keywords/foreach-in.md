---
title: foreach, in (Referenční dokumentace jazyka C#)
ms.date: 06/28/2018
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: e4b5ba6fb97d82d2b6f03e77995b9d3c2b9d68c6
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37104413"
---
# <a name="foreach-in-c-reference"></a>foreach, in (Referenční dokumentace jazyka C#)

`foreach` Příkaz spustí příkaz nebo blok příkazů pro jednotlivé elementy v instanci typu, který implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> nebo <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> rozhraní. `foreach` Příkaz není omezen na tyto typy a dají se použít k instanci žádný typ, který splňuje tyto podmínky:

- má public bez parametrů `GetEnumerator` metoda, jejíž návratový typ je třída, struktura nebo typ rozhraní
- Návratový typ `GetEnumerator` metoda má veřejnosti `Current` vlastnost a public bez parametrů `MoveNext` metoda s návratovým typem <xref:System.Boolean>.

Kdykoli bodu v rámci `foreach` příkaz bloku, může dojít k narušení mimo smyčky pomocí [zalomení](break.md) příkaz nebo krok do další iterace ve smyčce pomocí [pokračovat](continue.md) příkaz. Také můžete ukončit `foreach` cykly pomocí [goto](goto.md), [vrátit](return.md), nebo [throw](throw.md) příkazy.

## <a name="examples"></a>Příklady

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Následující příklad ukazuje použití `foreach` příkaz s instanci <xref:System.Collections.Generic.List%601> typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní:

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

Další příklad používá `foreach` příkaz s instanci <xref:System.Span%601?displayProperty=nameWithType> typu, který neimplementuje žádné rozhraní:

[!code-csharp-interactive[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

Počínaje 7.3 C#, když typ kolekce podporuje `ref` přístup k jeho prvky, můžou deklarovat proměnnou iteraci pomocí `ref` nebo `ref readonly` modifikátor. Následující příklad používá `ref` proměnné iterace nastavit hodnotu každé položky v poli stackalloc. `ref readonly` Verze iterace kolekce k vytištění všech hodnot. `readonly` Deklarace používá implicitní deklarace místní proměnné. Implicitní deklarace proměnných lze použít s buď `ref` nebo `ref readonly` deklarace, jak můžete explicitně zadali deklarace proměnných.

[!code-csharp-interactive[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

[Foreach – příkaz (specifikace jazyka C#)](/dotnet/csharp/language-reference/language-specification/statements#the-foreach-statement)  
[Použití příkazu foreach s poli](../../programming-guide/arrays/using-foreach-with-arrays.md)  
[for](for.md)  
[Příkazy iterace](iteration-statements.md)  
[Klíčová slova jazyka C#](index.md)  
[Referenční dokumentace jazyka C#](../index.md)  
[Průvodce programováním v jazyce C#](../../programming-guide/index.md)  