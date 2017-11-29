---
title: "Použitelnost funkční transformaci (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: c78107bd-b006-4574-a3d4-bbf808388ff3
caps.latest.revision: "4"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c7196e128a6d61b2b28e955a79561db2b9a5e51b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="applicability-of-functional-transformation-c"></a>Použitelnost funkční transformaci (C#)
Čistý funkční transformace platí v celé řadě situacích.  
  
 Funkční transformace přístupu je ideální pro dotazování a manipulace s nimi strukturovaných dat; proto vyhovuje s technologií LINQ. Funkční transformace má však mnohem širší použitelnost než použití s dotazy LINQ. Jakýkoli proces, kde je hlavní aktivní transformace dat z jednoho formátu do druhého by měly být považovány pravděpodobně kandidátem na funkční transformace.  
  
 Tento přístup je pro mnoho problémů, které nemusí být kandidátem na první pohled zobrazit. Používá ve spojení s nebo samostatně z technologie LINQ, považovat za funkční transformaci v následujících oblastech:  
  
-   Dokumenty XML. Všechny dialekt XML ve správném formátu data můžete snadno upravit prostřednictvím funkční transformace. Další informace najdete v tématu [funkční transformace XML (C#)](../../../../csharp/programming-guide/concepts/linq/functional-transformation-of-xml.md).  
  
-   Ostatní formáty strukturovaných souborů. Většina souborů z Windows.ini soubory do prostého textu dokumentů, mít některé struktura, která slouží k analýze a transformace.  
  
-   Protokoly streamování data. Kódování dat do a dekódování dat z komunikační protokoly můžete často reprezentované pomocí jednoduchého funkční transformace.  
  
-   RDBMS a OODBMS data. Relační a objektově orientované databáze, stejně jako XML, jsou často používá strukturované datové zdroje.  
  
-   Mathematic statistiky a vědecké účely řešení. Tato pole jsou obvykle zpracování velkých datových sad, které vám pomohou uživatele v vizualizace, odhad nebo ve skutečnosti řešení potíží, které nejsou v netriviálních.  
  
 Jak je popsáno v [refaktoring do čistého funkce (C#)](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md), pomocí čistý funkcí je příkladem funkční programování. V další jejich okamžité výhody pomocí čistý funkcí poskytuje cenné v přemýšlení o problémy z hlediska funkčnosti transformace. Tento přístup může mít významný vliv na program a třída návrhu. To platí hlavně při problém slouží k transformaci řešení dat, jak je popsáno výše.  
  
 I když jsou nad rámec tohoto kurzu, návrhy, které jsou ovlivněné funkční transformace perspektivy jsou obvykle na střed v procesech více než u objektů jako aktéři a výsledný řešení obvykle provádí jako řadu ve velkém měřítku transformace, místo jednotlivého objektu změny stavu.  
  
 Znovu nezapomeňte, že C# podporuje imperativní a funkční přístupy, takže nejvhodnější návrh pro vaše aplikace může obsahovat elementy obou.  
  
## <a name="see-also"></a>Viz také  
 [Úvod do čistého funkční transformace (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
 [Funkční transformace XML (C#)](../../../../csharp/programming-guide/concepts/linq/functional-transformation-of-xml.md)  
 [Refaktoring do čistého funkcí (C#)](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md)
