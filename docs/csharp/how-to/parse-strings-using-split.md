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
ms.openlocfilehash: cf8307517213b54041b272843232eb595660b2e9
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389506"
---
# <a name="how-to-parse-strings-using-stringsplit-in-c"></a>Jak analyzovat řetězce pomocí String.Split v C\#

Metoda <xref:System.String.Split%2A?displayProperty=nameWithType> vytvoří pole podřetězců rozdělením vstupního řetězce na základě jednoho nebo více oddělovačů. Často se jedná o nejjednodušší způsob, jak oddělit řetězec na hranice slov. Používá se také k rozdělení řetězců na jiné konkrétní znaky nebo řetězce.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Následující kód rozdělí společnou frázi do pole řetězců pro každé slovo.

[!code-csharp-interactive[split strings on word boundaries](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#1)]

Každá instance znaku oddělovače vytvoří hodnotu ve vráceném poli. Po sobě jdoucí oddělovací znaky vytvářejí prázdný řetězec jako hodnotu ve vráceném poli. Můžete vidět, jak je vytvořen prázdný řetězec v následujícím příkladu, který používá znak mezery jako oddělovač.

[!code-csharp-interactive[split strings with repeated separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#2)]

Toto chování usnadňuje formáty, jako jsou soubory csv oddělené čárkami (CSV), které představují tabulková data. Po sobě jdoucí čárky představují prázdný sloupec.

Můžete předat volitelný <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parametr vyloučit všechny prázdné řetězce ve vráceném poli. Pro složitější zpracování vrácené kolekce můžete použít [LINQ](../programming-guide/concepts/linq/index.md) k manipulaci s výsledkovou sekvencí.

<xref:System.String.Split%2A?displayProperty=nameWithType>můžete použít více oddělovacích znaků.
Následující příklad používá mezery, čárky, tečky, dvojtečky a tabulátory, všechny <xref:System.String.Split%2A>předané v poli obsahujícím tyto oddělující znaky do .
Smyčka v dolní části kódu zobrazí každé slovo v vrácené pole.  

[!code-csharp-interactive[split strings using multiple separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#3)]

Po sobě jdoucí instance libovolného oddělovače vytvoří prázdný řetězec ve výstupním poli:

[!code-csharp-interactive[split strings using multiple consecutive separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#4)]

<xref:System.String.Split%2A?displayProperty=nameWithType>může trvat pole řetězců (sekvence znaků, které fungují jako oddělovače pro analýzu cílového řetězce, namísto jednotlivých znaků).  
  
[!code-csharp-interactive[split strings using strings as separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#5)]

Tyto ukázky můžete vyzkoušet tak, že se podíváte na kód v našem [úložišti GitHub](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings). Nebo si můžete stáhnout ukázky [jako zip soubor](../../../samples/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../programming-guide/index.md)
- [Řetězce](../programming-guide/strings/index.md)
- [Regulární výrazy rozhraní .NET](../../standard/base-types/regular-expressions.md)
