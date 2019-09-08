---
title: Vrácení prvního prvku v posloupnosti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
ms.openlocfilehash: 9faeed754942d7b176872484ac776c1df592bbd8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792719"
---
# <a name="return-the-first-element-in-a-sequence"></a><span data-ttu-id="174a0-102">Vrácení prvního prvku v posloupnosti</span><span class="sxs-lookup"><span data-stu-id="174a0-102">Return the First Element in a Sequence</span></span>
<span data-ttu-id="174a0-103"><xref:System.Linq.Enumerable.First%2A> Použijte operátor k vrácení prvního prvku v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="174a0-103">Use the <xref:System.Linq.Enumerable.First%2A> operator to return the first element in a sequence.</span></span> <span data-ttu-id="174a0-104">Dotazy, které <xref:System.Linq.Enumerable.First%2A> používají, se spustí okamžitě.</span><span class="sxs-lookup"><span data-stu-id="174a0-104">Queries that use <xref:System.Linq.Enumerable.First%2A> are executed immediately.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="174a0-105"><xref:System.Linq.Enumerable.Last%2A> nepodporuje operátor.</span><span class="sxs-lookup"><span data-stu-id="174a0-105">does not support the <xref:System.Linq.Enumerable.Last%2A> operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="174a0-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="174a0-106">Example</span></span>  
 <span data-ttu-id="174a0-107">Následující kód vyhledá první `Shipper` v tabulce:</span><span class="sxs-lookup"><span data-stu-id="174a0-107">The following code finds the first `Shipper` in a table:</span></span>  
  
 <span data-ttu-id="174a0-108">Pokud spustíte tento dotaz proti ukázkové databázi Northwind, výsledky jsou</span><span class="sxs-lookup"><span data-stu-id="174a0-108">If you run this query against the Northwind sample database, the results are</span></span>  
  
 <span data-ttu-id="174a0-109">`ID = 1, Company = Speedy Express`.</span><span class="sxs-lookup"><span data-stu-id="174a0-109">`ID = 1, Company = Speedy Express`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="174a0-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="174a0-110">Example</span></span>  
 <span data-ttu-id="174a0-111">Následující kód najde jeden `Customer` , který `CustomerID` má BONAP.</span><span class="sxs-lookup"><span data-stu-id="174a0-111">The following code finds the single `Customer` that has the `CustomerID` BONAP.</span></span>  
  
 <span data-ttu-id="174a0-112">Pokud spustíte tento dotaz proti ukázkové databázi Northwind, budou `ID = BONAP, Contact = Laurence Lebihan`výsledky.</span><span class="sxs-lookup"><span data-stu-id="174a0-112">If you run this query against the Northwind sample database, the results are `ID = BONAP, Contact = Laurence Lebihan`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="174a0-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="174a0-113">See also</span></span>

- [<span data-ttu-id="174a0-114">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="174a0-114">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="174a0-115">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="174a0-115">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
