---
title: Převod typu na obecnou položku IEnumerable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 64774fb5-7447-4296-ad3b-8a94346f99a1
ms.openlocfilehash: c92f65c22fe4b4128a171c757bb9e9c0ccbc3fee
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247732"
---
# <a name="convert-a-type-to-a-generic-ienumerable"></a><span data-ttu-id="2186c-102">Převod typu na obecnou položku IEnumerable</span><span class="sxs-lookup"><span data-stu-id="2186c-102">Convert a Type to a Generic IEnumerable</span></span>
<span data-ttu-id="2186c-103">Použijte <xref:System.Linq.Enumerable.AsEnumerable%2A> k vrácení argumentu zadaného jako obecné `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="2186c-103">Use <xref:System.Linq.Enumerable.AsEnumerable%2A> to return the argument typed as a generic `IEnumerable`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2186c-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="2186c-104">Example</span></span>  
 <span data-ttu-id="2186c-105">V tomto příkladu ( [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pomocí výchozího obecného `Query`) se pokusí převést dotaz na SQL a spustit ho na serveru.</span><span class="sxs-lookup"><span data-stu-id="2186c-105">In this example, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (using the default generic `Query`) would try to convert the query to SQL and execute it on the server.</span></span> <span data-ttu-id="2186c-106">Ale klauzule odkazuje na uživatelem definovanou metodu na straně klienta (`isValidProduct`), kterou nelze převést na SQL. `where`</span><span class="sxs-lookup"><span data-stu-id="2186c-106">But the `where` clause references a user-defined client-side method (`isValidProduct`), which cannot be converted to SQL.</span></span>  
  
 <span data-ttu-id="2186c-107">Řešením je určit obecnou <xref:System.Collections.Generic.IEnumerable%601> `where` implementaci na straně klienta pro nahrazení obecného <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="2186c-107">The solution is to specify the client-side generic <xref:System.Collections.Generic.IEnumerable%601> implementation of `where` to replace the generic <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="2186c-108">Provedete to vyvoláním <xref:System.Linq.Enumerable.AsEnumerable%2A> operátoru.</span><span class="sxs-lookup"><span data-stu-id="2186c-108">You do this by invoking the <xref:System.Linq.Enumerable.AsEnumerable%2A> operator.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#46](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#46)]
 [!code-vb[DLinqQueryExamples#46](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#46)]  
  
## <a name="see-also"></a><span data-ttu-id="2186c-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2186c-109">See also</span></span>

- [<span data-ttu-id="2186c-110">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="2186c-110">Query Examples</span></span>](query-examples.md)
