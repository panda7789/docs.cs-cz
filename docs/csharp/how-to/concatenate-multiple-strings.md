---
title: 'Postupy: řetězení více řetězců (Průvodce v C#)'
description: Zřetězení řetězců v jazyce C# několika způsoby. Další možnosti a důvodech různé možnosti.
ms.date: 02/20/2018
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
ms.openlocfilehash: 355e56acf36b6212ee4563f34722b10b56a0fb47
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43855384"
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a>Postupy: řetězení více řetězců (Průvodce v C#)

*Zřetězení* je proces přidávání jeden řetězec na konci další řetězec. Zřetězení řetězců s použitím `+` operátor. Řetězcové literály a řetězcové konstanty zřetězení dochází v době kompilace; Vyvolá se v žádné zřetězení za běhu. Pro proměnné řetězce zřetězení dochází pouze v době běhu.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Následující příklad používá zřetězení rozdělením dlouhý řetězec literálu řetězce menší za účelem zlepšení čitelnosti ve zdrojovém kódu. Tyto části zřetězeny do jednoho řetězce v době kompilace. Je zahrnutých bez poplatků za běhu výkonu bez ohledu na počet řetězců.  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  

K proměnné řetězce zřetězit, můžete použít `+` nebo `+=` operátory, [interpolace](../language-reference/tokens/interpolated.md) nebo <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> nebo <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> metody. `+` Operátor se snadno používá a zajišťuje intuitivní kódu. I když použijete několik `+` operátory v jednom příkazu, řetězec obsahu zkopírován pouze jednou. Následující kód ukazuje příklady použití `+` a `+=` operátory zřetězení řetězců:

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

V některých výrazů je snazší ke zřetězení řetězců pomocí interpolace řetězců, jak ukazuje následující kód:
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
> V operacích zřetězení řetězec kompilátor jazyka C# považuje za řetězec null stejné prázdný řetězec.

Jiné metody ke zřetězení řetězců je <xref:System.String.Format%2A?displayProperty=nameWithType>. Tato metoda funguje dobře, když vytváříte řetězec z malý počet součástí řetězce.

V ostatních případech může být kombinování řetězců ve smyčce, pokud si nejste jisti, kolik zdrojové řetězce kombinujete a skutečný počet zdrojové řetězce může být poměrně velký. <xref:System.Text.StringBuilder> Třídy je navržená pro tyto scénáře. Následující kód používá <xref:System.Text.StringBuilder.Append%2A> metodu <xref:System.Text.StringBuilder> třídy ke zřetězení řetězců.  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

Další informace o [důvodů, proč zvolit zřetězení řetězců nebo `StringBuilder` třídy](xref:System.Text.StringBuilder#StringAndSB)

Další možnost spojit řetězce z kolekce je použití <xref:System.String.Concat%2A?displayProperty=nameWithType> metoda. Použití <xref:System.String.Join%2A?displayProperty=nameWithType> metodu, pokud zdrojové řetězce musí být odděleny delimeter. Následující kód kombinuje pole slov pomocí obou těchto metod:

[!code-csharp-interactive[concatenation of string collection](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]

V poslední, můžete použít [LINQ](../programming-guide/concepts/linq/index.md) a <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> způsob připojit se k řetězce z kolekce. Tato metoda kombinuje zdrojové řetězce použití výrazu lambda. Výraz lambda funguje přidat do existující akumulací každého řetězce. V následujícím příkladu jsou k dispozici pole slova přidáním mezeru mezi jednotlivých slov v poli:

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#6)]  

Tyto ukázky můžete zkusit pohledem na kód v našich [úložiště GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings). Nebo si můžete stáhnout ukázky [jako soubor zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Viz také

- <xref:System.String>  
- <xref:System.Text.StringBuilder>  
- [Průvodce programováním v jazyce C#](../programming-guide/index.md)  
- [Řetězce](../programming-guide/strings/index.md)
