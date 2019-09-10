---
title: Výrazy v dotazech LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: e625ac3968542c65e737093c0ac292de4c2ffa37
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854455"
---
# <a name="expressions-in-linq-to-entities-queries"></a>Výrazy v dotazech LINQ to Entities
Výraz je fragment kódu, který lze vyhodnotit na jedinou hodnotu, objekt, metodu nebo obor názvů. Výrazy mohou obsahovat hodnotu literálu, volání metody, operátor a jeho operandy nebo jednoduchý název. Jednoduché názvy mohou být název proměnné, typ členu, parametr metody, obor názvů nebo typ. Výrazy mohou používat operátory, které zase používají jiné výrazy jako parametry, nebo volání metody, jejichž parametry jsou zapínají jiné volání metody. Výrazy mohou proto být v rozsahu od jednoduchých až po velmi složité.  
  
 V LINQ to Entities dotazy mohou výrazy obsahovat cokoli, co povoluje typy v rámci <xref:System.Linq.Expressions> oboru názvů, včetně výrazů lambda. Výrazy, které lze použít v LINQ to Entities dotazů, jsou nadmnožinou výrazů, které lze použít k dotazování Entity Framework. výrazy, které jsou součástí dotazů proti Entity Framework jsou omezeny na operace podporované `ObjectQuery<T>` a podkladový zdroj dat.  
  
 V následujícím příkladu je porovnání v `Where` klauzuli výrazem:  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
> Konkrétní jazykové konstrukce, jako C# `unchecked`například, nemají v LINQ to Entities žádný význam.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Výrazy konstant](constant-expressions.md)  
  
 [Výrazy porovnání](comparison-expressions.md)  
  
 [Porovnávání s hodnotou Null](null-comparisons.md)  
  
 [Výrazy inicializace](initialization-expressions.md)  
  
 [Relace, navigační vlastnosti a cizí klíče](/ef/ef6/fundamentals/relationships)  
  
## <a name="see-also"></a>Viz také:

- [ADO.NET Entity Framework](../index.md)
