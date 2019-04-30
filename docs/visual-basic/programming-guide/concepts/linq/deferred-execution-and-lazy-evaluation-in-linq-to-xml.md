---
title: Odložené provedení a opožděné vyhodnocení v LINQ to XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 31998eed-b95e-47fb-a865-9de1f337d1fb
ms.openlocfilehash: b5c3e2a484aa16df22742ddf77d6438ec2a699bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790530"
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-visual-basic"></a>Odložené provedení a opožděné vyhodnocení v LINQ to XML (Visual Basic)
Operace dotazů a osy jsou často implementována pomocí odloženého provedení. Toto téma popisuje požadavky a výhody odložené provedení a některé důležité informace o implementaci.  
  
## <a name="deferred-execution"></a>Odložené provedení  
 Odložené provedení znamená, že vyhodnocení výrazu je odložena až do jeho *realizované* hodnota je skutečně nutná. Odložené provedení může výrazně zlepšit výkon, když máte k manipulaci s kolekcí velkých objemů dat, zejména v aplikacích, které obsahují řadu zřetězených dotazů nebo manipulace. Odložené provedení v nejlepším případě umožňuje pouze jednu iterace přes zdrojové kolekce.  
  
 Technologie LINQ využívat rozsáhlé odložené provedení v členy základní <xref:System.Linq?displayProperty=nameWithType> třídy a metody rozšíření v různých oborech názvů LINQ, jako například <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.  
  
## <a name="eager-vs-lazy-evaluation"></a>Nemůžou dočkat, až vs. Opožděné vyhodnocení  
 Když napíšete metodu, která implementuje odložené provedení, máte také rozhodnout, jestli se má implementovat metodu pomocí opožděné vyhodnocení nebo nemůžou dočkat, až hodnocení.  
  
- V *opožděné vyhodnocení*, jeden element zdrojové kolekce je zpracovaných za každé volání iterátoru. Toto je typická způsob, ve kterém jsou implementovány iterátory.  
  
- V *nemůžou dočkat, až hodnocení*, první volání iterátoru způsobí celou kolekci právě zpracovává. Dočasná kopie zdrojové kolekce může být také potřeba. Například <xref:System.Linq.Enumerable.OrderBy%2A> metoda se má seřadit celou kolekci dříve, než vrátí první prvek.  
  
 Opožděné vyhodnocení obvykle poskytuje lepší výkon, protože distribuuje nároky na zpracování rovnoměrně během vyhodnocení kolekce a minimalizuje využití dočasná data. Samozřejmě pro některé operace, neexistuje žádná možnost než a materializovat mezilehlých výsledků.  
  
## <a name="next-steps"></a>Další kroky  
 Další téma v tomto kurzu ukazuje odložené provedení:  
  
- [Příklad odloženého provedení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-example.md)  
  
## <a name="see-also"></a>Viz také:

- [Kurz: Odložené provedení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
- [Koncepty a terminologie (funkční transformace) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)
- [Aggregation Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)
