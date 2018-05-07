---
title: Odložené provedení a opožděné vyhodnocení v technologii LINQ to XML (C#)
ms.date: 07/20/2015
ms.assetid: 8683d1b4-b7ec-407b-be12-906ebe958a09
ms.openlocfilehash: dd0b8413f172182edfc83f99fd418d1372984b7d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-c"></a>Odložené provedení a opožděné vyhodnocení v technologii LINQ to XML (C#)
Operace dotazů a osu se často implementují používat odložené provedení. Toto téma vysvětluje požadavky a výhody odložené provedení a některé aspekty implementace.  
  
## <a name="deferred-execution"></a>Odložené provedení  
 Odložené provedení znamená, že je zpožděna vyhodnocení výrazu, dokud jeho *uvědomili si* je ve skutečnosti požadována hodnota. Odložené provedení může výrazně zlepšit výkon, když máte k manipulaci s kolekcí velkého množství dat, zejména v programech, které obsahují řadu zřetězené dotazy nebo manipulace. V případě nejlepší umožňuje odložené provedení jednoho iteraci prostřednictvím kolekce zdroje.  
  
 Technologie LINQ využívají rozsáhlé odložené provedení v obou členy základní <xref:System.Linq?displayProperty=nameWithType> třídy a metody rozšíření v různých oborech názvů LINQ, jako například <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.  
  
 Odložené provedení je podporována přímo v jazyce C# pomocí [yield](../../../../csharp/language-reference/keywords/yield.md) – klíčové slovo (ve formě `yield-return` příkaz) při použití v rámci bloku iterator. Takové iterovat musí vracet kolekci typu <xref:System.Collections.IEnumerator> nebo <xref:System.Collections.Generic.IEnumerator%601> (nebo odvozený typ).  
  
## <a name="eager-vs-lazy-evaluation"></a>Přes vs. Opožděné vyhodnocení  
 Pokud napíšete metodu, která implementuje odložené provedení, máte také rozhodnout, zda chcete implementovat metodu pomocí opožděné vyhodnocení nebo přes hodnocení.  
  
-   V *opožděné vyhodnocení*, jeden prvek zdrojové kolekci je zpracovaných za každé volání iteraci. To je typické způsob, ve kterém jsou implementované iterátory.  
  
-   V *přes vyhodnocení*, první volání iteraci způsobí celou kolekci zpracovává. Dočasnou kopii tohoto zdrojové kolekci může být taky potřeba. Například <xref:System.Linq.Enumerable.OrderBy%2A> metoda má seřadit celou kolekci před vrátí první prvek.  
  
 Opožděné vyhodnocení obvykle poskytuje lepší výkon, protože distribuuje nároky na zpracování rovnoměrně v rámci vyhodnocení kolekce a minimalizuje použití dočasná data. Samozřejmě pro některé operace, není žádná možnost než chcete vyhodnotit mezilehlých výsledků.  
  
## <a name="next-steps"></a>Další kroky  
 Další téma v tomto kurzu znázorňuje odložené provedení:  
  
-   [Odložené provedení příklad (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-example.md)  
  
## <a name="see-also"></a>Viz také  
 [Kurz: Řetězení dotazy společně (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)  
 [Principy a terminologií (funkční transformaci) (C#)](../../../../csharp/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)  
 [Agregační operace (C#)](../../../../csharp/programming-guide/concepts/linq/aggregation-operations.md)  
 [yield](../../../../csharp/language-reference/keywords/yield.md)
