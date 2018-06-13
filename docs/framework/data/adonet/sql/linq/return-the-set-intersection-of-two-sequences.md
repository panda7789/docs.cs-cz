---
title: Vrátí sadu průnik dvou sekvencí
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d09c344e-3548-4944-a3ed-051880e3f5b8
ms.openlocfilehash: 9fd2a5dc435829d08594ea3c2f1c129328386250
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358781"
---
# <a name="return-the-set-intersection-of-two-sequences"></a><span data-ttu-id="6b416-102">Vrátí sadu průnik dvou sekvencí</span><span class="sxs-lookup"><span data-stu-id="6b416-102">Return the Set Intersection of Two Sequences</span></span>
<span data-ttu-id="6b416-103">Použití <xref:System.Linq.Queryable.Intersect%2A> operátor vrátit sadu průnik dvou sekvencí.</span><span class="sxs-lookup"><span data-stu-id="6b416-103">Use the <xref:System.Linq.Queryable.Intersect%2A> operator to return the set intersection of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b416-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="6b416-104">Example</span></span>  
 <span data-ttu-id="6b416-105">Tento příklad používá <xref:System.Linq.Queryable.Intersect%2A> vrátit pořadí všech zemí, ve kterých `Customers` a `Employees` za provozu.</span><span class="sxs-lookup"><span data-stu-id="6b416-105">This example uses <xref:System.Linq.Queryable.Intersect%2A> to return a sequence of all countries in which both `Customers` and `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#42](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#42)]
 [!code-vb[DLinqQueryExamples#42](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#42)]  
  
 <span data-ttu-id="6b416-106">V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Linq.Queryable.Intersect%2A> operace je dobře definované jenom na sady.</span><span class="sxs-lookup"><span data-stu-id="6b416-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Intersect%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="6b416-107">Sémantika pro multisets není definován.</span><span class="sxs-lookup"><span data-stu-id="6b416-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b416-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="6b416-108">See Also</span></span>  
 [<span data-ttu-id="6b416-109">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="6b416-109">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="6b416-110">Převod standardních operátorů dotazů</span><span class="sxs-lookup"><span data-stu-id="6b416-110">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
