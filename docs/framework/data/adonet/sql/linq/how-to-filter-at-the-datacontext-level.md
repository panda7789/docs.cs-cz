---
title: 'Postupy: Filtrování na úrovni DataContext'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 15505cd7-0df2-427a-9f86-e0f96f60ee2e
ms.openlocfilehash: 343cffa9b1c034068e5abcc652e936f89ee6a992
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61903003"
---
# <a name="how-to-filter-at-the-datacontext-level"></a><span data-ttu-id="4a1c8-102">Postupy: Filtrování na úrovni DataContext</span><span class="sxs-lookup"><span data-stu-id="4a1c8-102">How to: Filter at the DataContext Level</span></span>
<span data-ttu-id="4a1c8-103">Můžete filtrovat `EntitySets` na `DataContext` úroveň.</span><span class="sxs-lookup"><span data-stu-id="4a1c8-103">You can filter `EntitySets` at the `DataContext` level.</span></span> <span data-ttu-id="4a1c8-104">Tyto filtry vztahovat na všechny dotazy provádět s ním <xref:System.Data.Linq.DataContext> instance.</span><span class="sxs-lookup"><span data-stu-id="4a1c8-104">Such filters apply to all queries done with that <xref:System.Data.Linq.DataContext> instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a1c8-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="4a1c8-105">Example</span></span>  
 <span data-ttu-id="4a1c8-106">V následujícím příkladu <xref:System.Data.Linq.DataLoadOptions.AssociateWith%28System.Linq.Expressions.LambdaExpression%29?displayProperty=nameWithType> slouží k filtrování už načtené objednávek zákazníků podle `ShippedDate`.</span><span class="sxs-lookup"><span data-stu-id="4a1c8-106">In the following example, <xref:System.Data.Linq.DataLoadOptions.AssociateWith%28System.Linq.Expressions.LambdaExpression%29?displayProperty=nameWithType> is used to filter the pre-loaded orders for customers by `ShippedDate`.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#10)]
 [!code-vb[DLinqQueryConcepts#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="4a1c8-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4a1c8-107">See also</span></span>

- [<span data-ttu-id="4a1c8-108">Koncepty dotazů</span><span class="sxs-lookup"><span data-stu-id="4a1c8-108">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
