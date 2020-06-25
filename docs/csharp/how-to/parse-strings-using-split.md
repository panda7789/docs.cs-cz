---
title: Analyzovat řetězce pomocí String. Split (Průvodce C#)
description: Metoda Split vrátí pole řetězců rozdělené ze sady oddělovačů. Je to snadný způsob, jak analyzovat řetězce.
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: 7c5d8fa462775c6f3a9981693129997dda6c2286
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324143"
---
# <a name="how-to-parse-strings-using-stringsplit-in-c"></a>Jak analyzovat řetězce pomocí řetězce. rozdělit v jazyce C\#

<xref:System.String.Split%2A?displayProperty=nameWithType>Metoda vytvoří pole podřetězců rozdělením vstupního řetězce na základě jednoho nebo více oddělovačů. Tato metoda je často nejjednodušší způsob, jak oddělit řetězec na hranici slova. Používá se také k rozdělení řetězců na jiné konkrétní znaky nebo řetězce.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Následující kód rozdělí společnou frázi na pole řetězců pro každé slovo.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet1":::

Každá instance znaku oddělovače vytvoří hodnotu ve vráceném poli. Po sobě jdoucí oddělovací znaky vytvoří prázdný řetězec jako hodnotu ve vráceném poli. V následujícím příkladu vidíte, jak se vytvoří prázdný řetězec, který jako oddělovač používá znak mezery.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet2":::

Toto chování usnadňuje formátování jako soubory hodnot oddělených čárkami (CSV), které představují tabulková data. Po sobě jdoucí čárky představuje prázdný sloupec.

Můžete předat volitelný <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parametr pro vyloučení prázdných řetězců ve vráceném poli. Pro složitější zpracování vrácené kolekce můžete použít [LINQ](../programming-guide/concepts/linq/index.md) k manipulaci s pořadím výsledků.

<xref:System.String.Split%2A?displayProperty=nameWithType>může použít více znaků oddělovače.
Následující příklad používá mezery, čárky, tečky, dvojtečky a tabulátory jako oddělení znaků, které jsou předány <xref:System.String.Split%2A> v poli.
Smyčka v dolní části kódu zobrazí všechna slova ve vráceném poli.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet3":::

Po sobě jdoucí instance libovolného oddělovače vyprodukuje prázdný řetězec v výstupním poli:

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet4":::

<xref:System.String.Split%2A?displayProperty=nameWithType>může převzít pole řetězců (sekvence znaků, které fungují jako oddělovače pro analýzu cílového řetězce místo jednotlivých znaků).

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet5":::

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../programming-guide/index.md)
- [Řetězce](../programming-guide/strings/index.md)
- [Regulární výrazy .NET](../../standard/base-types/regular-expressions.md)
