---
title: Počet elementů v pořadí
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccbe5d54-c9eb-4b14-b0ab-f628483c5f99
ms.openlocfilehash: 928cfd33a187637c6d18da3cccefb22bb2950acf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353831"
---
# <a name="count-the-number-of-elements-in-a-sequence"></a><span data-ttu-id="2d491-102">Počet elementů v pořadí</span><span class="sxs-lookup"><span data-stu-id="2d491-102">Count the Number of Elements in a Sequence</span></span>
<span data-ttu-id="2d491-103">Použití <xref:System.Linq.Enumerable.Count%2A> operátor počítat počet elementů v pořadí.</span><span class="sxs-lookup"><span data-stu-id="2d491-103">Use the <xref:System.Linq.Enumerable.Count%2A> operator to count the number of elements in a sequence.</span></span>  
  
 <span data-ttu-id="2d491-104">Spusťte tento dotaz proti ukázková databáze Northwind vytváří výstup `91`.</span><span class="sxs-lookup"><span data-stu-id="2d491-104">Running this query against the Northwind sample database produces an output of `91`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d491-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="2d491-105">Example</span></span>  
 <span data-ttu-id="2d491-106">Následující příklad vrátí počet `Customers` v databázi.</span><span class="sxs-lookup"><span data-stu-id="2d491-106">The following example counts the number of `Customers` in the database.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#4)]
 [!code-vb[DLinqQueryExamples#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="2d491-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="2d491-107">Example</span></span>  
 <span data-ttu-id="2d491-108">Následující příklad vrátí počet produktů v databázi, které se již.</span><span class="sxs-lookup"><span data-stu-id="2d491-108">The following example counts the number of products in the database that have not been discontinued.</span></span>  
  
 <span data-ttu-id="2d491-109">Tento příklad spuštěn proti ukázková databáze Northwind vytváří výstup `69`.</span><span class="sxs-lookup"><span data-stu-id="2d491-109">Running this example against the Northwind sample database produces an output of `69`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#5)]
 [!code-vb[DLinqQueryExamples#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="2d491-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="2d491-110">See Also</span></span>  
 [<span data-ttu-id="2d491-111">Agregační dotazy</span><span class="sxs-lookup"><span data-stu-id="2d491-111">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 [<span data-ttu-id="2d491-112">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="2d491-112">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
