---
title: Operace elementu (C#)
description: Přečtěte si o standardních metodách operátoru dotazu, které dělají operace prvků, které vracejí jeden prvek z sekvence v jazyce C#.
ms.date: 10/03/2018
ms.assetid: 283206c9-3246-4c48-b01a-d9de409a7231
ms.openlocfilehash: 8cd34146a3b93205ec01ed128aacb79d566a03c6
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105443"
---
# <a name="element-operations-c"></a>Operace elementu (C#)

Operace elementu vrací jeden konkrétní prvek z sekvence.  
  
 Standardní metody operátoru dotazu, které provádějí operace s elementy, jsou uvedeny v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu v jazyce C#|Další informace|  
|-----------------|-----------------|---------------------------------|----------------------|  
|ElementAt|Vrátí prvek v zadaném indexu v kolekci.|Neužívá se.|<xref:System.Linq.Enumerable.ElementAt%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ElementAt%2A?displayProperty=nameWithType>|  
|ElementAtOrDefault|Vrátí prvek v zadaném indexu v kolekci nebo výchozí hodnotu, pokud je index mimo rozsah.|Neužívá se.|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ElementAtOrDefault%2A?displayProperty=nameWithType>|  
|První|Vrátí první prvek kolekce nebo první prvek, který splňuje podmínku.|Neužívá se.|<xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.First%2A?displayProperty=nameWithType>|  
|FirstOrDefault|Vrátí první prvek kolekce nebo první prvek, který splňuje podmínku. Vrací výchozí hodnotu, pokud žádný takový prvek neexistuje.|Neužívá se.|<xref:System.Linq.Enumerable.FirstOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%60%601%28System.Linq.IQueryable%7B%60%600%7D%29?displayProperty=nameWithType>|  
|Poslední|Vrátí poslední prvek kolekce nebo poslední prvek, který splňuje podmínku.|Neužívá se.|<xref:System.Linq.Enumerable.Last%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Last%2A?displayProperty=nameWithType>|  
|LastOrDefault|Vrátí poslední prvek kolekce nebo poslední prvek, který splňuje podmínku. Vrací výchozí hodnotu, pokud žádný takový prvek neexistuje.|Neužívá se.|<xref:System.Linq.Enumerable.LastOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LastOrDefault%2A?displayProperty=nameWithType>|  
|Jeden|Vrátí jediný prvek kolekce nebo jediný prvek, který splňuje podmínku. Vyvolá výjimku, <xref:System.InvalidOperationException> Pokud neexistuje žádný element nebo více než jeden prvek, který chcete vrátit. |Neužívá se.|<xref:System.Linq.Enumerable.Single%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Single%2A?displayProperty=nameWithType>|  
|SingleOrDefault|Vrátí jediný prvek kolekce nebo jediný prvek, který splňuje podmínku. Vrátí výchozí hodnotu, pokud neexistuje žádný element k vrácení. Vyvolá výjimku <xref:System.InvalidOperationException> , pokud existuje více než jeden prvek, který se má vrátit. |Neužívá se.|<xref:System.Linq.Enumerable.SingleOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SingleOrDefault%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Linq>
- [Přehled standardních operátorů dotazů (C#)](./standard-query-operators-overview.md)
- [Dotazování na největší soubor nebo soubory ve stromu adresářů (LINQ) (C#)](./how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)
