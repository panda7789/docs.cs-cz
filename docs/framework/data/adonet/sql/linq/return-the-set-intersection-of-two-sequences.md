---
title: Vrácení průniku množin mezi dvěma sekvencemi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d09c344e-3548-4944-a3ed-051880e3f5b8
ms.openlocfilehash: 944d0b2efe1e74f901a493d1c3202d0f180d599d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792703"
---
# <a name="return-the-set-intersection-of-two-sequences"></a><span data-ttu-id="b87b6-102">Vrácení průniku množin mezi dvěma sekvencemi</span><span class="sxs-lookup"><span data-stu-id="b87b6-102">Return the Set Intersection of Two Sequences</span></span>
<span data-ttu-id="b87b6-103"><xref:System.Linq.Queryable.Intersect%2A> Pomocí operátoru vraťte množinu průniku dvou sekvencí.</span><span class="sxs-lookup"><span data-stu-id="b87b6-103">Use the <xref:System.Linq.Queryable.Intersect%2A> operator to return the set intersection of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b87b6-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="b87b6-104">Example</span></span>  
 <span data-ttu-id="b87b6-105">Tento příklad používá <xref:System.Linq.Queryable.Intersect%2A> k vrácení posloupnosti všech zemí nebo oblastí, ve kterých obojí `Customers` i `Employees` Live.</span><span class="sxs-lookup"><span data-stu-id="b87b6-105">This example uses <xref:System.Linq.Queryable.Intersect%2A> to return a sequence of all countries/regions in which both `Customers` and `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#42](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#42)]
 [!code-vb[DLinqQueryExamples#42](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#42)]  
  
 <span data-ttu-id="b87b6-106">V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]systémuje operacedobředefinovanápouzevsadách.<xref:System.Linq.Queryable.Intersect%2A></span><span class="sxs-lookup"><span data-stu-id="b87b6-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Intersect%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="b87b6-107">Sémantika pro více sad není definována.</span><span class="sxs-lookup"><span data-stu-id="b87b6-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b87b6-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b87b6-108">See also</span></span>

- [<span data-ttu-id="b87b6-109">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="b87b6-109">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="b87b6-110">Převod standardních operátorů dotazů</span><span class="sxs-lookup"><span data-stu-id="b87b6-110">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)
