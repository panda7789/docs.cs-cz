---
title: Odložené provedení a opožděné vyhodnocení v technologii LINQ to XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 31998eed-b95e-47fb-a865-9de1f337d1fb
ms.openlocfilehash: eade2fe987ecbc399c2e2a8a65e74e3beab5e123
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643121"
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-visual-basic"></a>Odložené provedení a opožděné vyhodnocení v technologii LINQ to XML (Visual Basic)
Operace dotazů a osu se často implementují používat odložené provedení. Toto téma vysvětluje požadavky a výhody odložené provedení a některé aspekty implementace.  
  
## <a name="deferred-execution"></a>Odložené provedení  
 Odložené provedení znamená, že je zpožděna vyhodnocení výrazu, dokud jeho *uvědomili si* je ve skutečnosti požadována hodnota. Odložené provedení může výrazně zlepšit výkon, když máte k manipulaci s kolekcí velkého množství dat, zejména v programech, které obsahují řadu zřetězené dotazy nebo manipulace. V případě nejlepší umožňuje odložené provedení jednoho iteraci prostřednictvím kolekce zdroje.  
  
 Technologie LINQ využívají rozsáhlé odložené provedení v obou členy základní <xref:System.Linq?displayProperty=nameWithType> třídy a metody rozšíření v různých oborech názvů LINQ, jako například <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.  
  
## <a name="eager-vs-lazy-evaluation"></a>Přes vs. Opožděné vyhodnocení  
 Pokud napíšete metodu, která implementuje odložené provedení, máte také rozhodnout, zda chcete implementovat metodu pomocí opožděné vyhodnocení nebo přes hodnocení.  
  
-   V *opožděné vyhodnocení*, jeden prvek zdrojové kolekci je zpracovaných za každé volání iteraci. To je typické způsob, ve kterém jsou implementované iterátory.  
  
-   V *přes vyhodnocení*, první volání iteraci způsobí celou kolekci zpracovává. Dočasnou kopii tohoto zdrojové kolekci může být taky potřeba. Například <xref:System.Linq.Enumerable.OrderBy%2A> metoda má seřadit celou kolekci před vrátí první prvek.  
  
 Opožděné vyhodnocení obvykle poskytuje lepší výkon, protože distribuuje nároky na zpracování rovnoměrně v rámci vyhodnocení kolekce a minimalizuje použití dočasná data. Samozřejmě pro některé operace, není žádná možnost než chcete vyhodnotit mezilehlých výsledků.  
  
## <a name="next-steps"></a>Další kroky  
 Další téma v tomto kurzu znázorňuje odložené provedení:  
  
-   [Odložené provedení příklad (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-example.md)  
  
## <a name="see-also"></a>Viz také  
 [Kurz: Odložený provádění (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)  
 [Principy a terminologií (funkční transformaci) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)  
 [Agregační operace (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)
