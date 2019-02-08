---
title: 'Příklady syntaxe výrazů dotazů: Řazení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bcbc9625-7cf7-476e-85d2-058f12682f54
ms.openlocfilehash: e7591e68490bf1ac35b56d5f483d1838a0a7d0c2
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/07/2019
ms.locfileid: "55826314"
---
# <a name="query-expression-syntax-examples-ordering"></a><span data-ttu-id="3bf9b-102">Příklady syntaxe výrazů dotazů: Řazení</span><span class="sxs-lookup"><span data-stu-id="3bf9b-102">Query Expression Syntax Examples: Ordering</span></span>
<span data-ttu-id="3bf9b-103">Příklady v tomto tématu ukazují, jak používat `OrderBy` a `OrderByDescending` metody k dotazování [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="3bf9b-103">The examples in this topic demonstrate how to use the `OrderBy` and `OrderByDescending` methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using query expression syntax.</span></span> <span data-ttu-id="3bf9b-104">Model prodeje AdventureWorks používá v těchto příkladech je sestaven z tabulky kontaktu, adresa, produktu, SalesOrderHeader a podrobnosti prodejní objednávky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="3bf9b-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="3bf9b-105">V příkladech v tomto tématu se používá následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="3bf9b-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="orderby"></a><span data-ttu-id="3bf9b-106">Řadit podle</span><span class="sxs-lookup"><span data-stu-id="3bf9b-106">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="3bf9b-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="3bf9b-107">Example</span></span>  
 <span data-ttu-id="3bf9b-108">Následující příklad používá <xref:System.Linq.Enumerable.OrderBy%2A> vrátila seznam kontaktů seřazené podle příjmení.</span><span class="sxs-lookup"><span data-stu-id="3bf9b-108">The following example uses <xref:System.Linq.Enumerable.OrderBy%2A> to return a list of contacts ordered by last name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderBySimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbysimple1)]
 [!code-vb[DP L2E Examples#OrderBySimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbysimple1)]  
  
### <a name="example"></a><span data-ttu-id="3bf9b-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="3bf9b-109">Example</span></span>  
 <span data-ttu-id="3bf9b-110">Následující příklad používá <xref:System.Linq.Enumerable.OrderBy%2A> seřadíte seznam kontaktů podle délky příjmení.</span><span class="sxs-lookup"><span data-stu-id="3bf9b-110">The following example uses <xref:System.Linq.Enumerable.OrderBy%2A> to sort a list of contacts by length of last name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderBySimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbysimple2)]
 [!code-vb[DP L2E Examples#OrderBySimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbysimple2)]  
  
## <a name="orderbydescending"></a><span data-ttu-id="3bf9b-111">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="3bf9b-111">OrderByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="3bf9b-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="3bf9b-112">Example</span></span>  
 <span data-ttu-id="3bf9b-113">Následující příklad používá `orderby… descending` (`Order By … Descending` v jazyce Visual Basic), což je totéž jako <xref:System.Linq.Enumerable.OrderByDescending%2A> metoda seřadíte seznam cena od nejvyšší k nejnižší.</span><span class="sxs-lookup"><span data-stu-id="3bf9b-113">The following example uses `orderby… descending` (`Order By … Descending` in Visual Basic), which is equivalent to the <xref:System.Linq.Enumerable.OrderByDescending%2A> method, to sort the price list from highest to lowest.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByDescendingSimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbydescendingsimple1)]
 [!code-vb[DP L2E Examples#OrderByDescendingSimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbydescendingsimple1)]  
  
## <a name="thenby"></a><span data-ttu-id="3bf9b-114">ThenBy</span><span class="sxs-lookup"><span data-stu-id="3bf9b-114">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="3bf9b-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="3bf9b-115">Example</span></span>  
 <span data-ttu-id="3bf9b-116">Následující příklad používá <xref:System.Linq.Queryable.OrderBy%2A> a <xref:System.Linq.Queryable.ThenBy%2A> vrátila seznam kontaktů seřazené podle příjmení a pak podle křestního jména.</span><span class="sxs-lookup"><span data-stu-id="3bf9b-116">The following example uses <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenBy%2A> to return a list of contacts ordered by last name and then by first name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByThenBy](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbythenby)]
 [!code-vb[DP L2E Examples#OrderByThenBy](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbythenby)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="3bf9b-117">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="3bf9b-117">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="3bf9b-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="3bf9b-118">Example</span></span>  
 <span data-ttu-id="3bf9b-119">Následující příklad používá `OrderBy… Descending`, což je totéž jako <xref:System.Linq.Enumerable.ThenByDescending%2A> metoda seřadíte seznam produktů, nejprve podle názvu a pak podle ceníku od nejvyšší k nejnižší.</span><span class="sxs-lookup"><span data-stu-id="3bf9b-119">The following example uses `OrderBy… Descending`, which is equivalent to the <xref:System.Linq.Enumerable.ThenByDescending%2A> method, to sort a list of products, first by name and then by list price from highest to lowest.</span></span>  
  
 [!code-csharp[DP L2E Examples#ThenByDescendingSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#thenbydescendingsimple)]
 [!code-vb[DP L2E Examples#ThenByDescendingSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#thenbydescendingsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="3bf9b-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3bf9b-120">See also</span></span>
- [<span data-ttu-id="3bf9b-121">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="3bf9b-121">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
