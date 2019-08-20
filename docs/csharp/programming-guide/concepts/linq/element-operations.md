---
title: Operace elementu (C#)
ms.date: 10/03/2018
ms.assetid: 283206c9-3246-4c48-b01a-d9de409a7231
ms.openlocfilehash: b32066d13e700d95e4d2eef29e24e8b87690037d
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594571"
---
# <a name="element-operations-c"></a>Operace elementu (C#)

Operace elementu vrací jeden konkrétní prvek z sekvence.  
  
 Standardní metody operátoru dotazu, které provádějí operace s elementy, jsou uvedeny v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|C#Syntaxe výrazu dotazu|Další informace|  
|-----------------|-----------------|---------------------------------|----------------------|  
|ElementAt|Vrátí prvek v zadaném indexu v kolekci.|Není k dispozici.|<xref:System.Linq.Enumerable.ElementAt%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ElementAt%2A?displayProperty=nameWithType>|  
|ElementAtOrDefault|Vrátí prvek v zadaném indexu v kolekci nebo výchozí hodnotu, pokud je index mimo rozsah.|Není k dispozici.|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ElementAtOrDefault%2A?displayProperty=nameWithType>|  
|První|Vrátí první prvek kolekce nebo první prvek, který splňuje podmínku.|Není k dispozici.|<xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.First%2A?displayProperty=nameWithType>|  
|FirstOrDefault|Vrátí první prvek kolekce nebo první prvek, který splňuje podmínku. Vrací výchozí hodnotu, pokud žádný takový prvek neexistuje.|Není k dispozici.|<xref:System.Linq.Enumerable.FirstOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%60%601%28System.Linq.IQueryable%7B%60%600%7D%29?displayProperty=nameWithType>|  
|Poslední|Vrátí poslední prvek kolekce nebo poslední prvek, který splňuje podmínku.|Není k dispozici.|<xref:System.Linq.Enumerable.Last%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Last%2A?displayProperty=nameWithType>|  
|LastOrDefault|Vrátí poslední prvek kolekce nebo poslední prvek, který splňuje podmínku. Vrací výchozí hodnotu, pokud žádný takový prvek neexistuje.|Není k dispozici.|<xref:System.Linq.Enumerable.LastOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LastOrDefault%2A?displayProperty=nameWithType>|  
|Single|Vrátí jediný prvek kolekce nebo jediný prvek, který splňuje podmínku. Vyvolá výjimku, pokud neexistuje žádný element nebo více než jeden prvek, který chcete vrátit. <xref:System.InvalidOperationException> |Není k dispozici.|<xref:System.Linq.Enumerable.Single%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Single%2A?displayProperty=nameWithType>|  
|SingleOrDefault|Vrátí jediný prvek kolekce nebo jediný prvek, který splňuje podmínku. Vrátí výchozí hodnotu, pokud neexistuje žádný element k vrácení. Vyvolá výjimku, pokud existuje více než jeden prvek, který se má vrátit. <xref:System.InvalidOperationException> |Není k dispozici.|<xref:System.Linq.Enumerable.SingleOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SingleOrDefault%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq>
- [Přehled standardních operátorů dotazůC#()](./standard-query-operators-overview.md)
- [Postupy: Dotaz na největší soubor nebo soubory v adresářovém stromu (LINQ) (C#)](./how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)
