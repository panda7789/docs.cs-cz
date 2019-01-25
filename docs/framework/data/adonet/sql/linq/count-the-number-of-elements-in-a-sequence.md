---
title: Počet prvků v posloupnosti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccbe5d54-c9eb-4b14-b0ab-f628483c5f99
ms.openlocfilehash: 546417cc0b4aed7fa092ddb25fe37fa8d95d0e91
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54510479"
---
# <a name="count-the-number-of-elements-in-a-sequence"></a><span data-ttu-id="4bac2-102">Počet prvků v posloupnosti</span><span class="sxs-lookup"><span data-stu-id="4bac2-102">Count the Number of Elements in a Sequence</span></span>
<span data-ttu-id="4bac2-103">Použití <xref:System.Linq.Enumerable.Count%2A> operátor ke zjištění počtu prvků v posloupnosti.</span><span class="sxs-lookup"><span data-stu-id="4bac2-103">Use the <xref:System.Linq.Enumerable.Count%2A> operator to count the number of elements in a sequence.</span></span>  
  
 <span data-ttu-id="4bac2-104">Běží tento dotaz s ukázkovou databází Northwind vytvoří výstup `91`.</span><span class="sxs-lookup"><span data-stu-id="4bac2-104">Running this query against the Northwind sample database produces an output of `91`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4bac2-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="4bac2-105">Example</span></span>  
 <span data-ttu-id="4bac2-106">Následující příklad vrátí počet `Customers` v databázi.</span><span class="sxs-lookup"><span data-stu-id="4bac2-106">The following example counts the number of `Customers` in the database.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#4)]
 [!code-vb[DLinqQueryExamples#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="4bac2-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="4bac2-107">Example</span></span>  
 <span data-ttu-id="4bac2-108">Následující příklad vrátí počet produktů v databázi, které dosud nebyly vyřazeny.</span><span class="sxs-lookup"><span data-stu-id="4bac2-108">The following example counts the number of products in the database that have not been discontinued.</span></span>  
  
 <span data-ttu-id="4bac2-109">Spuštěním tohoto příkladu s ukázkovou databází Northwind vytvoří výstup `69`.</span><span class="sxs-lookup"><span data-stu-id="4bac2-109">Running this example against the Northwind sample database produces an output of `69`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#5)]
 [!code-vb[DLinqQueryExamples#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="4bac2-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4bac2-110">See also</span></span>
- [<span data-ttu-id="4bac2-111">Agregační dotazy</span><span class="sxs-lookup"><span data-stu-id="4bac2-111">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)
- [<span data-ttu-id="4bac2-112">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="4bac2-112">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
