---
title: "Postupy: načtení mnoho objektů najednou"
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
ms.assetid: 18aff4d8-bde8-461b-9960-ccabb24e9d22
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: f7b9adc9d8bde80a3e888ce873a611f01f69fd9d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-retrieve-many-objects-at-once"></a><span data-ttu-id="14ff3-102">Postupy: načtení mnoho objektů najednou</span><span class="sxs-lookup"><span data-stu-id="14ff3-102">How to: Retrieve Many Objects At Once</span></span>
<span data-ttu-id="14ff3-103">Mnoho objektů v jednom dotazu můžete načíst pomocí <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span><span class="sxs-lookup"><span data-stu-id="14ff3-103">You can retrieve many objects in one query by using <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14ff3-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="14ff3-104">Example</span></span>  
 <span data-ttu-id="14ff3-105">Následující kód používá <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> metoda pro načtení obě `Customer` a `Order` objekty.</span><span class="sxs-lookup"><span data-stu-id="14ff3-105">The following code uses the <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> method to retrieve both `Customer` and `Order` objects.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#9)]
 [!code-vb[DLinqQueryConcepts#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="14ff3-106">Viz také</span><span class="sxs-lookup"><span data-stu-id="14ff3-106">See Also</span></span>  
 [<span data-ttu-id="14ff3-107">Koncepty dotazů</span><span class="sxs-lookup"><span data-stu-id="14ff3-107">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
