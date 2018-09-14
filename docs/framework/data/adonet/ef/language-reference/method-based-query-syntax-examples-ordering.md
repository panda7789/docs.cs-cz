---
title: 'Příklady syntaxe dotazů založených na volání metody: řazení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5d21b178-d731-471a-8534-1f8184a2ef06
ms.openlocfilehash: c059bd771667c23bb9aeb78b548e7036e4b8a73a
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45519880"
---
# <a name="method-based-query-syntax-examples-ordering"></a><span data-ttu-id="deeb5-102">Příklady syntaxe dotazů založených na volání metody: řazení</span><span class="sxs-lookup"><span data-stu-id="deeb5-102">Method-Based Query Syntax Examples: Ordering</span></span>
<span data-ttu-id="deeb5-103">Příklady v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.ThenBy%2A> metodu dotazu [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) pomocí syntaxe dotazů založených na volání metody.</span><span class="sxs-lookup"><span data-stu-id="deeb5-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ThenBy%2A> method to query the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="deeb5-104">Model prodeje AdventureWorks používá v těchto příkladech je sestaven z tabulky kontaktu, adresa, produktu, SalesOrderHeader a podrobnosti prodejní objednávky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="deeb5-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="deeb5-105">V příkladech v tomto tématu se používá následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="deeb5-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="thenby"></a><span data-ttu-id="deeb5-106">ThenBy</span><span class="sxs-lookup"><span data-stu-id="deeb5-106">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="deeb5-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="deeb5-107">Example</span></span>  
 <span data-ttu-id="deeb5-108">V následujícím příkladu v syntaxi dotazů založených na volání metody <xref:System.Linq.Queryable.OrderBy%2A> a <xref:System.Linq.Queryable.ThenBy%2A> vrátila seznam kontaktů seřazené podle příjmení a pak podle křestního jména.</span><span class="sxs-lookup"><span data-stu-id="deeb5-108">The following example in method-based query syntax uses <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenBy%2A> to return a list of contacts ordered by last name and then by first name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbythenby_mq)]
 [!code-vb[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbythenby_mq)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="deeb5-109">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="deeb5-109">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="deeb5-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="deeb5-110">Example</span></span>  
 <span data-ttu-id="deeb5-111">V následujícím příkladu <xref:System.Linq.Queryable.OrderBy%2A> a <xref:System.Linq.Queryable.ThenByDescending%2A> metody pro první řadit podle ceníku a pak proveďte sestupně ze názvy produktů.</span><span class="sxs-lookup"><span data-stu-id="deeb5-111">The following example uses the <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenByDescending%2A> methods to first sort by list price, and then perform a descending sort of the product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#thenbydescending_mq)]
 [!code-vb[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#thenbydescending_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="deeb5-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="deeb5-112">See Also</span></span>  
 [<span data-ttu-id="deeb5-113">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="deeb5-113">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
