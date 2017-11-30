---
title: "Odložené provedení a opožděné vyhodnocení v technologii LINQ to XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31998eed-b95e-47fb-a865-9de1f337d1fb
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3a465c4448157505a42db57202298cb18e44a562
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
