---
title: Určení počtu prvků v posloupnosti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccbe5d54-c9eb-4b14-b0ab-f628483c5f99
ms.openlocfilehash: 74e24aeb64b0097cba3975e76475034e6bb9544d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247705"
---
# <a name="count-the-number-of-elements-in-a-sequence"></a><span data-ttu-id="ecc2d-102">Určení počtu prvků v posloupnosti</span><span class="sxs-lookup"><span data-stu-id="ecc2d-102">Count the Number of Elements in a Sequence</span></span>
<span data-ttu-id="ecc2d-103"><xref:System.Linq.Enumerable.Count%2A> Pomocí operátoru můžete spočítat počet prvků v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="ecc2d-103">Use the <xref:System.Linq.Enumerable.Count%2A> operator to count the number of elements in a sequence.</span></span>  
  
 <span data-ttu-id="ecc2d-104">Spuštění tohoto dotazu proti ukázkové databázi Northwind vytvoří výstup `91`.</span><span class="sxs-lookup"><span data-stu-id="ecc2d-104">Running this query against the Northwind sample database produces an output of `91`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ecc2d-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="ecc2d-105">Example</span></span>  
 <span data-ttu-id="ecc2d-106">Následující příklad spočítá počet `Customers` v databázi.</span><span class="sxs-lookup"><span data-stu-id="ecc2d-106">The following example counts the number of `Customers` in the database.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#4)]
 [!code-vb[DLinqQueryExamples#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="ecc2d-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="ecc2d-107">Example</span></span>  
 <span data-ttu-id="ecc2d-108">Následující příklad spočítá počet produktů v databázi, které nebyly ukončeny.</span><span class="sxs-lookup"><span data-stu-id="ecc2d-108">The following example counts the number of products in the database that have not been discontinued.</span></span>  
  
 <span data-ttu-id="ecc2d-109">Spuštění tohoto příkladu pro ukázkovou databázi Northwind vytvoří výstup `69`.</span><span class="sxs-lookup"><span data-stu-id="ecc2d-109">Running this example against the Northwind sample database produces an output of `69`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#5)]
 [!code-vb[DLinqQueryExamples#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="ecc2d-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ecc2d-110">See also</span></span>

- [<span data-ttu-id="ecc2d-111">Agregační dotazy</span><span class="sxs-lookup"><span data-stu-id="ecc2d-111">Aggregate Queries</span></span>](aggregate-queries.md)
- [<span data-ttu-id="ecc2d-112">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="ecc2d-112">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
