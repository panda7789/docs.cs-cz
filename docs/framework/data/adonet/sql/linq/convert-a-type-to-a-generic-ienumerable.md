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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: fa15e1336c31aec47fb2255f224146b9ac7e429d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="convert-a-type-to-a-generic-ienumerable"></a><span data-ttu-id="58905-102">Převést typ na obecný IEnumerable</span><span class="sxs-lookup"><span data-stu-id="58905-102">Convert a Type to a Generic IEnumerable</span></span>
<span data-ttu-id="58905-103">Použití <xref:System.Linq.Enumerable.AsEnumerable%2A> vrátit argument zadán jako obecný `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="58905-103">Use <xref:System.Linq.Enumerable.AsEnumerable%2A> to return the argument typed as a generic `IEnumerable`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58905-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="58905-104">Example</span></span>  
 <span data-ttu-id="58905-105">V tomto příkladu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (použití výchozí Obecné `Query`) se pokusit o převést dotaz SQL a spustit na serveru.</span><span class="sxs-lookup"><span data-stu-id="58905-105">In this example, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (using the default generic `Query`) would try to convert the query to SQL and execute it on the server.</span></span> <span data-ttu-id="58905-106">Ale `where` klauzule odkazuje uživatelem definované metody na straně klienta (`isValidProduct`), který nelze převést na SQL.</span><span class="sxs-lookup"><span data-stu-id="58905-106">But the `where` clause references a user-defined client-side method (`isValidProduct`), which cannot be converted to SQL.</span></span>  
  
 <span data-ttu-id="58905-107">Řešení je k určení obecného klienta <xref:System.Collections.Generic.IEnumerable%601> implementace `where` nahradit Obecné <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="58905-107">The solution is to specify the client-side generic <xref:System.Collections.Generic.IEnumerable%601> implementation of `where` to replace the generic <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="58905-108">To se provádí volání <xref:System.Linq.Enumerable.AsEnumerable%2A> operátor.</span><span class="sxs-lookup"><span data-stu-id="58905-108">You do this by invoking the <xref:System.Linq.Enumerable.AsEnumerable%2A> operator.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#46](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#46)]
 [!code-vb[DLinqQueryExamples#46](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#46)]  
  
## <a name="see-also"></a><span data-ttu-id="58905-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="58905-109">See Also</span></span>  
 [<span data-ttu-id="58905-110">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="58905-110">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
