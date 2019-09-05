---
title: 'Příklady syntaxe dotazů založených na volání metody: Řazení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5d21b178-d731-471a-8534-1f8184a2ef06
ms.openlocfilehash: 8da335bc2b45153aa00cd28f1a6baf58d11020ce
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250111"
---
# <a name="method-based-query-syntax-examples-ordering"></a><span data-ttu-id="5e7a5-102">Příklady syntaxe dotazů založených na volání metody: Řazení</span><span class="sxs-lookup"><span data-stu-id="5e7a5-102">Method-Based Query Syntax Examples: Ordering</span></span>
<span data-ttu-id="5e7a5-103">Příklady v tomto tématu ukazují, jak použít <xref:System.Linq.Enumerable.ThenBy%2A> metodu pro dotazování [modelu prodeje AdventureWorks](https://archive.codeplex.com/?p=msftdbprodsamples) pomocí syntaxe dotazu založeného na metodách.</span><span class="sxs-lookup"><span data-stu-id="5e7a5-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ThenBy%2A> method to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using method-based query syntax.</span></span> <span data-ttu-id="5e7a5-104">Model prodeje společnosti AdventureWorks použitý v těchto příkladech je sestaven z tabulek Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="5e7a5-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="5e7a5-105">Příklady v tomto tématu používají následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="5e7a5-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="thenby"></a><span data-ttu-id="5e7a5-106">ThenBy</span><span class="sxs-lookup"><span data-stu-id="5e7a5-106">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="5e7a5-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="5e7a5-107">Example</span></span>  
 <span data-ttu-id="5e7a5-108">Následující příklad v syntaxi dotazu založeného na metodách <xref:System.Linq.Queryable.OrderBy%2A> používá <xref:System.Linq.Queryable.ThenBy%2A> a vrátí seznam kontaktů seřazené podle příjmení a pak podle křestního jména.</span><span class="sxs-lookup"><span data-stu-id="5e7a5-108">The following example in method-based query syntax uses <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenBy%2A> to return a list of contacts ordered by last name and then by first name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbythenby_mq)]
 [!code-vb[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbythenby_mq)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="5e7a5-109">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="5e7a5-109">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="5e7a5-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="5e7a5-110">Example</span></span>  
 <span data-ttu-id="5e7a5-111">Následující příklad používá <xref:System.Linq.Queryable.OrderBy%2A> metody a <xref:System.Linq.Queryable.ThenByDescending%2A> k prvnímu řazení podle ceníkové ceny a pak provede sestupné řazení názvů produktů.</span><span class="sxs-lookup"><span data-stu-id="5e7a5-111">The following example uses the <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenByDescending%2A> methods to first sort by list price, and then perform a descending sort of the product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#thenbydescending_mq)]
 [!code-vb[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#thenbydescending_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="5e7a5-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5e7a5-112">See also</span></span>

- [<span data-ttu-id="5e7a5-113">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="5e7a5-113">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
