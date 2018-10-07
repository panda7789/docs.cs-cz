---
title: Operace s elementy (C#)
ms.date: 10/03/2018
ms.assetid: 283206c9-3246-4c48-b01a-d9de409a7231
ms.openlocfilehash: dbae8c0b3d98fe9674fbbeb432c1e42763e81026
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48836774"
---
# <a name="element-operations-c"></a>Operace s elementy (C#)

Operace s elementy vrátí jeden, konkrétní element ze sekvence.  
  
 Standardní metody operátoru dotazu, které provádějí operace s elementy jsou uvedeny v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka C#|Další informace|  
|-----------------|-----------------|---------------------------------|----------------------|  
|ElementAt|Vrátí prvek na zadaném indexu v kolekci.|Nelze použít.|<xref:System.Linq.Enumerable.ElementAt%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ElementAt%2A?displayProperty=nameWithType>|  
|ElementAtOrDefault|Vrátí prvek na zadaném indexu v kolekci nebo výchozí hodnotu, pokud index je mimo rozsah.|Nelze použít.|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ElementAtOrDefault%2A?displayProperty=nameWithType>|  
|první|Vrátí první prvek kolekce nebo první prvek, který splňuje podmínku.|Nelze použít.|<xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.First%2A?displayProperty=nameWithType>|  
|Metody FirstOrDefault|Vrátí první prvek kolekce nebo první prvek, který splňuje podmínku. Vrátí výchozí hodnotu, pokud žádný takový prvek neexistuje.|Nelze použít.|<xref:System.Linq.Enumerable.FirstOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%60%601%28System.Linq.IQueryable%7B%60%600%7D%29?displayProperty=nameWithType>|  
|poslední|Vrátí poslední prvek kolekce nebo poslední prvek, který splňuje podmínku.|Nelze použít.|<xref:System.Linq.Enumerable.Last%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Last%2A?displayProperty=nameWithType>|  
|LastOrDefault|Vrátí poslední prvek kolekce nebo poslední prvek, který splňuje podmínku. Vrátí výchozí hodnotu, pokud žádný takový prvek neexistuje.|Nelze použít.|<xref:System.Linq.Enumerable.LastOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LastOrDefault%2A?displayProperty=nameWithType>|  
|Single|Vrátí jediný prvek kolekce nebo jediným prvkem, který splňuje podmínku. Vyvolá <xref:System.InvalidOperationException> Pokud neexistuje žádný element nebo vrátit více než jeden element. |Nelze použít.|<xref:System.Linq.Enumerable.Single%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Single%2A?displayProperty=nameWithType>|  
|SingleOrDefault|Vrátí jediný prvek kolekce nebo jediným prvkem, který splňuje podmínku. Vrátí výchozí hodnotu, pokud neexistuje žádný element vrátit. Vyvolá <xref:System.InvalidOperationException> Pokud dojde k vrácení více než jeden element. |Nelze použít.|<xref:System.Linq.Enumerable.SingleOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SingleOrDefault%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Linq>  
- [Přehled standardních operátorů dotazu (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
- [Postupy: dotazování na největší soubor či soubory v adresářovém stromu (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)
