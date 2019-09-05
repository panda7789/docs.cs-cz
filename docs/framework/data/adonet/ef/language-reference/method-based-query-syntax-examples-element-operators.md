---
title: 'Příklady syntaxe dotazů založených na volání metody: Operátory elementů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8438b995-bd07-4223-b22d-13adadef33fb
ms.openlocfilehash: 9a057cd80b3dc110626d1a9a850ee7c9704b33b4
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250262"
---
# <a name="method-based-query-syntax-examples-element-operators"></a><span data-ttu-id="59b3b-102">Příklady syntaxe dotazů založených na volání metody: Operátory elementů</span><span class="sxs-lookup"><span data-stu-id="59b3b-102">Method-Based Query Syntax Examples: Element Operators</span></span>
<span data-ttu-id="59b3b-103">Příklady v tomto tématu ukazují, jak použít <xref:System.Linq.Enumerable.First%2A> metodu pro dotazování [modelu prodeje AdventureWorks](https://archive.codeplex.com/?p=msftdbprodsamples) pomocí syntaxe dotazu založeného na metodách.</span><span class="sxs-lookup"><span data-stu-id="59b3b-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using method-based query syntax.</span></span> <span data-ttu-id="59b3b-104">Model prodeje společnosti AdventureWorks použitý v těchto příkladech je sestaven z tabulek Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="59b3b-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="59b3b-105">Příklad v tomto tématu používá následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="59b3b-105">The example in this topic uses the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="59b3b-106">První</span><span class="sxs-lookup"><span data-stu-id="59b3b-106">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="59b3b-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="59b3b-107">Example</span></span>  
 <span data-ttu-id="59b3b-108">Následující příklad používá <xref:System.Linq.Enumerable.First%2A> metodu k vyhledání první e-mailové adresy začínající na ' Caroline '.</span><span class="sxs-lookup"><span data-stu-id="59b3b-108">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to find the first email address that starts with 'caroline'.</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstcondition_mq)]
 [!code-vb[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstcondition_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="59b3b-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="59b3b-109">See also</span></span>

- [<span data-ttu-id="59b3b-110">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="59b3b-110">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
