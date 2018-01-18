---
title: "Postupy: volání vnořené funkce definované uživatelem"
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
ms.assetid: f80d4327-b6a5-4aa8-a743-e95d09a2a02e
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f84d6c2c75844ab265259339ed8f72e42419f63a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-call-user-defined-functions-inline"></a><span data-ttu-id="6732d-102">Postupy: volání vnořené funkce definované uživatelem</span><span class="sxs-lookup"><span data-stu-id="6732d-102">How to: Call User-Defined Functions Inline</span></span>
<span data-ttu-id="6732d-103">I když bude možné volat vložené uživatelem definované funkce, funkce, které jsou zahrnuty v dotazu, jejichž spuštění je odložení nejsou provést, dokud se spustí dotaz.</span><span class="sxs-lookup"><span data-stu-id="6732d-103">Although you can call user-defined functions inline, functions that are included in a query whose execution is deferred are not executed until the query is executed.</span></span> <span data-ttu-id="6732d-104">Další informace najdete v tématu [Úvod do dotazů LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="6732d-104">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 <span data-ttu-id="6732d-105">Při volání stejnou funkci mimo dotazu, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vytvoří jednoduchý dotaz z výrazu volání metody.</span><span class="sxs-lookup"><span data-stu-id="6732d-105">When you call the same function outside a query, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates a simple query from the method call expression.</span></span> <span data-ttu-id="6732d-106">Toto je syntaxe SQL (parametr `@p0` je vázána na konstantu předaná):</span><span class="sxs-lookup"><span data-stu-id="6732d-106">The following is the SQL syntax (the parameter `@p0` is bound to the constant passed in):</span></span>  
  
```  
SELECT dbo.ReverseCustName(@p0)  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="6732d-107">vytvoří následující:</span><span class="sxs-lookup"><span data-stu-id="6732d-107"> creates the following:</span></span>  
  
 [!code-csharp[DLinqUDFS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#4)]
 [!code-vb[DLinqUDFS#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="6732d-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="6732d-108">Example</span></span>  
 <span data-ttu-id="6732d-109">V následujícím [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotaz, zobrazí se o vložený volání do metody generované uživatelem definované funkce `ReverseCustName`.</span><span class="sxs-lookup"><span data-stu-id="6732d-109">In the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query, you can see an inline call to the generated user-defined function method `ReverseCustName`.</span></span> <span data-ttu-id="6732d-110">Funkce není okamžitě spustit, protože spuštění dotazu je odložen.</span><span class="sxs-lookup"><span data-stu-id="6732d-110">The function is not executed immediately because query execution is deferred.</span></span> <span data-ttu-id="6732d-111">SQL sestavených pro tento dotaz přeloží volání uživatelem definované funkce v databázi (viz následující dotaz SQL kód).</span><span class="sxs-lookup"><span data-stu-id="6732d-111">The SQL built for this query translates to a call to the user-defined function in the database (see the SQL code following the query).</span></span>  
  
 [!code-csharp[DLinqUDFS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#5)]
 [!code-vb[DLinqUDFS#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#5)]  
  
```  
SELECT [t0].[ContactName],  
    dbo.ReverseCustName([t0].[ContactTitle]) AS [Title]  
FROM [Customers] AS [t0]  
```  
  
## <a name="see-also"></a><span data-ttu-id="6732d-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="6732d-112">See Also</span></span>  
 [<span data-ttu-id="6732d-113">Uživatelem definované funkce</span><span class="sxs-lookup"><span data-stu-id="6732d-113">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
