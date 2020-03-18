---
title: Jak zřetězit více řetězců (Průvodce C#)
description: Existuje několik způsobů, jak zřetězit řetězce v c#. Seznamte se s možnostmi a důvody různých možností.
ms.date: 02/20/2018
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
ms.openlocfilehash: 9a0640a7ce73fa8454442cd301157bf5c265f9de
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713900"
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a>Jak zřetězit více řetězců (Průvodce C#)

*Zřetězení* je proces připojení jednoho řetězce na konec jiného řetězce. Řetězce můžete zřetězit pomocí `+` operátoru. Pro řetězcové literály a konstanty řetězců dochází k zřetězení v době kompilace; nedojde k žádnému zřetězení za běhu. Pro proměnné řetězce dochází k zřetězení pouze za běhu.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Následující příklad používá zřetězení rozdělit dlouhý řetězec literál do menších řetězců s cílem zlepšit čitelnost ve zdrojovém kódu. Tyto části jsou zřetězeny do jednoho řetězce v době kompilace. Neexistuje žádné náklady na výkon za běhu bez ohledu na počet zapojených řetězců.  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  

Chcete-li zřetězit proměnné řetězce, `+` můžete `+=` použít operátory [nebo, interpolaci řetězce](../language-reference/tokens/interpolated.md) nebo <xref:System.String.Format%2A?displayProperty=nameWithType>metody <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> nebo <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> metody. Obsluha `+` se snadno používá a umožňuje intuitivní kód. I v případě, že používáte několik `+` operátorů v jednom příkazu, obsah řetězce se zkopíruje pouze jednou. Následující kód ukazuje příklady `+` použití `+=` a operátory zřetězit řetězce:

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

V některých výrazech je snazší zřetězit řetězce pomocí interpolace řetězců, jak ukazuje následující kód:
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
> V operacích zřetězení řetězce kompilátor jazyka C# zachází s nulovým řetězcem stejně jako s prázdným řetězcem.

Další metodou pro zřetězení <xref:System.String.Format%2A?displayProperty=nameWithType>řetězců je . Tato metoda funguje dobře při vytváření řetězce z malého počtu řetězců komponent.

V ostatních případech může být kombinování řetězců ve smyčce, kde nevíte, kolik zdrojových řetězců kombinujete a skutečný počet zdrojových řetězců může být poměrně velký. Třída <xref:System.Text.StringBuilder> byla navržena pro tyto scénáře. Následující kód používá <xref:System.Text.StringBuilder.Append%2A> metodu <xref:System.Text.StringBuilder> třídy ke zřetězení řetězců.  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

Můžete si přečíst více o [důvodech, `StringBuilder` proč zvolit zřetězení řetězců nebo třídu](xref:System.Text.StringBuilder#StringAndSB).

Další možností pro připojení řetězců z <xref:System.String.Concat%2A?displayProperty=nameWithType> kolekce je použití metody. Použijte <xref:System.String.Join%2A?displayProperty=nameWithType> metodu, pokud by měly být zdrojové řetězce odděleny delimetrem. Následující kód kombinuje pole slov pomocí obou metod:

[!code-csharp-interactive[concatenation of string collection](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]

Nakonec můžete použít [LINQ](../programming-guide/concepts/linq/index.md) a <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> metodu pro spojení řetězců z kolekce. Tato metoda kombinuje zdrojové řetězce pomocí výrazu lambda. Výraz lambda provádí práci přidat každý řetězec do existující akumulace. Následující příklad kombinuje pole slov přidáním mezery mezi každé slovo v poli:

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#6)]  

Tyto ukázky můžete vyzkoušet tak, že se podíváte na kód v našem [úložišti GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings). Nebo si můžete stáhnout ukázky [jako zip soubor](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Viz také

- <xref:System.String>
- <xref:System.Text.StringBuilder>
- [Programovací příručka jazyka C#](../programming-guide/index.md)
- [Řetězce](../programming-guide/strings/index.md)
