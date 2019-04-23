---
title: Vrácení průniku množin mezi dvěma sekvencemi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d09c344e-3548-4944-a3ed-051880e3f5b8
ms.openlocfilehash: 07f48ab7ef1095ba80b1a955a4bd1ea602a75aa8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59205901"
---
# <a name="return-the-set-intersection-of-two-sequences"></a><span data-ttu-id="a5b96-102">Vrácení průniku množin mezi dvěma sekvencemi</span><span class="sxs-lookup"><span data-stu-id="a5b96-102">Return the Set Intersection of Two Sequences</span></span>
<span data-ttu-id="a5b96-103">Použití <xref:System.Linq.Queryable.Intersect%2A> operátor se vraťte průniku množin mezi dvěma sekvencemi.</span><span class="sxs-lookup"><span data-stu-id="a5b96-103">Use the <xref:System.Linq.Queryable.Intersect%2A> operator to return the set intersection of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5b96-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="a5b96-104">Example</span></span>  
 <span data-ttu-id="a5b96-105">Tento příklad používá <xref:System.Linq.Queryable.Intersect%2A> k vrácení sekvence všech zemí, ve kterých `Customers` a `Employees` live.</span><span class="sxs-lookup"><span data-stu-id="a5b96-105">This example uses <xref:System.Linq.Queryable.Intersect%2A> to return a sequence of all countries in which both `Customers` and `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#42](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#42)]
 [!code-vb[DLinqQueryExamples#42](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#42)]  
  
 <span data-ttu-id="a5b96-106">V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Linq.Queryable.Intersect%2A> operace je dobře definovaný pouze na sady.</span><span class="sxs-lookup"><span data-stu-id="a5b96-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Intersect%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="a5b96-107">Sémantika pro multisets není definován.</span><span class="sxs-lookup"><span data-stu-id="a5b96-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5b96-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a5b96-108">See also</span></span>

- [<span data-ttu-id="a5b96-109">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="a5b96-109">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="a5b96-110">Převod standardních operátorů dotazů</span><span class="sxs-lookup"><span data-stu-id="a5b96-110">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
