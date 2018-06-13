---
title: Operace kvantifikátoru (C#)
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: dac5ca7349a45f5fc37cff0cb83bd6b2e1292568
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339862"
---
# <a name="quantifier-operations-c"></a>Operace kvantifikátoru (C#)
Operace kvantifikátoru vrátit <xref:System.Boolean> hodnotu, která určuje, zda některé nebo všechny elementy v pořadí splňují podmínku.  
  
 Následující obrázek znázorňuje dvě různé kvantifikátoru operace na dva různé zdroje pořadí. První operace požádá, pokud jedna nebo více elementů je znak "A" a výsledkem je `true`. Druhá operace požádá, pokud jsou všechny prvky znak "A" a výsledkem je `true`.  
  
 ![Operace kvantifikátoru LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")  
  
 Metody operátor standardní dotazu, které provádějí operace kvantifikátoru jsou uvedeny v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka C#|Další informace|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Všechny|Určuje, zda všechny elementy v pořadí splňují podmínku.|Nelze použít.|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|všechny|Určuje, zda všechny elementy v pořadí splňují podmínku.|Nelze použít.|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|Obsahuje|Určuje, zda sekvence obsahuje zadaný element.|Nelze použít.|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Linq>  
 [Přehled standardních operátorů dotazu (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Postupy: dynamické určování filtrů predikátů při běhu](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)  
 [Postupy: dotazu na věty obsahující zadanou množinu slov (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
