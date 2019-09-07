---
title: 'Příklady syntaxe dotazů založených na volání metody: Operátory elementů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8438b995-bd07-4223-b22d-13adadef33fb
ms.openlocfilehash: 7add62a2792a0fc82346851b7dd835aad5082742
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397465"
---
# <a name="method-based-query-syntax-examples-element-operators"></a><span data-ttu-id="96f4d-102">Příklady syntaxe dotazů založených na volání metody: Operátory elementů</span><span class="sxs-lookup"><span data-stu-id="96f4d-102">Method-Based Query Syntax Examples: Element Operators</span></span>
<span data-ttu-id="96f4d-103">Příklady v tomto tématu ukazují, jak použít <xref:System.Linq.Enumerable.First%2A> metodu pro dotazování [modelu prodeje AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) pomocí syntaxe dotazu založeného na metodách.</span><span class="sxs-lookup"><span data-stu-id="96f4d-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="96f4d-104">Model prodeje společnosti AdventureWorks použitý v těchto příkladech je sestaven z tabulek Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="96f4d-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="96f4d-105">Příklad v tomto tématu používá následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="96f4d-105">The example in this topic uses the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="96f4d-106">První</span><span class="sxs-lookup"><span data-stu-id="96f4d-106">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="96f4d-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="96f4d-107">Example</span></span>  
 <span data-ttu-id="96f4d-108">Následující příklad používá <xref:System.Linq.Enumerable.First%2A> metodu k vyhledání první e-mailové adresy začínající na ' Caroline '.</span><span class="sxs-lookup"><span data-stu-id="96f4d-108">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to find the first email address that starts with 'caroline'.</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstcondition_mq)]
 [!code-vb[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstcondition_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="96f4d-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="96f4d-109">See also</span></span>

- [<span data-ttu-id="96f4d-110">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="96f4d-110">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
