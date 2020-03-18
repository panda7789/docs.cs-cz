---
title: Operace prvku (C#)
ms.date: 10/03/2018
ms.assetid: 283206c9-3246-4c48-b01a-d9de409a7231
ms.openlocfilehash: e9ec41793afffe60a7184622f91b5fc023e0958f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345163"
---
# <a name="element-operations-c"></a>Operace prvku (C#)

Operace prvku vrátí jeden, konkrétní prvek z sekvence.  
  
 Standardní metody operátoru dotazu, které provádějí operace prvku, jsou uvedeny v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka C#|Další informace|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Elementat|Vrátí prvek v zadaném indexu v kolekci.|Neužívá se.|<xref:System.Linq.Enumerable.ElementAt%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ElementAt%2A?displayProperty=nameWithType>|  
|ElementatOrDefault|Vrátí prvek na zadaný index v kolekci nebo výchozí hodnotu, pokud je index mimo rozsah.|Neužívá se.|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ElementAtOrDefault%2A?displayProperty=nameWithType>|  
|První|Vrátí první prvek kolekce nebo první prvek, který splňuje podmínku.|Neužívá se.|<xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.First%2A?displayProperty=nameWithType>|  
|Firstordefault|Vrátí první prvek kolekce nebo první prvek, který splňuje podmínku. Vrátí výchozí hodnotu, pokud takový prvek neexistuje.|Neužívá se.|<xref:System.Linq.Enumerable.FirstOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%60%601%28System.Linq.IQueryable%7B%60%600%7D%29?displayProperty=nameWithType>|  
|Poslední|Vrátí poslední prvek kolekce nebo poslední prvek, který splňuje podmínku.|Neužívá se.|<xref:System.Linq.Enumerable.Last%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Last%2A?displayProperty=nameWithType>|  
|LastOrDefault|Vrátí poslední prvek kolekce nebo poslední prvek, který splňuje podmínku. Vrátí výchozí hodnotu, pokud takový prvek neexistuje.|Neužívá se.|<xref:System.Linq.Enumerable.LastOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LastOrDefault%2A?displayProperty=nameWithType>|  
|Single|Vrátí pouze prvek kolekce nebo jediný prvek, který splňuje podmínku. <xref:System.InvalidOperationException> Vyvolá, pokud neexistuje žádný prvek nebo více než jeden prvek vrátit. |Neužívá se.|<xref:System.Linq.Enumerable.Single%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Single%2A?displayProperty=nameWithType>|  
|Singleordefault|Vrátí pouze prvek kolekce nebo jediný prvek, který splňuje podmínku. Vrátí výchozí hodnotu, pokud neexistuje žádný prvek, který by měl být vrácen. Vyvolá <xref:System.InvalidOperationException> pokud je více než jeden prvek vrátit. |Neužívá se.|<xref:System.Linq.Enumerable.SingleOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SingleOrDefault%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Linq>
- [Standardní operátory dotazů – přehled (C#)](./standard-query-operators-overview.md)
- [Jak dotazovat na největší soubor nebo soubory ve stromu adresářů (LINQ) (C#)](./how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)
