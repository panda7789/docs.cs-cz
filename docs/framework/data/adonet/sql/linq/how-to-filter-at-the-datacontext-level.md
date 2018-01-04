---
title: "Postupy: filtru na úrovni DataContext"
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
ms.assetid: 15505cd7-0df2-427a-9f86-e0f96f60ee2e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 0b596a16a6bf11982ba6edd4a646b46fa22d3e3b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-filter-at-the-datacontext-level"></a>Postupy: filtru na úrovni DataContext
Můžete filtrovat `EntitySets` na `DataContext` úroveň. Tyto filtry platí pro všechny dotazy pracovat, <xref:System.Data.Linq.DataContext> instance.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Data.Linq.DataLoadOptions.AssociateWith%28System.Linq.Expressions.LambdaExpression%29?displayProperty=nameWithType> se používá k filtrování předem načtený objednávky pro zákazníky podle `ShippedDate`.  
  
 [!code-csharp[DLinqQueryConcepts#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#10)]
 [!code-vb[DLinqQueryConcepts#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#10)]  
  
## <a name="see-also"></a>Viz také  
 [Koncepty dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
