---
title: Jak zřetězit více řetězců (C# průvodce)
description: Existuje několik způsobů, jak zřetězit řetězce v C#. Seznamte se s možnostmi a důvody za různými volbami.
ms.date: 02/20/2018
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
ms.openlocfilehash: 2e443030445d2817c8f53a044a261edd22eeb26e
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973271"
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a>Jak zřetězit více řetězců (C# průvodce)

*Zřetězení* je proces připojení jednoho řetězce na konec jiného řetězce. Řetězení řetězců pomocí operátoru `+`. Pro řetězcové literály a řetězcové konstanty probíhá zřetězení v době kompilace; nedochází k žádnému zřetězení běhu. V případě řetězcových proměnných probíhá zřetězení pouze v době běhu.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Následující příklad používá zřetězení pro rozdělení dlouhého řetězcového literálu na menší řetězce, aby bylo možné zlepšit čitelnost ve zdrojovém kódu. Tyto části jsou zřetězeny do jednoho řetězce v době kompilace. Neexistují žádné náklady na výkon za běhu bez ohledu na počet zahrnutých řetězců.  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  

Chcete-li zřetězit proměnné řetězce, můžete použít operátory `+` nebo `+=`, [interpolaci řetězců](../language-reference/tokens/interpolated.md) nebo <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> nebo <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> metody. Operátor `+` se snadno používá a vytváří intuitivní kód. I v případě, že v jednom příkazu použijete několik operátorů `+`, je obsah řetězce zkopírován pouze jednou. Následující kód ukazuje příklady použití operátorů `+` a `+=` k zřetězení řetězců:

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

V některých výrazech je snazší zřetězit řetězce pomocí interpolace řetězců, jak ukazuje následující kód:
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
> V operacích zřetězení řetězců C# kompilátor zpracovává řetězec s hodnotou null stejně jako prázdný řetězec.

Jinou metodou zřetězení řetězců je <xref:System.String.Format%2A?displayProperty=nameWithType>. Tato metoda funguje dobře při sestavování řetězce z malého počtu řetězců komponent.

V jiných případech může být kombinování řetězců ve smyčce, kde nevíte, kolik zdrojového řetězce se zkombinujete, a skutečný počet zdrojových řetězců může být poměrně velký. Třída <xref:System.Text.StringBuilder> byla pro tyto scénáře navržena. Následující kód používá metodu <xref:System.Text.StringBuilder.Append%2A> třídy <xref:System.Text.StringBuilder> k zřetězení řetězců.  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

Můžete si přečíst další informace o [důvodech pro výběr zřetězení řetězců nebo `StringBuilder` třídy](xref:System.Text.StringBuilder#StringAndSB) .

Další možností připojení řetězců z kolekce je použití metody <xref:System.String.Concat%2A?displayProperty=nameWithType>. Použijte <xref:System.String.Join%2A?displayProperty=nameWithType> metodu, pokud by měly být zdrojové řetězce odděleny oddělovač. Následující kód kombinuje pole slov pomocí obou metod:

[!code-csharp-interactive[concatenation of string collection](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]

V posledních, můžete použít metodu [LINQ](../programming-guide/concepts/linq/index.md) a <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> k připojení řetězců z kolekce. Tato metoda kombinuje zdrojové řetězce pomocí výrazu lambda. Výraz lambda dokončí práci pro přidání každého řetězce do stávajícího akumulace. Následující příklad kombinuje pole slov přidáním mezery mezi jednotlivá slova v poli:

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#6)]  

Tyto ukázky můžete vyzkoušet na základě kódu v našem [úložišti GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings). Nebo si můžete stáhnout ukázky [jako soubor zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Viz také:

- <xref:System.String>
- <xref:System.Text.StringBuilder>
- [Průvodce programováním v jazyce C#](../programming-guide/index.md)
- [Řetězce](../programming-guide/strings/index.md)
