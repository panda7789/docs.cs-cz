---
title: Vrácení sjednocení množin mezi dvěma sekvencemi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
ms.openlocfilehash: 058856243b2a8daaecd653a9b5999013de5407a8
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182525"
---
# <a name="return-the-set-union-of-two-sequences"></a><span data-ttu-id="f24e8-102">Vrácení sjednocení množin mezi dvěma sekvencemi</span><span class="sxs-lookup"><span data-stu-id="f24e8-102">Return the Set Union of Two Sequences</span></span>
<span data-ttu-id="f24e8-103"><xref:System.Linq.Queryable.Union%2A> Použijte operátor k vrácení sjednocení se dvěma sekvencemi.</span><span class="sxs-lookup"><span data-stu-id="f24e8-103">Use the <xref:System.Linq.Queryable.Union%2A> operator to return the set union of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f24e8-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="f24e8-104">Example</span></span>  
 <span data-ttu-id="f24e8-105">Tento příklad používá <xref:System.Linq.Queryable.Union%2A> k vrácení posloupnosti všech zemí nebo oblastí, ve kterých existuje buď `Customers` nebo `Employees`.</span><span class="sxs-lookup"><span data-stu-id="f24e8-105">This example uses <xref:System.Linq.Queryable.Union%2A> to return a sequence of all countries/regions in which there are either `Customers` or `Employees`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 <span data-ttu-id="f24e8-106">V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]je [`UNION ALL`](/sql/t-sql/language-elements/set-operators-union-transact-sql) operátor definován pro množiny jako neuspořádané zřetězení množin (efektivně výsledek klauzule v jazyce SQL). <xref:System.Linq.Queryable.Union%2A></span><span class="sxs-lookup"><span data-stu-id="f24e8-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Union%2A> operator is defined for multisets as the unordered concatenation of the multisets (effectively the result of the [`UNION ALL`](/sql/t-sql/language-elements/set-operators-union-transact-sql) clause in SQL).</span></span>

<span data-ttu-id="f24e8-107">Další informace a příklady naleznete v tématu <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f24e8-107">For more info and examples, see <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f24e8-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f24e8-108">See also</span></span>

- [<span data-ttu-id="f24e8-109">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="f24e8-109">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="f24e8-110">Převod standardních operátorů dotazů</span><span class="sxs-lookup"><span data-stu-id="f24e8-110">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)
