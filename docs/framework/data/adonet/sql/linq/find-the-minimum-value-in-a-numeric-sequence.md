---
title: "Vrátí minimální hodnotu číselného pořadí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 78203093-f242-4572-9b31-9495b10926aa
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a042d1b1e78afee632dea20bbafe2383e50430c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="find-the-minimum-value-in-a-numeric-sequence"></a><span data-ttu-id="2950b-102">Vrátí minimální hodnotu číselného pořadí</span><span class="sxs-lookup"><span data-stu-id="2950b-102">Find the Minimum Value in a Numeric Sequence</span></span>
<span data-ttu-id="2950b-103">Použití <xref:System.Linq.Enumerable.Min%2A> operátor se vrátí minimální hodnotu ze posloupnost číselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2950b-103">Use the <xref:System.Linq.Enumerable.Min%2A> operator to return the minimum value from a sequence of numeric values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2950b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="2950b-104">Example</span></span>  
 <span data-ttu-id="2950b-105">Následující příklad vyhledá nejnižší jednotkové ceny všech produktů.</span><span class="sxs-lookup"><span data-stu-id="2950b-105">The following example finds the lowest unit price of any product.</span></span>  
  
 <span data-ttu-id="2950b-106">Pokud spustíte tento dotaz proti ukázková databáze Northwind, je výstup: `2.5000`.</span><span class="sxs-lookup"><span data-stu-id="2950b-106">If you run this query against the Northwind sample database, the output is: `2.5000`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#9)]
 [!code-vb[DLinqQueryExamples#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="2950b-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="2950b-107">Example</span></span>  
 <span data-ttu-id="2950b-108">Následující příklad vyhledá nejnižší velikost nákladní pro libovolném pořadí.</span><span class="sxs-lookup"><span data-stu-id="2950b-108">The following example finds the lowest freight amount for any order.</span></span>  
  
 <span data-ttu-id="2950b-109">Pokud spustíte tento dotaz proti ukázková databáze Northwind, je výstup: `0.0200`.</span><span class="sxs-lookup"><span data-stu-id="2950b-109">If you run this query against the Northwind sample database, the output is: `0.0200`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#10)]
 [!code-vb[DLinqQueryExamples#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="2950b-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="2950b-110">Example</span></span>  
 <span data-ttu-id="2950b-111">Následující příklad používá k nalezení Min `Products` mají nejnižší jednotkové ceny v každé kategorii.</span><span class="sxs-lookup"><span data-stu-id="2950b-111">The following example uses Min to find the `Products` that have the lowest unit price in each category.</span></span> <span data-ttu-id="2950b-112">Výstup uspořádána podle kategorie.</span><span class="sxs-lookup"><span data-stu-id="2950b-112">The output is arranged by category.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#11](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#11)]
 [!code-vb[DLinqQueryExamples#11](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#11)]  
  
 <span data-ttu-id="2950b-113">Pokud spustíte předchozí dotaz proti ukázková databáze Northwind, výsledky budou vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="2950b-113">If you run the previous query against the Northwind sample database, your results will resemble the following:</span></span>  
  
 `1`  
  
 `Guaraná Fantástica`  
  
 `2`  
  
 `Aniseed Syrup`  
  
 `3`  
  
 `Teatime Chocolate Biscuits`  
  
 `4`  
  
 `Geitost`  
  
 `5`  
  
 `Filo Mix`  
  
 `6`  
  
 `Tourtière`  
  
 `7`  
  
 `Longlife Tofu`  
  
 `8`  
  
 `Konbu`  
  
## <a name="see-also"></a><span data-ttu-id="2950b-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="2950b-114">See Also</span></span>  
 [<span data-ttu-id="2950b-115">Agregační dotazy</span><span class="sxs-lookup"><span data-stu-id="2950b-115">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 [<span data-ttu-id="2950b-116">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="2950b-116">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
