---
title: Operace s elementy (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 283206c9-3246-4c48-b01a-d9de409a7231
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 55081e66419624c2c4930a254d3d464007477766
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="element-operations-c"></a>Operace s elementy (C#)
Operace s elementy vrátí jeden, konkrétní element z řady.  
  
 Operátor metody standardní dotazů, které provádět operace s elementy jsou uvedeny v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka C#|Další informace|  
|-----------------|-----------------|---------------------------------|----------------------|  
|ElementAt|Vrátí element v zadaném indexu v kolekci.|Nelze použít.|<xref:System.Linq.Enumerable.ElementAt%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ElementAt%2A?displayProperty=nameWithType>|  
|ElementAtOrDefault|Vrátí element v zadaném indexu v kolekci nebo výchozí hodnotu, pokud index je mimo rozsah.|Nelze použít.|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ElementAtOrDefault%2A?displayProperty=nameWithType>|  
|první|Vrátí první prvek kolekce nebo první prvek, který splňuje podmínku.|Nelze použít.|<xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.First%2A?displayProperty=nameWithType>|  
|FirstOrDefault|Vrátí první prvek kolekce nebo první prvek, který splňuje podmínku. Vrátí výchozí hodnotu, pokud neexistuje žádný takový prvek.|Nelze použít.|<xref:System.Linq.Enumerable.FirstOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%60%601%28System.Linq.IQueryable%7B%60%600%7D%29?displayProperty=nameWithType>|  
|poslední|Vrátí poslední prvek kolekce nebo poslední elementu, který splňuje podmínku.|Nelze použít.|<xref:System.Linq.Enumerable.Last%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Last%2A?displayProperty=nameWithType>|  
|LastOrDefault|Vrátí poslední prvek kolekce nebo poslední elementu, který splňuje podmínku. Vrátí výchozí hodnotu, pokud neexistuje žádný takový prvek.|Nelze použít.|<xref:System.Linq.Enumerable.LastOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LastOrDefault%2A?displayProperty=nameWithType>|  
|Single|Vrátí jediný prvek kolekce nebo jediným prvkem, který splňuje podmínku.|Nelze použít.|<xref:System.Linq.Enumerable.Single%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Single%2A?displayProperty=nameWithType>|  
|SingleOrDefault|Vrátí jediný prvek kolekce nebo jediným prvkem, který splňuje podmínku. Vrátí výchozí hodnotu, pokud neexistuje žádný takový prvek nebo kolekci neobsahuje právě jeden element.|Nelze použít.|<xref:System.Linq.Enumerable.SingleOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SingleOrDefault%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Linq>  
 [Přehled standardních operátorů dotazu (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Postupy: dotazování na největší soubor či soubory v adresářovém stromu (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)
