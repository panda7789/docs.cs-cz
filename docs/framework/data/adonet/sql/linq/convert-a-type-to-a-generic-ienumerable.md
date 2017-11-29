---
title: "Převést typ na obecný IEnumerable"
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
ms.assetid: 64774fb5-7447-4296-ad3b-8a94346f99a1
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f2e91a5fe4b27891b1750b0d74a8e9b01ad68449
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="convert-a-type-to-a-generic-ienumerable"></a><span data-ttu-id="a5f99-102">Převést typ na obecný IEnumerable</span><span class="sxs-lookup"><span data-stu-id="a5f99-102">Convert a Type to a Generic IEnumerable</span></span>
<span data-ttu-id="a5f99-103">Použití <xref:System.Linq.Enumerable.AsEnumerable%2A> vrátit argument zadán jako obecný `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="a5f99-103">Use <xref:System.Linq.Enumerable.AsEnumerable%2A> to return the argument typed as a generic `IEnumerable`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5f99-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="a5f99-104">Example</span></span>  
 <span data-ttu-id="a5f99-105">V tomto příkladu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (použití výchozí Obecné `Query`) se pokusit o převést dotaz SQL a spustit na serveru.</span><span class="sxs-lookup"><span data-stu-id="a5f99-105">In this example, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (using the default generic `Query`) would try to convert the query to SQL and execute it on the server.</span></span> <span data-ttu-id="a5f99-106">Ale `where` klauzule odkazuje uživatelem definované metody na straně klienta (`isValidProduct`), který nelze převést na SQL.</span><span class="sxs-lookup"><span data-stu-id="a5f99-106">But the `where` clause references a user-defined client-side method (`isValidProduct`), which cannot be converted to SQL.</span></span>  
  
 <span data-ttu-id="a5f99-107">Řešení je k určení obecného klienta <xref:System.Collections.Generic.IEnumerable%601> implementace `where` nahradit Obecné <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="a5f99-107">The solution is to specify the client-side generic <xref:System.Collections.Generic.IEnumerable%601> implementation of `where` to replace the generic <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="a5f99-108">To se provádí volání <xref:System.Linq.Enumerable.AsEnumerable%2A> operátor.</span><span class="sxs-lookup"><span data-stu-id="a5f99-108">You do this by invoking the <xref:System.Linq.Enumerable.AsEnumerable%2A> operator.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#46](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#46)]
 [!code-vb[DLinqQueryExamples#46](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#46)]  
  
## <a name="see-also"></a><span data-ttu-id="a5f99-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="a5f99-109">See Also</span></span>  
 [<span data-ttu-id="a5f99-110">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="a5f99-110">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
