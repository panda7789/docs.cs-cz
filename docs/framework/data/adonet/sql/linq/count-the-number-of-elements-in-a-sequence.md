---
title: Určení počtu prvků v posloupnosti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccbe5d54-c9eb-4b14-b0ab-f628483c5f99
ms.openlocfilehash: b39b0a1487c9f250e32b13330f2f70b7e3c7c877
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032920"
---
# <a name="count-the-number-of-elements-in-a-sequence"></a><span data-ttu-id="8574b-102">Určení počtu prvků v posloupnosti</span><span class="sxs-lookup"><span data-stu-id="8574b-102">Count the Number of Elements in a Sequence</span></span>
<span data-ttu-id="8574b-103">Použití <xref:System.Linq.Enumerable.Count%2A> operátor ke zjištění počtu prvků v posloupnosti.</span><span class="sxs-lookup"><span data-stu-id="8574b-103">Use the <xref:System.Linq.Enumerable.Count%2A> operator to count the number of elements in a sequence.</span></span>  
  
 <span data-ttu-id="8574b-104">Běží tento dotaz s ukázkovou databází Northwind vytvoří výstup `91`.</span><span class="sxs-lookup"><span data-stu-id="8574b-104">Running this query against the Northwind sample database produces an output of `91`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8574b-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="8574b-105">Example</span></span>  
 <span data-ttu-id="8574b-106">Následující příklad vrátí počet `Customers` v databázi.</span><span class="sxs-lookup"><span data-stu-id="8574b-106">The following example counts the number of `Customers` in the database.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#4)]
 [!code-vb[DLinqQueryExamples#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="8574b-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="8574b-107">Example</span></span>  
 <span data-ttu-id="8574b-108">Následující příklad vrátí počet produktů v databázi, které dosud nebyly vyřazeny.</span><span class="sxs-lookup"><span data-stu-id="8574b-108">The following example counts the number of products in the database that have not been discontinued.</span></span>  
  
 <span data-ttu-id="8574b-109">Spuštěním tohoto příkladu s ukázkovou databází Northwind vytvoří výstup `69`.</span><span class="sxs-lookup"><span data-stu-id="8574b-109">Running this example against the Northwind sample database produces an output of `69`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#5)]
 [!code-vb[DLinqQueryExamples#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="8574b-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8574b-110">See also</span></span>

- [<span data-ttu-id="8574b-111">Agregační dotazy</span><span class="sxs-lookup"><span data-stu-id="8574b-111">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)
- [<span data-ttu-id="8574b-112">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="8574b-112">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
