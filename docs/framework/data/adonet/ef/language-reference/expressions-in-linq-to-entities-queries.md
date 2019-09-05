---
title: Výrazy v dotazech LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: 5262d2bca07525aba6db5303e730c8b358641d52
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250976"
---
# <a name="expressions-in-linq-to-entities-queries"></a>Výrazy v dotazech LINQ to Entities
Výraz je fragment kódu, který lze vyhodnotit na jedinou hodnotu, objekt, metodu nebo obor názvů. Výrazy mohou obsahovat hodnotu literálu, volání metody, operátor a jeho operandy nebo jednoduchý název. Jednoduché názvy mohou být název proměnné, typ členu, parametr metody, obor názvů nebo typ. Výrazy mohou používat operátory, které zase používají jiné výrazy jako parametry, nebo volání metody, jejichž parametry jsou zapínají jiné volání metody. Výrazy mohou proto být v rozsahu od jednoduchých až po velmi složité.  
  
 V LINQ to Entities dotazy mohou výrazy obsahovat cokoli, co povoluje typy v rámci <xref:System.Linq.Expressions> oboru názvů, včetně výrazů lambda. Výrazy, které lze použít v LINQ to Entities dotazů, jsou nadmnožinou výrazů, které lze použít k dotazování na [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].  Výrazy, které jsou součástí dotazů proti, [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] jsou omezeny na operace podporované `ObjectQuery<T>` nástrojem a podkladovým zdrojem dat.  
  
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
