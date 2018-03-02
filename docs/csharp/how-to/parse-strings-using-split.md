---
title: "Postupy: Analýza řetězců využívajících String.Split (Průvodce C#)"
description: "String.Split vrací pole řetězců rozdělení ze sady oddělovače. Je snadný způsob, jak analyzovat řetězce."
ms.date: 01/03/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
author: BillWagner
ms.author: wiwagn
ms.custom: mvc
ms.openlocfilehash: afaff6f81a1a4240214f738d0fc9f3bafdaf868c
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2018
---
# <a name="how-to-parse-strings-using-stringsplit-c-guide"></a>Postupy: Analýza řetězců využívajících String.Split (Průvodce C#)

<xref:System.String.Split%2A?displayProperty=nameWithType> Metoda vytvoří pole podřetězců rozdělením vstupní řetězec založený na jeden nebo více oddělovače. Často je nejjednodušší způsob, jak jednotlivé řetězec na hranicích aplikace word. Slouží také k rozdělení řetězců na jiné zvláštní znaky nebo řetězce.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Následující kód rozdělí běžné slovní spojení na pole řetězců pro každou aplikaci word.

[!code-csharp-interactive[split strings on word boundaries](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#1)]

Všechny instance oddělovací znak slouží k vytvoření hodnoty v poli vráceném. Po sobě jdoucí oddělovače vytvořit prázdný řetězec jako hodnotu v poli vráceném.  Můžete to vidět v následujícím příkladu, který používá jako oddělovač místa:

[!code-csharp-interactive[split strings with repeated separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#2)]

Toto chování usnadňuje formáty stejně jako soubory s hodnotami (CSV) oddělený čárkami představující tabulková data. Po sobě jdoucích čárkami představují sloupec je prázdný.

Abyste mohli předávat volitelný <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parametr vyloučit všechny prázdné řetězce v poli vráceném. Pro složitější zpracování vrácená kolekce, můžete použít [LINQ](../programming-guide/concepts/linq/index.md) k manipulaci s pořadí výsledek.    

<xref:System.String.Split%2A?displayProperty=nameWithType> můžete použít více znaků oddělovače. Následující příklad používá mezery, čárky, tečky, dvojtečky a karty, všechny předané pole obsahující tyto oddělení znaky, na <xref:System.String.Split%2A>.  Smyčky v dolní části kód zobrazí každý slova v poli vráceném.  

[!code-csharp-interactive[split strings using multiple separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#3)]

Po sobě jdoucích instancí všechny oddělovače způsobit prázdný řetězec v poli výstup:

[!code-csharp-interactive[split strings using multiple consecutive separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#4)]

<xref:System.String.Split%2A?displayProperty=nameWithType> může trvat pole řetězců (sekvence znaků, které se chovají jako oddělovače pro potřeby analýzy cíl řetězce, místo jedné znaků).  
  
[!code-csharp-interactive[split strings using strings as separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#5)]

Tyto ukázky můžete zkusit prohlížením kódu v našem [úložiště GitHub](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings). Nebo si můžete stáhnout ukázky [jako soubor zip](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../programming-guide/index.md)  
 [Řetězce](../programming-guide/strings/index.md)  
 [Regulární výrazy rozhraní .NET](../../standard/base-types/regular-expressions.md)
