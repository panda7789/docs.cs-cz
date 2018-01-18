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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 9cc16b09912cb9cc695fc350d9fd4530ea99e794
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="find-the-minimum-value-in-a-numeric-sequence"></a><span data-ttu-id="4e748-102">Vrátí minimální hodnotu číselného pořadí</span><span class="sxs-lookup"><span data-stu-id="4e748-102">Find the Minimum Value in a Numeric Sequence</span></span>
<span data-ttu-id="4e748-103">Použití <xref:System.Linq.Enumerable.Min%2A> operátor se vrátí minimální hodnotu ze posloupnost číselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4e748-103">Use the <xref:System.Linq.Enumerable.Min%2A> operator to return the minimum value from a sequence of numeric values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e748-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="4e748-104">Example</span></span>  
 <span data-ttu-id="4e748-105">Následující příklad vyhledá nejnižší jednotkové ceny všech produktů.</span><span class="sxs-lookup"><span data-stu-id="4e748-105">The following example finds the lowest unit price of any product.</span></span>  
  
 <span data-ttu-id="4e748-106">Pokud spustíte tento dotaz proti ukázková databáze Northwind, je výstup: `2.5000`.</span><span class="sxs-lookup"><span data-stu-id="4e748-106">If you run this query against the Northwind sample database, the output is: `2.5000`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#9)]
 [!code-vb[DLinqQueryExamples#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="4e748-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="4e748-107">Example</span></span>  
 <span data-ttu-id="4e748-108">Následující příklad vyhledá nejnižší velikost nákladní pro libovolném pořadí.</span><span class="sxs-lookup"><span data-stu-id="4e748-108">The following example finds the lowest freight amount for any order.</span></span>  
  
 <span data-ttu-id="4e748-109">Pokud spustíte tento dotaz proti ukázková databáze Northwind, je výstup: `0.0200`.</span><span class="sxs-lookup"><span data-stu-id="4e748-109">If you run this query against the Northwind sample database, the output is: `0.0200`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#10)]
 [!code-vb[DLinqQueryExamples#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="4e748-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="4e748-110">Example</span></span>  
 <span data-ttu-id="4e748-111">Následující příklad používá k nalezení Min `Products` mají nejnižší jednotkové ceny v každé kategorii.</span><span class="sxs-lookup"><span data-stu-id="4e748-111">The following example uses Min to find the `Products` that have the lowest unit price in each category.</span></span> <span data-ttu-id="4e748-112">Výstup uspořádána podle kategorie.</span><span class="sxs-lookup"><span data-stu-id="4e748-112">The output is arranged by category.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#11](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#11)]
 [!code-vb[DLinqQueryExamples#11](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#11)]  
  
 <span data-ttu-id="4e748-113">Pokud spustíte předchozí dotaz proti ukázková databáze Northwind, výsledky budou vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="4e748-113">If you run the previous query against the Northwind sample database, your results will resemble the following:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4e748-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="4e748-114">See Also</span></span>  
 [<span data-ttu-id="4e748-115">Agregační dotazy</span><span class="sxs-lookup"><span data-stu-id="4e748-115">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 [<span data-ttu-id="4e748-116">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="4e748-116">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
