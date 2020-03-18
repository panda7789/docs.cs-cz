---
title: Jak analyzovat řetězce pomocí String.Split (C# Guide)
description: String.Split vrátí pole řetězců rozdělených ze sady oddělovačů. Je to snadný způsob, jak analyzovat struny.
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: b46429f3b55658e1f2a7d21eed714c1d02236c57
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73973224"
---
# <a name="how-to-parse-strings-using-stringsplit-c-guide"></a>Jak analyzovat řetězce pomocí String.Split (C# Guide)

Metoda <xref:System.String.Split%2A?displayProperty=nameWithType> vytvoří pole podřetězců rozdělením vstupního řetězce na základě jednoho nebo více oddělovačů. Často se jedná o nejjednodušší způsob, jak oddělit řetězec na hranice slov. Používá se také k rozdělení řetězců na jiné konkrétní znaky nebo řetězce.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Následující kód rozdělí společnou frázi do pole řetězců pro každé slovo.

[!code-csharp-interactive[split strings on word boundaries](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#1)]

Každá instance znaku oddělovače vytvoří hodnotu ve vráceném poli. Po sobě jdoucí oddělovací znaky vytvářejí prázdný řetězec jako hodnotu ve vráceném poli.  To můžete vidět v následujícím příkladu, který používá mezeru jako oddělovač:

[!code-csharp-interactive[split strings with repeated separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#2)]

Toto chování usnadňuje formáty, jako jsou soubory csv (comma separated) představující tabulková data. Po sobě jdoucí čárky představují prázdný sloupec.

Můžete předat volitelný <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parametr vyloučit všechny prázdné řetězce ve vráceném poli. Pro složitější zpracování vrácené kolekce můžete použít [LINQ](../programming-guide/concepts/linq/index.md) k manipulaci s výsledkovou sekvencí.

<xref:System.String.Split%2A?displayProperty=nameWithType>můžete použít více oddělovacích znaků.
Následující příklad používá mezery, čárky, tečky, dvojtečky a tabulátory, všechny <xref:System.String.Split%2A>předané v poli obsahujícím tyto oddělující znaky do .
Smyčka v dolní části kódu zobrazí každé slovo v vrácené pole.  

[!code-csharp-interactive[split strings using multiple separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#3)]

Po sobě jdoucí instance libovolného oddělovače vytvoří prázdný řetězec ve výstupním poli:

[!code-csharp-interactive[split strings using multiple consecutive separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#4)]

<xref:System.String.Split%2A?displayProperty=nameWithType>může trvat pole řetězců (sekvence znaků, které fungují jako oddělovače pro analýzu cílového řetězce, namísto jednotlivých znaků).  
  
[!code-csharp-interactive[split strings using strings as separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#5)]

Tyto ukázky můžete vyzkoušet tak, že se podíváte na kód v našem [úložišti GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings). Nebo si můžete stáhnout ukázky [jako zip soubor](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../programming-guide/index.md)
- [Řetězce](../programming-guide/strings/index.md)
- [Regulární výrazy rozhraní .NET](../../standard/base-types/regular-expressions.md)
