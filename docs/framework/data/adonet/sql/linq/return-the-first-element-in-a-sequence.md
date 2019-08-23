---
title: Vrácení prvního prvku v posloupnosti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
ms.openlocfilehash: 39cf9270b08fce64590fef418bb428c5a781b0e9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963810"
---
# <a name="return-the-first-element-in-a-sequence"></a><span data-ttu-id="37104-102">Vrácení prvního prvku v posloupnosti</span><span class="sxs-lookup"><span data-stu-id="37104-102">Return the First Element in a Sequence</span></span>
<span data-ttu-id="37104-103"><xref:System.Linq.Enumerable.First%2A> Použijte operátor k vrácení prvního prvku v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="37104-103">Use the <xref:System.Linq.Enumerable.First%2A> operator to return the first element in a sequence.</span></span> <span data-ttu-id="37104-104">Dotazy, které <xref:System.Linq.Enumerable.First%2A> používají, se spustí okamžitě.</span><span class="sxs-lookup"><span data-stu-id="37104-104">Queries that use <xref:System.Linq.Enumerable.First%2A> are executed immediately.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="37104-105"><xref:System.Linq.Enumerable.Last%2A> nepodporuje operátor.</span><span class="sxs-lookup"><span data-stu-id="37104-105">does not support the <xref:System.Linq.Enumerable.Last%2A> operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37104-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="37104-106">Example</span></span>  
 <span data-ttu-id="37104-107">Následující kód vyhledá první `Shipper` v tabulce:</span><span class="sxs-lookup"><span data-stu-id="37104-107">The following code finds the first `Shipper` in a table:</span></span>  
  
 <span data-ttu-id="37104-108">Pokud spustíte tento dotaz proti ukázkové databázi Northwind, výsledky jsou</span><span class="sxs-lookup"><span data-stu-id="37104-108">If you run this query against the Northwind sample database, the results are</span></span>  
  
 <span data-ttu-id="37104-109">`ID = 1, Company = Speedy Express`.</span><span class="sxs-lookup"><span data-stu-id="37104-109">`ID = 1, Company = Speedy Express`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="37104-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="37104-110">Example</span></span>  
 <span data-ttu-id="37104-111">Následující kód najde jeden `Customer` , který `CustomerID` má BONAP.</span><span class="sxs-lookup"><span data-stu-id="37104-111">The following code finds the single `Customer` that has the `CustomerID` BONAP.</span></span>  
  
 <span data-ttu-id="37104-112">Pokud spustíte tento dotaz proti ukázkové databázi Northwind, budou `ID = BONAP, Contact = Laurence Lebihan`výsledky.</span><span class="sxs-lookup"><span data-stu-id="37104-112">If you run this query against the Northwind sample database, the results are `ID = BONAP, Contact = Laurence Lebihan`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="37104-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="37104-113">See also</span></span>

- [<span data-ttu-id="37104-114">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="37104-114">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="37104-115">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="37104-115">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
