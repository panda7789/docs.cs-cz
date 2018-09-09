---
title: 'Postupy: Analýza řetězců metodou String.Split (Průvodce v C#)'
description: String.Split vrátí pole řetězců oddělit od sadu oddělovačů. Je snadný způsob, jak parsovat řetězce.
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: b6170be2dbb3f11906bbaa6e5c3be3e48a976246
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/09/2018
ms.locfileid: "44228062"
---
# <a name="how-to-parse-strings-using-stringsplit-c-guide"></a>Postupy: Analýza řetězců metodou String.Split (Průvodce v C#)

<xref:System.String.Split%2A?displayProperty=nameWithType> Metoda vytvoří pole podřetězců rozdělení vstupního řetězce podle jednoho nebo více oddělovačů. Často je nejjednodušším způsobem rozdělení řetězce na hranicích slov. Používá se také k rozdělení řetězců na jiné určitých znaků nebo řetězce.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Následující kód rozdělí běžných frází na pole řetězců pro každé slovo.

[!code-csharp-interactive[split strings on word boundaries](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#1)]

Každá instance oddělovací znak produkuje hodnotu jako pole vrácené. Po sobě jdoucích oddělovače vytvořit prázdný řetězec jako hodnotu jako pole vrácené.  To můžete vidět v následujícím příkladu, který se použije jako oddělovač místo:

[!code-csharp-interactive[split strings with repeated separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#2)]

Toto chování usnadňuje formáty jako oddělený čárkami souborů (CSV) představující tabulková data. Po sobě jdoucích čárek představují sloupec je prázdný.

Můžete předat volitelně <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parametr vyloučit jakékoli prázdné řetězce vrácené jako pole. Pro složitější zpracování vrácená kolekce, můžete použít [LINQ](../programming-guide/concepts/linq/index.md) k manipulaci s výsledkem pořadí.

<xref:System.String.Split%2A?displayProperty=nameWithType> můžete použít více znaky oddělovačů.
Následující příklad používá mezery, čárky, tečky, dvojtečky a karty, všechny předané pole obsahující tyto znaky, pro oddělení <xref:System.String.Split%2A>.
Smyčka v dolní části kódu zobrazí jednotlivých slov v příspěvcích ve vrácené pole.  

[!code-csharp-interactive[split strings using multiple separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#3)]

Po sobě jdoucích instancí žádné oddělovače způsobit prázdný řetězec v poli výstup:

[!code-csharp-interactive[split strings using multiple consecutive separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#4)]

<xref:System.String.Split%2A?displayProperty=nameWithType> může trvat pole řetězců (sekvence znaků, které se chovají jako oddělovače pro analýzu cílovém řetězci namísto jednotlivé znaky).  
  
[!code-csharp-interactive[split strings using strings as separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#5)]

Tyto ukázky můžete zkusit pohledem na kód v našich [úložiště GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings). Nebo si můžete stáhnout ukázky [jako soubor zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../programming-guide/index.md)  
- [Řetězce](../programming-guide/strings/index.md)  
- [Regulárních výrazů .NET](../../standard/base-types/regular-expressions.md)
