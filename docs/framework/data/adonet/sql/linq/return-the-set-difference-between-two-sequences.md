---
title: Vrácení rozdílů množin mezi dvěma sekvencemi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
ms.openlocfilehash: 282ec36a2ad489e77db9fb5b338d3189c3001f03
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609028"
---
# <a name="return-the-set-difference-between-two-sequences"></a><span data-ttu-id="3051c-102">Vrácení rozdílů množin mezi dvěma sekvencemi</span><span class="sxs-lookup"><span data-stu-id="3051c-102">Return the Set Difference Between Two Sequences</span></span>
<span data-ttu-id="3051c-103">Použití <xref:System.Linq.Queryable.Except%2A> operátor vrácení rozdílů množin mezi dvěma sekvencemi.</span><span class="sxs-lookup"><span data-stu-id="3051c-103">Use the <xref:System.Linq.Queryable.Except%2A> operator to return the set difference between two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3051c-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="3051c-104">Example</span></span>  
 <span data-ttu-id="3051c-105">Tento příklad používá <xref:System.Linq.Queryable.Except%2A> k vrácení sekvence všech zemí, ve kterém `Customers` provozu, ale v které ne `Employees` live.</span><span class="sxs-lookup"><span data-stu-id="3051c-105">This example uses <xref:System.Linq.Queryable.Except%2A> to return a sequence of all countries in which `Customers` live but in which no `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 <span data-ttu-id="3051c-106">V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Linq.Queryable.Except%2A> operace je dobře definovaný pouze na sady.</span><span class="sxs-lookup"><span data-stu-id="3051c-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Except%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="3051c-107">Sémantika pro multisets není definován.</span><span class="sxs-lookup"><span data-stu-id="3051c-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3051c-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3051c-108">See also</span></span>
- [<span data-ttu-id="3051c-109">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="3051c-109">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="3051c-110">Převod standardních operátorů dotazů</span><span class="sxs-lookup"><span data-stu-id="3051c-110">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
