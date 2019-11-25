---
title: Jak analyzovat řetězce pomocí String. Split (C# vodítko)
description: String. Split vrátí pole řetězců rozdělené ze sady oddělovačů. Je to snadný způsob, jak analyzovat řetězce.
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: b46429f3b55658e1f2a7d21eed714c1d02236c57
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973224"
---
# <a name="how-to-parse-strings-using-stringsplit-c-guide"></a>Jak analyzovat řetězce pomocí String. Split (C# vodítko)

Metoda <xref:System.String.Split%2A?displayProperty=nameWithType> vytvoří pole podřetězců rozdělením vstupního řetězce na základě jednoho nebo více oddělovačů. Je často nejjednodušší způsob, jak oddělit řetězec na hranici slova. Používá se také k rozdělení řetězců na jiné konkrétní znaky nebo řetězce.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Následující kód rozdělí společnou frázi na pole řetězců pro každé slovo.

[!code-csharp-interactive[split strings on word boundaries](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#1)]

Každá instance znaku oddělovače vytvoří hodnotu ve vráceném poli. Po sobě jdoucí oddělovací znaky vytvoří prázdný řetězec jako hodnotu ve vráceném poli.  Můžete to vidět v následujícím příkladu, který jako oddělovač používá místo:

[!code-csharp-interactive[split strings with repeated separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#2)]

Toto chování usnadňuje formátování, jako jsou soubory s hodnotami oddělenými čárkou (CSV), které představují tabulková data. Po sobě jdoucí čárky představuje prázdný sloupec.

Můžete předat volitelný <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parametr pro vyloučení prázdných řetězců ve vráceném poli. Pro složitější zpracování vrácené kolekce můžete použít [LINQ](../programming-guide/concepts/linq/index.md) k manipulaci s pořadím výsledků.

<xref:System.String.Split%2A?displayProperty=nameWithType> může použít více znaků oddělovače.
Následující příklad používá mezery, čárky, tečky, dvojtečky a tabulátory, všechny předané v poli, které obsahuje tyto dělicí znaky, k <xref:System.String.Split%2A>.
Smyčka v dolní části kódu zobrazí všechna slova ve vráceném poli.  

[!code-csharp-interactive[split strings using multiple separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#3)]

Po sobě jdoucí instance libovolného oddělovače vyprodukuje prázdný řetězec v výstupním poli:

[!code-csharp-interactive[split strings using multiple consecutive separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#4)]

<xref:System.String.Split%2A?displayProperty=nameWithType> může převzít pole řetězců (sekvence znaků, které fungují jako oddělovače pro analýzu cílového řetězce místo jednotlivých znaků).  
  
[!code-csharp-interactive[split strings using strings as separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#5)]

Tyto ukázky můžete vyzkoušet na základě kódu v našem [úložišti GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings). Nebo si můžete stáhnout ukázky [jako soubor zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../programming-guide/index.md)
- [Řetězce](../programming-guide/strings/index.md)
- [Regulární výrazy .NET](../../standard/base-types/regular-expressions.md)
