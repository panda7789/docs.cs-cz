---
title: Odložené provedení a opožděné vyhodnocení v LINQ to XML (C#)
ms.date: 07/20/2015
ms.assetid: 8683d1b4-b7ec-407b-be12-906ebe958a09
ms.openlocfilehash: baf6a26b1579c17adfc60b27b485ba3af66c67d7
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43787857"
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-c"></a>Odložené provedení a opožděné vyhodnocení v LINQ to XML (C#)
Operace dotazů a osy jsou často implementována pomocí odloženého provedení. Toto téma popisuje požadavky a výhody odložené provedení a některé důležité informace o implementaci.  
  
## <a name="deferred-execution"></a>Odložené provedení  
 Odložené provedení znamená, že vyhodnocení výrazu je odložena až do jeho *realizované* hodnota je skutečně nutná. Odložené provedení může výrazně zlepšit výkon, když máte k manipulaci s kolekcí velkých objemů dat, zejména v aplikacích, které obsahují řadu zřetězených dotazů nebo manipulace. Odložené provedení v nejlepším případě umožňuje pouze jednu iterace přes zdrojové kolekce.  
  
 Technologie LINQ využívat rozsáhlé odložené provedení v členy základní <xref:System.Linq?displayProperty=nameWithType> třídy a metody rozšíření v různých oborech názvů LINQ, jako například <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.  
  
 Odložené provedení je podporován přímo v jazyce C# pomocí [yield](../../../../csharp/language-reference/keywords/yield.md) – klíčové slovo (ve formě `yield-return` příkaz) při použití v rámci blok iterátoru. Takové iterátor musí vracet kolekci typu <xref:System.Collections.IEnumerator> nebo <xref:System.Collections.Generic.IEnumerator%601> (nebo odvozeného typu).  
  
## <a name="eager-vs-lazy-evaluation"></a>Nemůžou dočkat, až vs. Opožděné vyhodnocení  
 Když napíšete metodu, která implementuje odložené provedení, máte také rozhodnout, jestli se má implementovat metodu pomocí opožděné vyhodnocení nebo nemůžou dočkat, až hodnocení.  
  
-   V *opožděné vyhodnocení*, jeden element zdrojové kolekce je zpracovaných za každé volání iterátoru. Toto je typická způsob, ve kterém jsou implementovány iterátory.  
  
-   V *nemůžou dočkat, až hodnocení*, první volání iterátoru způsobí celou kolekci právě zpracovává. Dočasná kopie zdrojové kolekce může být také potřeba. Například <xref:System.Linq.Enumerable.OrderBy%2A> metoda se má seřadit celou kolekci dříve, než vrátí první prvek.  
  
 Opožděné vyhodnocení obvykle poskytuje lepší výkon, protože distribuuje nároky na zpracování rovnoměrně během vyhodnocení kolekce a minimalizuje využití dočasná data. Samozřejmě pro některé operace, neexistuje žádná možnost než a materializovat mezilehlých výsledků.  
  
## <a name="next-steps"></a>Další kroky  
 Další téma v tomto kurzu ukazuje odložené provedení:  
  
-   [Příklad odloženého provedení (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-example.md)  
  
## <a name="see-also"></a>Viz také

- [Kurz: Zřetězení dotazů společně (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)  
- [Koncepty a terminologie (funkční transformace) (C#)](../../../../csharp/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)  
- [Agregační operace (C#)](../../../../csharp/programming-guide/concepts/linq/aggregation-operations.md)  
- [yield](../../../../csharp/language-reference/keywords/yield.md)
