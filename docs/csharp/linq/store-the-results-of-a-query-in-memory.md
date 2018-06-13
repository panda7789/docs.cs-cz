---
title: Ukládání výsledků dotazu do paměti
description: Tom, jak ukládat výsledky.
ms.date: 11/30/2016
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: c125d134d7c1db98363844c12fc8abd3faa9c868
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33279630"
---
# <a name="store-the-results-of-a-query-in-memory"></a>Ukládání výsledků dotazu do paměti

Dotaz je v podstatě sadu pokyny, jak získat a uspořádat data. Dotazy jsou líné, provést, protože každá další položka ve výsledku se požaduje. Při použití `foreach` položky k iteraci výsledky, se vrátí jako získat přístup. K vyhodnocení dotazu a ukládat své výsledky bez spuštění `foreach` cykly, stačí jeden z následujících metod zavolat na proměnnou dotazu:  
  
-   <xref:System.Linq.Enumerable.ToList%2A>  
  
-   <xref:System.Linq.Enumerable.ToArray%2A>  
  
-   <xref:System.Linq.Enumerable.ToDictionary%2A>  
  
-   <xref:System.Linq.Enumerable.ToLookup%2A>  
  
 Doporučujeme vám, že při ukládání výsledků dotazu je vrácená kolekce objekt přiřadit nové proměnné jak je znázorněno v následujícím příkladu:  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideLINQ#25](../../../samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]  
  

## <a name="see-also"></a>Viz také  
 [LINQ – výrazy dotazů](index.md)
