---
title: 'Postupy: filtru na úrovni DataContext'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 15505cd7-0df2-427a-9f86-e0f96f60ee2e
ms.openlocfilehash: c04be0bb955cff4bf796d14d45b39cac7ce4352d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354930"
---
# <a name="how-to-filter-at-the-datacontext-level"></a>Postupy: filtru na úrovni DataContext
Můžete filtrovat `EntitySets` na `DataContext` úroveň. Tyto filtry platí pro všechny dotazy pracovat, <xref:System.Data.Linq.DataContext> instance.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Data.Linq.DataLoadOptions.AssociateWith%28System.Linq.Expressions.LambdaExpression%29?displayProperty=nameWithType> se používá k filtrování předem načtený objednávky pro zákazníky podle `ShippedDate`.  
  
 [!code-csharp[DLinqQueryConcepts#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#10)]
 [!code-vb[DLinqQueryConcepts#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#10)]  
  
## <a name="see-also"></a>Viz také  
 [Koncepty dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
