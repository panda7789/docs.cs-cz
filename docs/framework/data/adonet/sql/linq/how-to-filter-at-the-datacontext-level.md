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
# <a name="how-to-filter-at-the-datacontext-level"></a><span data-ttu-id="a0b27-102">Postupy: filtru na úrovni DataContext</span><span class="sxs-lookup"><span data-stu-id="a0b27-102">How to: Filter at the DataContext Level</span></span>
<span data-ttu-id="a0b27-103">Můžete filtrovat `EntitySets` na `DataContext` úroveň.</span><span class="sxs-lookup"><span data-stu-id="a0b27-103">You can filter `EntitySets` at the `DataContext` level.</span></span> <span data-ttu-id="a0b27-104">Tyto filtry platí pro všechny dotazy pracovat, <xref:System.Data.Linq.DataContext> instance.</span><span class="sxs-lookup"><span data-stu-id="a0b27-104">Such filters apply to all queries done with that <xref:System.Data.Linq.DataContext> instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0b27-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="a0b27-105">Example</span></span>  
 <span data-ttu-id="a0b27-106">V následujícím příkladu <xref:System.Data.Linq.DataLoadOptions.AssociateWith%28System.Linq.Expressions.LambdaExpression%29?displayProperty=nameWithType> se používá k filtrování předem načtený objednávky pro zákazníky podle `ShippedDate`.</span><span class="sxs-lookup"><span data-stu-id="a0b27-106">In the following example, <xref:System.Data.Linq.DataLoadOptions.AssociateWith%28System.Linq.Expressions.LambdaExpression%29?displayProperty=nameWithType> is used to filter the pre-loaded orders for customers by `ShippedDate`.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#10)]
 [!code-vb[DLinqQueryConcepts#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="a0b27-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0b27-107">See Also</span></span>  
 [<span data-ttu-id="a0b27-108">Koncepty dotazů</span><span class="sxs-lookup"><span data-stu-id="a0b27-108">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
