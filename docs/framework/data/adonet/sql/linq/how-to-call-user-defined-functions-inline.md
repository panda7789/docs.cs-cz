---
title: 'Postupy: Volání uživatelem definovaných vložených funkcí'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f80d4327-b6a5-4aa8-a743-e95d09a2a02e
ms.openlocfilehash: ed8071352902b8f97445cbfa5ff0ebe8fead9bb9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163706"
---
# <a name="how-to-call-user-defined-functions-inline"></a><span data-ttu-id="c61fb-102">Postupy: Volání uživatelem definovaných vložených funkcí</span><span class="sxs-lookup"><span data-stu-id="c61fb-102">How to: Call User-Defined Functions Inline</span></span>
<span data-ttu-id="c61fb-103">I když bude možné volat vložené uživatelem definované funkce, funkce, které jsou zahrnuty v dotazu, jehož spuštění je odloženo nejsou udělat, dokud je dotaz proveden.</span><span class="sxs-lookup"><span data-stu-id="c61fb-103">Although you can call user-defined functions inline, functions that are included in a query whose execution is deferred are not executed until the query is executed.</span></span> <span data-ttu-id="c61fb-104">Další informace najdete v tématu [Úvod do dotazů LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="c61fb-104">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 <span data-ttu-id="c61fb-105">Při volání stejné funkce mimo dotazu, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vytvoří jednoduchý dotaz z výrazu volání metody.</span><span class="sxs-lookup"><span data-stu-id="c61fb-105">When you call the same function outside a query, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates a simple query from the method call expression.</span></span> <span data-ttu-id="c61fb-106">Tady je syntaxe jazyka SQL (parametr `@p0` je vázán na konstantu předaný):</span><span class="sxs-lookup"><span data-stu-id="c61fb-106">The following is the SQL syntax (the parameter `@p0` is bound to the constant passed in):</span></span>  
  
```  
SELECT dbo.ReverseCustName(@p0)  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="c61fb-107">vytvoří následující:</span><span class="sxs-lookup"><span data-stu-id="c61fb-107">creates the following:</span></span>  
  
 [!code-csharp[DLinqUDFS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#4)]
 [!code-vb[DLinqUDFS#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="c61fb-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="c61fb-108">Example</span></span>  
 <span data-ttu-id="c61fb-109">V následujícím [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazu, můžete zobrazit vložený volání metody generované uživatelem definovanou funkci `ReverseCustName`.</span><span class="sxs-lookup"><span data-stu-id="c61fb-109">In the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query, you can see an inline call to the generated user-defined function method `ReverseCustName`.</span></span> <span data-ttu-id="c61fb-110">Funkce není okamžitě provést, protože provádění dotazu je odloženo.</span><span class="sxs-lookup"><span data-stu-id="c61fb-110">The function is not executed immediately because query execution is deferred.</span></span> <span data-ttu-id="c61fb-111">SQL sestavena pro tento dotaz se přeloží na volání funkce definované uživatelem v databázi (viz kód SQL následující dotaz).</span><span class="sxs-lookup"><span data-stu-id="c61fb-111">The SQL built for this query translates to a call to the user-defined function in the database (see the SQL code following the query).</span></span>  
  
 [!code-csharp[DLinqUDFS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#5)]
 [!code-vb[DLinqUDFS#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#5)]  
  
```  
SELECT [t0].[ContactName],  
    dbo.ReverseCustName([t0].[ContactTitle]) AS [Title]  
FROM [Customers] AS [t0]  
```  
  
## <a name="see-also"></a><span data-ttu-id="c61fb-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c61fb-112">See also</span></span>

- [<span data-ttu-id="c61fb-113">Uživatelem definované funkce</span><span class="sxs-lookup"><span data-stu-id="c61fb-113">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
