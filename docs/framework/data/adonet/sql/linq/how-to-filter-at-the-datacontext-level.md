---
title: 'Postupy: Filtr na úrovni DataContext'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 15505cd7-0df2-427a-9f86-e0f96f60ee2e
ms.openlocfilehash: 66bbfe19c73f116b8f85cae829bb61bb2da3d4c2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54644215"
---
# <a name="how-to-filter-at-the-datacontext-level"></a><span data-ttu-id="10abf-102">Postupy: Filtr na úrovni DataContext</span><span class="sxs-lookup"><span data-stu-id="10abf-102">How to: Filter at the DataContext Level</span></span>
<span data-ttu-id="10abf-103">Můžete filtrovat `EntitySets` na `DataContext` úroveň.</span><span class="sxs-lookup"><span data-stu-id="10abf-103">You can filter `EntitySets` at the `DataContext` level.</span></span> <span data-ttu-id="10abf-104">Tyto filtry vztahovat na všechny dotazy provádět s ním <xref:System.Data.Linq.DataContext> instance.</span><span class="sxs-lookup"><span data-stu-id="10abf-104">Such filters apply to all queries done with that <xref:System.Data.Linq.DataContext> instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10abf-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="10abf-105">Example</span></span>  
 <span data-ttu-id="10abf-106">V následujícím příkladu <xref:System.Data.Linq.DataLoadOptions.AssociateWith%28System.Linq.Expressions.LambdaExpression%29?displayProperty=nameWithType> slouží k filtrování už načtené objednávek zákazníků podle `ShippedDate`.</span><span class="sxs-lookup"><span data-stu-id="10abf-106">In the following example, <xref:System.Data.Linq.DataLoadOptions.AssociateWith%28System.Linq.Expressions.LambdaExpression%29?displayProperty=nameWithType> is used to filter the pre-loaded orders for customers by `ShippedDate`.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#10)]
 [!code-vb[DLinqQueryConcepts#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="10abf-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="10abf-107">See also</span></span>
- [<span data-ttu-id="10abf-108">Koncepty dotazů</span><span class="sxs-lookup"><span data-stu-id="10abf-108">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
