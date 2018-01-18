---
title: "Vrátí maximální hodnotu číselného pořadí"
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
ms.assetid: 70d7c058-0280-4815-a008-6f290093591a
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 028a8e4a7fa215b0bdbce1de92c20dc51a15faa6
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="find-the-maximum-value-in-a-numeric-sequence"></a><span data-ttu-id="1ed58-102">Vrátí maximální hodnotu číselného pořadí</span><span class="sxs-lookup"><span data-stu-id="1ed58-102">Find the Maximum Value in a Numeric Sequence</span></span>
<span data-ttu-id="1ed58-103">Použití <xref:System.Linq.Enumerable.Max%2A> operátor a vyhledá nejvyšší hodnotu v sekvenci číselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1ed58-103">Use the <xref:System.Linq.Enumerable.Max%2A> operator to find the highest value in a sequence of numeric values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ed58-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="1ed58-104">Example</span></span>  
 <span data-ttu-id="1ed58-105">Následující příklad vyhledá nejnovější data přijetím pro všechny zaměstnance.</span><span class="sxs-lookup"><span data-stu-id="1ed58-105">The following example finds the latest date of hire for any employee.</span></span>  
  
 <span data-ttu-id="1ed58-106">Pokud spustíte tento dotaz pro ukázkové databázi Northwind, je výstup: `11/15/1994 12:00:00 AM`.</span><span class="sxs-lookup"><span data-stu-id="1ed58-106">If you run this query against the sample Northwind database, the output is: `11/15/1994 12:00:00 AM`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#6)]
 [!code-vb[DLinqQueryExamples#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="1ed58-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="1ed58-107">Example</span></span>  
 <span data-ttu-id="1ed58-108">Následující příklad vyhledá v stock většina jednotky pro některý z produktů.</span><span class="sxs-lookup"><span data-stu-id="1ed58-108">The following example finds the most units in stock for any product.</span></span>  
  
 <span data-ttu-id="1ed58-109">Pokud spustíte v tomto příkladu v ukázkové databázi Northwind, je výstup: `125`.</span><span class="sxs-lookup"><span data-stu-id="1ed58-109">If you run this example against the sample Northwind database, the output is: `125`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#7)]
 [!code-vb[DLinqQueryExamples#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#7)]  
  
## <a name="example"></a><span data-ttu-id="1ed58-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="1ed58-110">Example</span></span>  
 <span data-ttu-id="1ed58-111">Následující příklad používá k nalezení maximální `Products` které mají nejvyšší jednotkové ceny v každé kategorii.</span><span class="sxs-lookup"><span data-stu-id="1ed58-111">The following example uses Max to find the `Products` that have the highest unit price in each category.</span></span> <span data-ttu-id="1ed58-112">Výstup jsou výsledky pak uvedené podle kategorie.</span><span class="sxs-lookup"><span data-stu-id="1ed58-112">The output then lists the results by category.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#8)]
 [!code-vb[DLinqQueryExamples#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#8)]  
  
 <span data-ttu-id="1ed58-113">Pokud spustíte předchozí dotaz proti ukázková databáze Northwind, výsledky budou vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="1ed58-113">If you run the previous query against the Northwind sample database, your results will resemble the following:</span></span>  
  
 `1`  
  
 `Côte de Blaye`  
  
 `2`  
  
 `Vegie-spread`  
  
 `3`  
  
 `Sir Rodney's Marmalade`  
  
 `4`  
  
 `Raclette Courdavault`  
  
 `5`  
  
 `Gnocchi di nonna Alice`  
  
 `6`  
  
 `Thüringer Rostbratwurst`  
  
 `7`  
  
 `Manjimup Dried Apples`  
  
 `8`  
  
 `Carnarvon Tigers`  
  
## <a name="see-also"></a><span data-ttu-id="1ed58-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="1ed58-114">See Also</span></span>  
 [<span data-ttu-id="1ed58-115">Agregační dotazy</span><span class="sxs-lookup"><span data-stu-id="1ed58-115">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 [<span data-ttu-id="1ed58-116">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="1ed58-116">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
