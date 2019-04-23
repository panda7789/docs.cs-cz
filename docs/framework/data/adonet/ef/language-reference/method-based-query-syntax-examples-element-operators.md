---
title: 'Příklady syntaxe dotazů založených na volání metody: Operátory elementů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8438b995-bd07-4223-b22d-13adadef33fb
ms.openlocfilehash: 3656ea6d2d9602c3790ab4113b5c2f153b4f7c73
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59188588"
---
# <a name="method-based-query-syntax-examples-element-operators"></a><span data-ttu-id="b22d0-102">Příklady syntaxe dotazů založených na volání metody: Operátory elementů</span><span class="sxs-lookup"><span data-stu-id="b22d0-102">Method-Based Query Syntax Examples: Element Operators</span></span>
<span data-ttu-id="b22d0-103">Příklady v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.First%2A> metodu dotazu [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) pomocí syntaxe dotazů založených na volání metody.</span><span class="sxs-lookup"><span data-stu-id="b22d0-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using method-based query syntax.</span></span> <span data-ttu-id="b22d0-104">Model prodeje AdventureWorks používá v těchto příkladech je sestaven z tabulky kontaktu, adresa, produktu, SalesOrderHeader a podrobnosti prodejní objednávky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="b22d0-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="b22d0-105">V příkladu v tomto tématu používá následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="b22d0-105">The example in this topic uses the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="b22d0-106">první</span><span class="sxs-lookup"><span data-stu-id="b22d0-106">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="b22d0-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="b22d0-107">Example</span></span>  
 <span data-ttu-id="b22d0-108">V následujícím příkladu <xref:System.Linq.Enumerable.First%2A> metody k vyhledání prvního e-mailovou adresu, která se spustí s "caroline".</span><span class="sxs-lookup"><span data-stu-id="b22d0-108">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to find the first email address that starts with 'caroline'.</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstcondition_mq)]
 [!code-vb[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstcondition_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="b22d0-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b22d0-109">See also</span></span>

- [<span data-ttu-id="b22d0-110">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="b22d0-110">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
