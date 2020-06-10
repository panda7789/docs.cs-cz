---
title: Jak zřetězit více řetězců (Průvodce C#)
description: Existuje několik způsobů, jak zřetězit řetězce v jazyce C#. Seznamte se s možnostmi a důvody za různými volbami.
ms.date: 02/20/2018
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
ms.openlocfilehash: ef3d79c5b40d08cb76e58eba1c8831c468fd1fc0
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2020
ms.locfileid: "84663015"
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a>Jak zřetězit více řetězců (Průvodce C#)

*Zřetězení* je proces připojení jednoho řetězce na konec jiného řetězce. Řetězení řetězců pomocí `+` operátoru. Pro řetězcové literály a řetězcové konstanty probíhá zřetězení v době kompilace; nedochází k žádnému zřetězení běhu. V případě řetězcových proměnných probíhá zřetězení pouze v době běhu.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Následující příklad používá zřetězení pro rozdělení dlouhého řetězcového literálu na menší řetězce, aby bylo možné zlepšit čitelnost ve zdrojovém kódu. Tyto části jsou zřetězeny do jednoho řetězce v době kompilace. Neexistují žádné náklady na výkon za běhu bez ohledu na počet zahrnutých řetězců.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet1":::

Chcete-li zřetězit řetězcové proměnné, můžete použít `+` `+=` operátory nebo, [interpolování řetězce](../language-reference/tokens/interpolated.md) nebo <xref:System.String.Format%2A?displayProperty=nameWithType> metody, <xref:System.String.Concat%2A?displayProperty=nameWithType> <xref:System.String.Join%2A?displayProperty=nameWithType> nebo <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> . `+`Operátor lze snadno použít a je určen pro intuitivní kód. I v případě, že `+` v jednom příkazu použijete několik operátorů, je obsah řetězce zkopírován pouze jednou. Následující kód ukazuje příklady použití `+` `+=` operátorů a k zřetězení řetězců:

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet2":::

V některých výrazech je snazší zřetězit řetězce pomocí interpolace řetězců, jak ukazuje následující kód:

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet3":::

> [!NOTE]
> V operacích zřetězení řetězců kompilátor jazyka C# zpracuje řetězec null stejný jako prázdný řetězec.

Jinou metodou zřetězení řetězců je <xref:System.String.Format%2A?displayProperty=nameWithType> . Tato metoda funguje dobře při sestavování řetězce z malého počtu řetězců komponent.

V jiných případech může být kombinování řetězců ve smyčce, kde nevíte, kolik zdrojových řetězců se zkombinujete, a skutečný počet zdrojových řetězců může být velký. <xref:System.Text.StringBuilder>Třída byla navržena pro tyto scénáře. Následující kód používá <xref:System.Text.StringBuilder.Append%2A> metodu <xref:System.Text.StringBuilder> třídy pro zřetězení řetězců.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet4":::

Můžete si přečíst další informace o [důvodech pro výběr zřetězení řetězců nebo `StringBuilder` třídy](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder#the-string-and-stringbuilder-types).

Další možností připojení řetězců z kolekce je použití <xref:System.String.Concat%2A?displayProperty=nameWithType> metody. Použijte <xref:System.String.Join%2A?displayProperty=nameWithType> metodu, pokud mají být zdrojové řetězce odděleny oddělovačem. Následující kód kombinuje pole slov pomocí obou metod:

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet5":::

V poslední době můžete [LINQ](../programming-guide/concepts/linq/index.md) <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> k připojení řetězců z kolekce použít LINQ a metodu. Tato metoda kombinuje zdrojové řetězce pomocí výrazu lambda. Výraz lambda dokončí práci pro přidání každého řetězce do stávajícího akumulace. Následující příklad kombinuje pole slov přidáním mezery mezi jednotlivá slova v poli:

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet6":::

## <a name="see-also"></a>Viz také

- <xref:System.String>
- <xref:System.Text.StringBuilder>
- [Průvodce programováním v C#](../programming-guide/index.md)
- [Řetězce](../programming-guide/strings/index.md)
