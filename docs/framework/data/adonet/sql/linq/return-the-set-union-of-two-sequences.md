---
title: Vrácení sjednocení množin mezi dvěma sekvencemi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
ms.openlocfilehash: 1b981d3002cf4a23897ce98927aebe96086f8a4a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781232"
---
# <a name="return-the-set-union-of-two-sequences"></a><span data-ttu-id="ae128-102">Vrácení sjednocení množin mezi dvěma sekvencemi</span><span class="sxs-lookup"><span data-stu-id="ae128-102">Return the Set Union of Two Sequences</span></span>
<span data-ttu-id="ae128-103"><xref:System.Linq.Queryable.Union%2A> Použijte operátor k vrácení sjednocení se dvěma sekvencemi.</span><span class="sxs-lookup"><span data-stu-id="ae128-103">Use the <xref:System.Linq.Queryable.Union%2A> operator to return the set union of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae128-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="ae128-104">Example</span></span>  
 <span data-ttu-id="ae128-105">Tento příklad používá <xref:System.Linq.Queryable.Union%2A> k vrácení posloupnosti všech zemí nebo oblastí, ve kterých existuje buď `Customers` nebo `Employees`.</span><span class="sxs-lookup"><span data-stu-id="ae128-105">This example uses <xref:System.Linq.Queryable.Union%2A> to return a sequence of all countries/regions in which there are either `Customers` or `Employees`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 <span data-ttu-id="ae128-106">V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]je [`UNION ALL`](https://docs.microsoft.com/sql/t-sql/language-elements/set-operators-union-transact-sql?view=sql-server-2017) operátor definován pro množiny jako neuspořádané zřetězení množin (efektivně výsledek klauzule v jazyce SQL). <xref:System.Linq.Queryable.Union%2A></span><span class="sxs-lookup"><span data-stu-id="ae128-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Union%2A> operator is defined for multisets as the unordered concatenation of the multisets (effectively the result of the [`UNION ALL`](https://docs.microsoft.com/sql/t-sql/language-elements/set-operators-union-transact-sql?view=sql-server-2017) clause in SQL).</span></span>

<span data-ttu-id="ae128-107">Další informace a příklady naleznete v tématu <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ae128-107">For more info and examples, see <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ae128-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ae128-108">See also</span></span>

- [<span data-ttu-id="ae128-109">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="ae128-109">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="ae128-110">Převod standardních operátorů dotazů</span><span class="sxs-lookup"><span data-stu-id="ae128-110">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)
