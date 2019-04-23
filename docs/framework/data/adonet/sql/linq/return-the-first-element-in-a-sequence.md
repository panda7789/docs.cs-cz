---
title: Vrácení prvního prvku v posloupnosti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
ms.openlocfilehash: dca917b3c12b0f9923cc9ea34a2568c412a09831
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59081818"
---
# <a name="return-the-first-element-in-a-sequence"></a><span data-ttu-id="8e613-102">Vrácení prvního prvku v posloupnosti</span><span class="sxs-lookup"><span data-stu-id="8e613-102">Return the First Element in a Sequence</span></span>
<span data-ttu-id="8e613-103">Použití <xref:System.Linq.Enumerable.First%2A> operátor vrátí první prvek v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="8e613-103">Use the <xref:System.Linq.Enumerable.First%2A> operator to return the first element in a sequence.</span></span> <span data-ttu-id="8e613-104">Dotazy, které používají <xref:System.Linq.Enumerable.First%2A> provádějí okamžitě.</span><span class="sxs-lookup"><span data-stu-id="8e613-104">Queries that use <xref:System.Linq.Enumerable.First%2A> are executed immediately.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="8e613-105">nepodporuje <xref:System.Linq.Enumerable.Last%2A> operátor.</span><span class="sxs-lookup"><span data-stu-id="8e613-105">does not support the <xref:System.Linq.Enumerable.Last%2A> operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e613-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="8e613-106">Example</span></span>  
 <span data-ttu-id="8e613-107">Následující kód najde první `Shipper` v tabulce:</span><span class="sxs-lookup"><span data-stu-id="8e613-107">The following code finds the first `Shipper` in a table:</span></span>  
  
 <span data-ttu-id="8e613-108">Pokud spouštíte skript v ukázkové databázi Northwind tento dotaz, jsou výsledky</span><span class="sxs-lookup"><span data-stu-id="8e613-108">If you run this query against the Northwind sample database, the results are</span></span>  
  
 <span data-ttu-id="8e613-109">`ID = 1, Company = Speedy Express`.</span><span class="sxs-lookup"><span data-stu-id="8e613-109">`ID = 1, Company = Speedy Express`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="8e613-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="8e613-110">Example</span></span>  
 <span data-ttu-id="8e613-111">Následující kód najde jedné `Customer` , který má `CustomerID` BONAP.</span><span class="sxs-lookup"><span data-stu-id="8e613-111">The following code finds the single `Customer` that has the `CustomerID` BONAP.</span></span>  
  
 <span data-ttu-id="8e613-112">Pokud spouštíte skript v ukázkové databázi Northwind tento dotaz, výsledky jsou `ID = BONAP, Contact = Laurence Lebihan`.</span><span class="sxs-lookup"><span data-stu-id="8e613-112">If you run this query against the Northwind sample database, the results are `ID = BONAP, Contact = Laurence Lebihan`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="8e613-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8e613-113">See also</span></span>

- [<span data-ttu-id="8e613-114">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="8e613-114">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="8e613-115">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="8e613-115">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
