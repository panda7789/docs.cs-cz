---
title: Vrácení rozdílu množin mezi dvěma sekvencemi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
ms.openlocfilehash: 92513ed33e2afb785edbdd462ba7bc14923aa6b0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781154"
---
# <a name="return-the-set-difference-between-two-sequences"></a><span data-ttu-id="134fa-102">Vrácení rozdílu množin mezi dvěma sekvencemi</span><span class="sxs-lookup"><span data-stu-id="134fa-102">Return the Set Difference Between Two Sequences</span></span>
<span data-ttu-id="134fa-103"><xref:System.Linq.Queryable.Except%2A> Použijte operátor k vrácení množiny rozdílů mezi dvěma sekvencemi.</span><span class="sxs-lookup"><span data-stu-id="134fa-103">Use the <xref:System.Linq.Queryable.Except%2A> operator to return the set difference between two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="134fa-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="134fa-104">Example</span></span>  
 <span data-ttu-id="134fa-105">Tento příklad používá <xref:System.Linq.Queryable.Except%2A> k vrácení posloupnosti všech zemí nebo oblastí, ve kterých `Customers` je živá, ale v `Employees` které nejsou živé.</span><span class="sxs-lookup"><span data-stu-id="134fa-105">This example uses <xref:System.Linq.Queryable.Except%2A> to return a sequence of all countries/regions in which `Customers` live but in which no `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 <span data-ttu-id="134fa-106">V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]systémuje operacedobředefinovanápouzevsadách.<xref:System.Linq.Queryable.Except%2A></span><span class="sxs-lookup"><span data-stu-id="134fa-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Except%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="134fa-107">Sémantika pro více sad není definována.</span><span class="sxs-lookup"><span data-stu-id="134fa-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="134fa-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="134fa-108">See also</span></span>

- [<span data-ttu-id="134fa-109">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="134fa-109">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="134fa-110">Převod standardních operátorů dotazů</span><span class="sxs-lookup"><span data-stu-id="134fa-110">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)
