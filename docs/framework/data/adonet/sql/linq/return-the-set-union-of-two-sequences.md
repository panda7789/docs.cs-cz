---
title: Vrácení sjednocení množin mezi dvěma sekvencemi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
ms.openlocfilehash: a2d51e8052c839ea4cd11dec07a3aef95d59d0f1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54546959"
---
# <a name="return-the-set-union-of-two-sequences"></a><span data-ttu-id="04567-102">Vrácení sjednocení množin mezi dvěma sekvencemi</span><span class="sxs-lookup"><span data-stu-id="04567-102">Return the Set Union of Two Sequences</span></span>
<span data-ttu-id="04567-103">Použití <xref:System.Linq.Queryable.Union%2A> operátor vrácení sjednocení množin mezi dvěma sekvencemi.</span><span class="sxs-lookup"><span data-stu-id="04567-103">Use the <xref:System.Linq.Queryable.Union%2A> operator to return the set union of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04567-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="04567-104">Example</span></span>  
 <span data-ttu-id="04567-105">Tento příklad používá <xref:System.Linq.Queryable.Union%2A> k vrácení sekvence všechny země, ve kterém se buď `Customers` nebo `Employees`.</span><span class="sxs-lookup"><span data-stu-id="04567-105">This example uses <xref:System.Linq.Queryable.Union%2A> to return a sequence of all countries in which there are either `Customers` or `Employees`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 <span data-ttu-id="04567-106">V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Linq.Queryable.Union%2A> operátor je pro multisets definován jako Neseřazený zřetězení multisets (efektivně výsledek [ `UNION ALL` ](https://docs.microsoft.com/sql/t-sql/language-elements/set-operators-union-transact-sql?view=sql-server-2017) klauzuli v SQL).</span><span class="sxs-lookup"><span data-stu-id="04567-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Union%2A> operator is defined for multisets as the unordered concatenation of the multisets (effectively the result of the [`UNION ALL`](https://docs.microsoft.com/sql/t-sql/language-elements/set-operators-union-transact-sql?view=sql-server-2017) clause in SQL).</span></span>

<span data-ttu-id="04567-107">Další informace a příklady najdete v tématu <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="04567-107">For more info and examples, see <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="04567-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="04567-108">See also</span></span>
- [<span data-ttu-id="04567-109">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="04567-109">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="04567-110">Převod standardních operátorů dotazů</span><span class="sxs-lookup"><span data-stu-id="04567-110">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
