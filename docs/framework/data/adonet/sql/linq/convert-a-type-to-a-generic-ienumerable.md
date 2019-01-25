---
title: Převod typu na obecnou položku IEnumerable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 64774fb5-7447-4296-ad3b-8a94346f99a1
ms.openlocfilehash: d1f4c1c4a561c893b5846e6ae0b08b2d78c3589d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54509592"
---
# <a name="convert-a-type-to-a-generic-ienumerable"></a><span data-ttu-id="45b69-102">Převod typu na obecnou položku IEnumerable</span><span class="sxs-lookup"><span data-stu-id="45b69-102">Convert a Type to a Generic IEnumerable</span></span>
<span data-ttu-id="45b69-103">Použití <xref:System.Linq.Enumerable.AsEnumerable%2A> vrátit argument obecného typu `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="45b69-103">Use <xref:System.Linq.Enumerable.AsEnumerable%2A> to return the argument typed as a generic `IEnumerable`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45b69-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="45b69-104">Example</span></span>  
 <span data-ttu-id="45b69-105">V tomto příkladu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (použití výchozí Obecné `Query`) by se pokusil převést dotaz SQL a spusťte na serveru.</span><span class="sxs-lookup"><span data-stu-id="45b69-105">In this example, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (using the default generic `Query`) would try to convert the query to SQL and execute it on the server.</span></span> <span data-ttu-id="45b69-106">Ale `where` klauzule odkazuje na metodu uživatelem definované na straně klienta (`isValidProduct`), kterou nelze převést na SQL.</span><span class="sxs-lookup"><span data-stu-id="45b69-106">But the `where` clause references a user-defined client-side method (`isValidProduct`), which cannot be converted to SQL.</span></span>  
  
 <span data-ttu-id="45b69-107">Toto řešení je k určení obecného na straně klienta <xref:System.Collections.Generic.IEnumerable%601> provádění `where` nahradit obecný <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="45b69-107">The solution is to specify the client-side generic <xref:System.Collections.Generic.IEnumerable%601> implementation of `where` to replace the generic <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="45b69-108">To provedete tak, že vyvolá <xref:System.Linq.Enumerable.AsEnumerable%2A> operátor.</span><span class="sxs-lookup"><span data-stu-id="45b69-108">You do this by invoking the <xref:System.Linq.Enumerable.AsEnumerable%2A> operator.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#46](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#46)]
 [!code-vb[DLinqQueryExamples#46](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#46)]  
  
## <a name="see-also"></a><span data-ttu-id="45b69-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="45b69-109">See also</span></span>
- [<span data-ttu-id="45b69-110">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="45b69-110">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
