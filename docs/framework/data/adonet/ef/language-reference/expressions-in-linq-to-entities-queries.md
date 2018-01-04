---
title: "Výrazy v technologii LINQ to Entities dotazy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 6c1460aa78e112d29a4c500c54661b63de03e953
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="expressions-in-linq-to-entities-queries"></a>Výrazy v technologii LINQ to Entities dotazy
Výraz je fragment kódu, který lze vyhodnotit na hodnotu typu single, objekt, metodu nebo obor názvů. Výrazy může obsahovat literálovou hodnotou, volání metod, operátor a jejími operandy nebo jednoduchý název. Název proměnné, typ, parametru metody, obor názvů nebo člena typu může být jednoduché názvy. Výrazy můžete použít operátory, které pak použít jiné výrazy jako parametry nebo volání metod, jejíž parametry jsou naopak další volání metody. Proto výrazy může jít o jednoduché pro velmi složité.  
  
 V [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazy, výrazy může obsahovat nic povolenou typů v rámci <xref:System.Linq.Expressions> obor názvů, včetně výrazy lambda. Výrazy, které mohou být používány [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazy jsou nadmnožinou výrazy, které lze použít k dotazu [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].  Výrazy, které jsou součástí dotazů vůči [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] jsou omezeny na operací podporované `ObjectQuery<T>` a na podkladový zdroj dat.  
  
 V následujícím příkladu, v porovnání `Where` klauzule je výraz:  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
>  Vytvoří konkrétní jazyk, například C# `unchecked`, mít žádný význam v [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Výrazy konstant](../../../../../../docs/framework/data/adonet/ef/language-reference/constant-expressions.md)  
  
 [Výrazy porovnání](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-expressions.md)  
  
 [Porovnávání s hodnotou Null](../../../../../../docs/framework/data/adonet/ef/language-reference/null-comparisons.md)  
  
 [Výrazy inicializace](../../../../../../docs/framework/data/adonet/ef/language-reference/initialization-expressions.md)  
  
 [Navigační vlastnosti](http://msdn.microsoft.com/en-us/41e1e6b9-8a57-467d-99d9-1857d2ca2ea5)  
  
## <a name="see-also"></a>Viz také  
 [ADO.NET Entity Framework](../../../../../../docs/framework/data/adonet/ef/index.md)
