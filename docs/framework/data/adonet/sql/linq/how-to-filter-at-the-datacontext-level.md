---
title: 'Postupy: Filtrování na úrovni DataContext'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 15505cd7-0df2-427a-9f86-e0f96f60ee2e
ms.openlocfilehash: 0ef5ba8e975cb1c59720c96b214ae2696cc6356e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781942"
---
# <a name="how-to-filter-at-the-datacontext-level"></a>Postupy: Filtrování na úrovni DataContext
Můžete filtrovat `EntitySets` `DataContext` na úrovni. Tyto filtry se vztahují na všechny dotazy, které <xref:System.Data.Linq.DataContext> jsou v dané instanci provedeny.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Data.Linq.DataLoadOptions.AssociateWith%28System.Linq.Expressions.LambdaExpression%29?displayProperty=nameWithType> slouží k filtrování předem načtených objednávek pro zákazníky pomocí `ShippedDate`.  
  
 [!code-csharp[DLinqQueryConcepts#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#10)]
 [!code-vb[DLinqQueryConcepts#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#10)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty dotazů](query-concepts.md)
