---
title: Použitelnost funkční transformaci (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 3b74e134-e19b-44bc-8d06-e26c48305040
ms.openlocfilehash: bdb487ce0de986a1dba36908352a8270cfde2700
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="applicability-of-functional-transformation-visual-basic"></a>Použitelnost funkční transformaci (Visual Basic)
Čistý funkční transformace platí v celé řadě situacích.  
  
 Funkční transformace přístupu je ideální pro dotazování a manipulace s nimi strukturovaných dat; proto vyhovuje s technologií LINQ. Funkční transformace má však mnohem širší použitelnost než použití s dotazy LINQ. Jakýkoli proces, kde je hlavní aktivní transformace dat z jednoho formátu do druhého by měly být považovány pravděpodobně kandidátem na funkční transformace.  
  
 Tento přístup je pro mnoho problémů, které nemusí být kandidátem na první pohled zobrazit. Používá ve spojení s nebo samostatně z technologie LINQ, považovat za funkční transformaci v následujících oblastech:  
  
-   Dokumenty XML. Všechny dialekt XML ve správném formátu data můžete snadno upravit prostřednictvím funkční transformace. Další informace najdete v tématu [funkční transformace XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-transformation-of-xml.md).  
  
-   Ostatní formáty strukturovaných souborů. Většina souborů z Windows.ini soubory do prostého textu dokumentů, mít některé struktura, která slouží k analýze a transformace.  
  
-   Protokoly streamování data. Kódování dat do a dekódování dat z komunikační protokoly můžete často reprezentované pomocí jednoduchého funkční transformace.  
  
-   RDBMS a OODBMS data. Relační a objektově orientované databáze, stejně jako XML, jsou často používá strukturované datové zdroje.  
  
-   Mathematic statistiky a vědecké účely řešení. Tato pole jsou obvykle zpracování velkých datových sad, které vám pomohou uživatele v vizualizace, odhad nebo ve skutečnosti řešení potíží, které nejsou v netriviálních.  
  
 Jak je popsáno v [refaktoring do čistého funkce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/refactoring-into-pure-functions.md), pomocí čistý funkcí je příkladem funkční programování. V další jejich okamžité výhody pomocí čistý funkcí poskytuje cenné v přemýšlení o problémy z hlediska funkčnosti transformace. Tento přístup může mít významný vliv na program a třída návrhu. To platí hlavně při problém slouží k transformaci řešení dat, jak je popsáno výše.  
  
 I když jsou nad rámec tohoto kurzu, návrhy, které jsou ovlivněné funkční transformace perspektivy jsou obvykle na střed v procesech více než u objektů jako aktéři a výsledný řešení obvykle provádí jako řadu ve velkém měřítku transformace, místo jednotlivého objektu změny stavu.  
  
 Znovu nezapomeňte, že jazyka Visual Basic podporuje imperativní a funkční přístupy, tak nejvhodnější návrh pro vaše aplikace může obsahovat elementy obou.  
  
## <a name="see-also"></a>Viz také  
 [Úvod do čistého funkční transformace (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
 [Funkční transformace XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-transformation-of-xml.md)  
 [Refaktoring do čistého funkce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/refactoring-into-pure-functions.md)
