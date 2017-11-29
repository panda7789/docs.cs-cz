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
ms.openlocfilehash: 69b711802d04e005095167db7df544e0f00d0b19
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-filter-at-the-datacontext-level"></a><span data-ttu-id="0fd5e-102">Postupy: filtru na úrovni DataContext</span><span class="sxs-lookup"><span data-stu-id="0fd5e-102">How to: Filter at the DataContext Level</span></span>
<span data-ttu-id="0fd5e-103">Můžete filtrovat `EntitySets` na `DataContext` úroveň.</span><span class="sxs-lookup"><span data-stu-id="0fd5e-103">You can filter `EntitySets` at the `DataContext` level.</span></span> <span data-ttu-id="0fd5e-104">Tyto filtry platí pro všechny dotazy pracovat, <xref:System.Data.Linq.DataContext> instance.</span><span class="sxs-lookup"><span data-stu-id="0fd5e-104">Such filters apply to all queries done with that <xref:System.Data.Linq.DataContext> instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fd5e-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="0fd5e-105">Example</span></span>  
 <span data-ttu-id="0fd5e-106">V následujícím příkladu <xref:System.Data.Linq.DataLoadOptions.AssociateWith%28System.Linq.Expressions.LambdaExpression%29?displayProperty=nameWithType> se používá k filtrování předem načtený objednávky pro zákazníky podle `ShippedDate`.</span><span class="sxs-lookup"><span data-stu-id="0fd5e-106">In the following example, <xref:System.Data.Linq.DataLoadOptions.AssociateWith%28System.Linq.Expressions.LambdaExpression%29?displayProperty=nameWithType> is used to filter the pre-loaded orders for customers by `ShippedDate`.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#10)]
 [!code-vb[DLinqQueryConcepts#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="0fd5e-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="0fd5e-107">See Also</span></span>  
 [<span data-ttu-id="0fd5e-108">Koncepty dotazu</span><span class="sxs-lookup"><span data-stu-id="0fd5e-108">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
