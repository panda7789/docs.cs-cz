---
title: Výrazy v dotazech LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: 234b3059f9109c23b8ecae4da37e15f7f094fbd1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59203233"
---
# <a name="expressions-in-linq-to-entities-queries"></a>Výrazy v dotazech LINQ to Entities
Výraz je fragment kódu, který lze vyhodnotit na jednu hodnotu, objekt, metodu nebo obor názvů. Hodnota literálu, volání metody, operátor a jeho operandy nebo jednoduchý název může obsahovat výrazy. Název proměnné, člen typu, parametr metody, obor názvů nebo typ může být jednoduché názvy. Výrazy můžete použít operátory, které pak použít jako parametry nebo volání metody, jejíž parametry jsou zase další volání metody jiných výrazech. Proto výrazy v rozsahu jednoduché až velmi složité.  
  
 V [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazy, výrazy mohou obsahovat cokoli, co povoluje typy v rámci <xref:System.Linq.Expressions> obor názvů, včetně výrazy lambda. Výrazy, které lze použít v [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazy jsou množinou výrazy, které lze použít k dotazování [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].  Výrazy, které jsou součástí sady dotazů [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] jsou omezené na operací podporované `ObjectQuery<T>` a podkladový zdroj dat.  
  
 V následujícím příkladu se v porovnání `Where` klauzule je výraz:  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
>  Vytvoří konkrétní jazyk, jako je C# `unchecked`, nemají význam [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Výrazy konstant](../../../../../../docs/framework/data/adonet/ef/language-reference/constant-expressions.md)  
  
 [Výrazy porovnání](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-expressions.md)  
  
 [Porovnávání s hodnotou Null](../../../../../../docs/framework/data/adonet/ef/language-reference/null-comparisons.md)  
  
 [Výrazy inicializace](../../../../../../docs/framework/data/adonet/ef/language-reference/initialization-expressions.md)  
  
 [Relace, navigačních vlastností a cizí klíče](/ef/ef6/fundamentals/relationships)  
  
## <a name="see-also"></a>Viz také:

- [ADO.NET Entity Framework](../../../../../../docs/framework/data/adonet/ef/index.md)
