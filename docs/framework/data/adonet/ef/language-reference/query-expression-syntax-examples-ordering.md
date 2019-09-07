---
title: 'Příklady syntaxe výrazů dotazů: Řazení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bcbc9625-7cf7-476e-85d2-058f12682f54
ms.openlocfilehash: 73000b16b29238dfb60596060733ecf8d7caa45b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398438"
---
# <a name="query-expression-syntax-examples-ordering"></a><span data-ttu-id="e0e25-102">Příklady syntaxe výrazů dotazů: Řazení</span><span class="sxs-lookup"><span data-stu-id="e0e25-102">Query Expression Syntax Examples: Ordering</span></span>
<span data-ttu-id="e0e25-103">Příklady v tomto tématu ukazují, jak použít `OrderBy` metody a `OrderByDescending` k dotazování [modelu prodeje AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="e0e25-103">The examples in this topic demonstrate how to use the `OrderBy` and `OrderByDescending` methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="e0e25-104">Model prodeje společnosti AdventureWorks použitý v těchto příkladech je sestaven z tabulek Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e0e25-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="e0e25-105">Příklady v tomto tématu používají následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="e0e25-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="orderby"></a><span data-ttu-id="e0e25-106">OrderBy</span><span class="sxs-lookup"><span data-stu-id="e0e25-106">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="e0e25-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="e0e25-107">Example</span></span>  
 <span data-ttu-id="e0e25-108">Následující příklad používá <xref:System.Linq.Enumerable.OrderBy%2A> k vrácení seznamu kontaktů seřazené podle příjmení.</span><span class="sxs-lookup"><span data-stu-id="e0e25-108">The following example uses <xref:System.Linq.Enumerable.OrderBy%2A> to return a list of contacts ordered by last name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderBySimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbysimple1)]
 [!code-vb[DP L2E Examples#OrderBySimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbysimple1)]  
  
### <a name="example"></a><span data-ttu-id="e0e25-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="e0e25-109">Example</span></span>  
 <span data-ttu-id="e0e25-110">Následující příklad používá <xref:System.Linq.Enumerable.OrderBy%2A> k řazení seznamu kontaktů podle délky příjmení.</span><span class="sxs-lookup"><span data-stu-id="e0e25-110">The following example uses <xref:System.Linq.Enumerable.OrderBy%2A> to sort a list of contacts by length of last name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderBySimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbysimple2)]
 [!code-vb[DP L2E Examples#OrderBySimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbysimple2)]  
  
## <a name="orderbydescending"></a><span data-ttu-id="e0e25-111">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="e0e25-111">OrderByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="e0e25-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="e0e25-112">Example</span></span>  
 <span data-ttu-id="e0e25-113">Následující příklad používá `orderby… descending` (`Order By … Descending` v Visual Basic), <xref:System.Linq.Enumerable.OrderByDescending%2A> který je ekvivalentní metodě, k seřazení ceníku od nejvyšší po nejnižší.</span><span class="sxs-lookup"><span data-stu-id="e0e25-113">The following example uses `orderby… descending` (`Order By … Descending` in Visual Basic), which is equivalent to the <xref:System.Linq.Enumerable.OrderByDescending%2A> method, to sort the price list from highest to lowest.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByDescendingSimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbydescendingsimple1)]
 [!code-vb[DP L2E Examples#OrderByDescendingSimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbydescendingsimple1)]  
  
## <a name="thenby"></a><span data-ttu-id="e0e25-114">ThenBy</span><span class="sxs-lookup"><span data-stu-id="e0e25-114">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="e0e25-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="e0e25-115">Example</span></span>  
 <span data-ttu-id="e0e25-116">Následující příklad používá <xref:System.Linq.Queryable.OrderBy%2A> a <xref:System.Linq.Queryable.ThenBy%2A> k vrácení seznamu kontaktů seřazených podle příjmení a pak podle křestního jména.</span><span class="sxs-lookup"><span data-stu-id="e0e25-116">The following example uses <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenBy%2A> to return a list of contacts ordered by last name and then by first name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByThenBy](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbythenby)]
 [!code-vb[DP L2E Examples#OrderByThenBy](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbythenby)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="e0e25-117">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="e0e25-117">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="e0e25-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="e0e25-118">Example</span></span>  
 <span data-ttu-id="e0e25-119">Následující příklad používá `OrderBy… Descending`, který je ekvivalentní <xref:System.Linq.Enumerable.ThenByDescending%2A> metodě, k seřazení seznamu produktů, nejprve podle názvu a potom podle ceny seznamu od nejvyšší po nejnižší.</span><span class="sxs-lookup"><span data-stu-id="e0e25-119">The following example uses `OrderBy… Descending`, which is equivalent to the <xref:System.Linq.Enumerable.ThenByDescending%2A> method, to sort a list of products, first by name and then by list price from highest to lowest.</span></span>  
  
 [!code-csharp[DP L2E Examples#ThenByDescendingSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#thenbydescendingsimple)]
 [!code-vb[DP L2E Examples#ThenByDescendingSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#thenbydescendingsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="e0e25-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e0e25-120">See also</span></span>

- [<span data-ttu-id="e0e25-121">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="e0e25-121">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
