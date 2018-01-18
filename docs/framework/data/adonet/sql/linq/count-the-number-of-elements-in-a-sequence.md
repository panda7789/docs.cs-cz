---
title: "Počet elementů v pořadí"
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
ms.assetid: ccbe5d54-c9eb-4b14-b0ab-f628483c5f99
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: bc2747167893e5c9bed76a118a528089fbe93a02
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="count-the-number-of-elements-in-a-sequence"></a><span data-ttu-id="a98bb-102">Počet elementů v pořadí</span><span class="sxs-lookup"><span data-stu-id="a98bb-102">Count the Number of Elements in a Sequence</span></span>
<span data-ttu-id="a98bb-103">Použití <xref:System.Linq.Enumerable.Count%2A> operátor počítat počet elementů v pořadí.</span><span class="sxs-lookup"><span data-stu-id="a98bb-103">Use the <xref:System.Linq.Enumerable.Count%2A> operator to count the number of elements in a sequence.</span></span>  
  
 <span data-ttu-id="a98bb-104">Spusťte tento dotaz proti ukázková databáze Northwind vytváří výstup `91`.</span><span class="sxs-lookup"><span data-stu-id="a98bb-104">Running this query against the Northwind sample database produces an output of `91`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a98bb-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="a98bb-105">Example</span></span>  
 <span data-ttu-id="a98bb-106">Následující příklad vrátí počet `Customers` v databázi.</span><span class="sxs-lookup"><span data-stu-id="a98bb-106">The following example counts the number of `Customers` in the database.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#4)]
 [!code-vb[DLinqQueryExamples#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="a98bb-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="a98bb-107">Example</span></span>  
 <span data-ttu-id="a98bb-108">Následující příklad vrátí počet produktů v databázi, které se již.</span><span class="sxs-lookup"><span data-stu-id="a98bb-108">The following example counts the number of products in the database that have not been discontinued.</span></span>  
  
 <span data-ttu-id="a98bb-109">Tento příklad spuštěn proti ukázková databáze Northwind vytváří výstup `69`.</span><span class="sxs-lookup"><span data-stu-id="a98bb-109">Running this example against the Northwind sample database produces an output of `69`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#5)]
 [!code-vb[DLinqQueryExamples#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="a98bb-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="a98bb-110">See Also</span></span>  
 [<span data-ttu-id="a98bb-111">Agregační dotazy</span><span class="sxs-lookup"><span data-stu-id="a98bb-111">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 [<span data-ttu-id="a98bb-112">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="a98bb-112">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
