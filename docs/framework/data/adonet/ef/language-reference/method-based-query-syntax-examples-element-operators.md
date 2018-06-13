---
title: 'Příklady syntaxe dotazu na základě metod: Operátory Element'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8438b995-bd07-4223-b22d-13adadef33fb
ms.openlocfilehash: 0933b1852d87f4f00a77aacfd9ea2cf19a3e9a1f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761295"
---
# <a name="method-based-query-syntax-examples-element-operators"></a><span data-ttu-id="2bb47-102">Příklady syntaxe dotazu na základě metod: Operátory Element</span><span class="sxs-lookup"><span data-stu-id="2bb47-102">Method-Based Query Syntax Examples: Element Operators</span></span>
<span data-ttu-id="2bb47-103">V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.First%2A> metodu pro dotaz [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) pomocí syntaxe dotazu na základě metod.</span><span class="sxs-lookup"><span data-stu-id="2bb47-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="2bb47-104">Model prodeje společnosti AdventureWorks použít v těchto příkladech je sestaven z kontaktu, adresu, produktu, SalesOrderHeader a podrobnosti prodejní objednávky tabulky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="2bb47-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="2bb47-105">V příkladu v tomto tématu používá následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="2bb47-105">The example in this topic uses the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="2bb47-106">první</span><span class="sxs-lookup"><span data-stu-id="2bb47-106">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="2bb47-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="2bb47-107">Example</span></span>  
 <span data-ttu-id="2bb47-108">Následující příklad používá <xref:System.Linq.Enumerable.First%2A> metody k vyhledání prvního e-mailovou adresu, která se spouští s 'caroline'.</span><span class="sxs-lookup"><span data-stu-id="2bb47-108">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to find the first email address that starts with 'caroline'.</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstcondition_mq)]
 [!code-vb[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstcondition_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="2bb47-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="2bb47-109">See Also</span></span>  
 [<span data-ttu-id="2bb47-110">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="2bb47-110">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
