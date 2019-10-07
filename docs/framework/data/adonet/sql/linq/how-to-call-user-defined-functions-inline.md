---
title: 'Postupy: volání vložených funkcí definovaných uživatelem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f80d4327-b6a5-4aa8-a743-e95d09a2a02e
ms.openlocfilehash: 01ba9ab4359cbd124b2207c87d5dae904641911a
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002981"
---
# <a name="how-to-call-user-defined-functions-inline"></a><span data-ttu-id="a4f71-102">Postupy: volání vložených funkcí definovaných uživatelem</span><span class="sxs-lookup"><span data-stu-id="a4f71-102">How to: Call User-Defined Functions Inline</span></span>
<span data-ttu-id="a4f71-103">I když můžete volat uživatelsky definované funkce vložené, funkce, které jsou zahrnuty v dotazu, jehož spuštění je odloženo, nejsou provedeny, dokud není dotaz proveden.</span><span class="sxs-lookup"><span data-stu-id="a4f71-103">Although you can call user-defined functions inline, functions that are included in a query whose execution is deferred are not executed until the query is executed.</span></span> <span data-ttu-id="a4f71-104">Další informace najdete v tématu [Úvod do dotazů LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="a4f71-104">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 <span data-ttu-id="a4f71-105">Když zavoláte stejnou funkci mimo dotaz, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vytvoří jednoduchý dotaz z výrazu volání metody.</span><span class="sxs-lookup"><span data-stu-id="a4f71-105">When you call the same function outside a query, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates a simple query from the method call expression.</span></span> <span data-ttu-id="a4f71-106">Následuje syntaxe SQL (parametr `@p0` je svázán s předaným konstantou):</span><span class="sxs-lookup"><span data-stu-id="a4f71-106">The following is the SQL syntax (the parameter `@p0` is bound to the constant passed in):</span></span>  
  
```sql  
SELECT dbo.ReverseCustName(@p0)  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="a4f71-107">vytvoří následující:</span><span class="sxs-lookup"><span data-stu-id="a4f71-107">creates the following:</span></span>  
  
 [!code-csharp[DLinqUDFS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#4)]
 [!code-vb[DLinqUDFS#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="a4f71-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="a4f71-108">Example</span></span>  
 <span data-ttu-id="a4f71-109">V následujících dotazech [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] můžete zobrazit vložené volání uživatelsky definované metody funkce `ReverseCustName`.</span><span class="sxs-lookup"><span data-stu-id="a4f71-109">In the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query, you can see an inline call to the generated user-defined function method `ReverseCustName`.</span></span> <span data-ttu-id="a4f71-110">Funkce není provedena ihned, protože provádění dotazu je odloženo.</span><span class="sxs-lookup"><span data-stu-id="a4f71-110">The function is not executed immediately because query execution is deferred.</span></span> <span data-ttu-id="a4f71-111">SQL sestavený pro tento dotaz se překládá na volání uživatelsky definované funkce v databázi (viz kód SQL, který následuje dotaz).</span><span class="sxs-lookup"><span data-stu-id="a4f71-111">The SQL built for this query translates to a call to the user-defined function in the database (see the SQL code following the query).</span></span>  
  
 [!code-csharp[DLinqUDFS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#5)]
 [!code-vb[DLinqUDFS#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#5)]  
  
```sql  
SELECT [t0].[ContactName],  
    dbo.ReverseCustName([t0].[ContactTitle]) AS [Title]  
FROM [Customers] AS [t0]  
```  
  
## <a name="see-also"></a><span data-ttu-id="a4f71-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a4f71-112">See also</span></span>

- [<span data-ttu-id="a4f71-113">Uživatelem definované funkce</span><span class="sxs-lookup"><span data-stu-id="a4f71-113">User-Defined Functions</span></span>](user-defined-functions.md)
