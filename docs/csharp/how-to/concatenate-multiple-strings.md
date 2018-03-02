---
title: "Postupy: řetězení více řetězců (Průvodce C#)"
description: "Zřetězení řetězců v jazyce C# několika způsoby. Další možnosti a důvodech různé možnosti."
ms.date: 02/20/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 43b60455762ecd91a790ea5c7dae49d3348794aa
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2018
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a>Postupy: řetězení více řetězců (Průvodce C#)

*Zřetězení* je proces připojování jeden řetězec na konec jiným řetězcem. Zřetězení řetězců pomocí `+` operátor. Pro textové literály a řetězcové konstanty zřetězení nastane při kompilaci; nastane, bez spuštění zřetězení. Pro proměnné řetězec zřetězení dojde pouze v době běhu.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Následující příklad používá zřetězení rozdělením dlouhý řetězec literálu menší řetězců za účelem zlepšení čitelnosti ve zdrojovém kódu. Následující části jsou zřetězeny do jednoho řetězce v době kompilace. Související se situací je bez nákladů výkon bez ohledu na počet řetězce.  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  
  

Ke zřetězení proměnné řetězce, můžete použít `+` nebo `+=` operátory, [řetězec interpolace](../tutorials/string-interpolation.md) nebo <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> nebo <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> metody. `+` Operátor se snadno používá a zajišťuje intuitivní kódu. I když používáte několik `+` operátory v jednom příkazu, řetězec obsahu zkopíruje pouze jednou. Následující kód ukazuje příklady použití `+` a `+=` operátory zřetězení řetězců:

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

V některých výrazy je snazší zřetězení řetězců pomocí řetězce interpolace, jak ukazuje následující kód:
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
>  V operace s řetězci zřetězení kompilátor jazyka C# zpracovává řetězec null stejné jako prázdný řetězec.

Jiné metody ke zřetězení řetězců je <xref:System.String.Format%2A?displayProperty=nameWithType>. Tato metoda funguje dobře, pokud vytváříte řetězec z malý počet součástí řetězce.

V jiných případech může být kombinovaných řetězců ve smyčce, kde nevíte, kolik řetězce zdrojů kombinujete a skutečný počet řetězce zdrojů může mít poměrně značnou. <xref:System.Text.StringBuilder> Třída byl navržený pro tyto scénáře. Následující kód používá <xref:System.Text.StringBuilder.Append%2A> metodu <xref:System.Text.StringBuilder> třídy ke zřetězení řetězců.  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

Další informace o [důvodů, proč zvolit zřetězení řetězců nebo `StringBuilder` – třída](xref:System.Text.StringBuilder#StringAndSB)

Další možností pro připojení řetězce z kolekce, je použít <xref:System.String.Concat%2A?displayProperty=nameWithType> metoda. Použití <xref:System.String.Join%2A?displayProperty=nameWithType> metoda Pokud zdrojové řetězce musí být odděleny delimeter. Následující kód kombinuje pole slov pomocí obou těchto metod:

[!code-csharp-interactive[concatenation of string collection](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]

V poslední, můžete použít [LINQ](../programming-guide/concepts/linq/index.md) a <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> metoda připojení řetězce z kolekce. Tato metoda kombinuje řetězce zdrojů pomocí výrazu lambda. Výraz lambda funguje pro přidání do existující akumulace každý řetězec. Následující příklad kombinuje pole slov přidáním mezery mezi jednotlivých slov v poli:

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#6)]  

Tyto ukázky můžete zkusit prohlížením kódu v našem [úložiště GitHub](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings). Nebo si můžete stáhnout ukázky [jako soubor zip](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Viz také  
 <xref:System.String>  
 <xref:System.Text.StringBuilder>  
 [Průvodce programováním v jazyce C#](../programming-guide/index.md)  
 [Řetězce](../programming-guide/strings/index.md)
