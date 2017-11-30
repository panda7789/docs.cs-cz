---
title: "Ukládání výsledků dotazu do paměti"
description: "Tom, jak ukládat výsledky."
keywords: "Rozhraní .NET, rozhraní .NET core, C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: 86a9c2d464eac83cabb5faa68987ad580fc31248
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/18/2017
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
