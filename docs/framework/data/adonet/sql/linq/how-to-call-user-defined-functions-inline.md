---
title: 'Postupy: Volání uživatelem definovaných vložených funkcí'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f80d4327-b6a5-4aa8-a743-e95d09a2a02e
ms.openlocfilehash: e9808856543e20b8904be812b15b32154eab56e2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782107"
---
# <a name="how-to-call-user-defined-functions-inline"></a><span data-ttu-id="337e9-102">Postupy: Volání uživatelem definovaných vložených funkcí</span><span class="sxs-lookup"><span data-stu-id="337e9-102">How to: Call User-Defined Functions Inline</span></span>
<span data-ttu-id="337e9-103">I když můžete volat uživatelsky definované funkce vložené, funkce, které jsou zahrnuty v dotazu, jehož spuštění je odloženo, nejsou provedeny, dokud není dotaz proveden.</span><span class="sxs-lookup"><span data-stu-id="337e9-103">Although you can call user-defined functions inline, functions that are included in a query whose execution is deferred are not executed until the query is executed.</span></span> <span data-ttu-id="337e9-104">Další informace najdete v tématu [Úvod do dotazů LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="337e9-104">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 <span data-ttu-id="337e9-105">Když zavoláte stejnou funkci mimo dotaz, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vytvoří se jednoduchý dotaz z výrazu volání metody.</span><span class="sxs-lookup"><span data-stu-id="337e9-105">When you call the same function outside a query, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates a simple query from the method call expression.</span></span> <span data-ttu-id="337e9-106">Následuje syntaxe SQL (parametr `@p0` je svázán s předaným konstantou):</span><span class="sxs-lookup"><span data-stu-id="337e9-106">The following is the SQL syntax (the parameter `@p0` is bound to the constant passed in):</span></span>  
  
```  
SELECT dbo.ReverseCustName(@p0)  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="337e9-107">Vytvoří následující:</span><span class="sxs-lookup"><span data-stu-id="337e9-107">creates the following:</span></span>  
  
 [!code-csharp[DLinqUDFS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#4)]
 [!code-vb[DLinqUDFS#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="337e9-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="337e9-108">Example</span></span>  
 <span data-ttu-id="337e9-109">V následujícím [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazu vidíte vložené volání do vygenerované uživatelsky definované metody `ReverseCustName`Function.</span><span class="sxs-lookup"><span data-stu-id="337e9-109">In the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query, you can see an inline call to the generated user-defined function method `ReverseCustName`.</span></span> <span data-ttu-id="337e9-110">Funkce není provedena ihned, protože provádění dotazu je odloženo.</span><span class="sxs-lookup"><span data-stu-id="337e9-110">The function is not executed immediately because query execution is deferred.</span></span> <span data-ttu-id="337e9-111">SQL sestavený pro tento dotaz se překládá na volání uživatelsky definované funkce v databázi (viz kód SQL, který následuje dotaz).</span><span class="sxs-lookup"><span data-stu-id="337e9-111">The SQL built for this query translates to a call to the user-defined function in the database (see the SQL code following the query).</span></span>  
  
 [!code-csharp[DLinqUDFS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#5)]
 [!code-vb[DLinqUDFS#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#5)]  
  
```  
SELECT [t0].[ContactName],  
    dbo.ReverseCustName([t0].[ContactTitle]) AS [Title]  
FROM [Customers] AS [t0]  
```  
  
## <a name="see-also"></a><span data-ttu-id="337e9-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="337e9-112">See also</span></span>

- [<span data-ttu-id="337e9-113">Uživatelem definované funkce</span><span class="sxs-lookup"><span data-stu-id="337e9-113">User-Defined Functions</span></span>](user-defined-functions.md)
