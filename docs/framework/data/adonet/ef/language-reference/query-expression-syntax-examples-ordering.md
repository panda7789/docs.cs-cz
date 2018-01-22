---
title: "Příklady syntaxe výrazu dotazu: řazení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: bcbc9625-7cf7-476e-85d2-058f12682f54
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 09cc843bd56d4b9c8c13dba7883e10c6a7834cb6
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="query-expression-syntax-examples-ordering"></a><span data-ttu-id="9f58a-102">Příklady syntaxe výrazu dotazu: řazení</span><span class="sxs-lookup"><span data-stu-id="9f58a-102">Query Expression Syntax Examples: Ordering</span></span>
<span data-ttu-id="9f58a-103">V příkladech v tomto tématu ukazují, jak používat `OrderBy` a `OrderByDescending` metody k dotazování [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="9f58a-103">The examples in this topic demonstrate how to use the `OrderBy` and `OrderByDescending` methods to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using query expression syntax.</span></span> <span data-ttu-id="9f58a-104">Model prodeje společnosti AdventureWorks použít v těchto příkladech je sestaven z kontaktu, adresu, produktu, SalesOrderHeader a podrobnosti prodejní objednávky tabulky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="9f58a-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="9f58a-105">V příkladech v tomto tématu použijte následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="9f58a-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="orderby"></a><span data-ttu-id="9f58a-106">Řadit podle</span><span class="sxs-lookup"><span data-stu-id="9f58a-106">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="9f58a-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="9f58a-107">Example</span></span>  
 <span data-ttu-id="9f58a-108">Následující příklad používá <xref:System.Linq.Enumerable.OrderBy%2A> vrácení seznamu kontaktů seřazené podle příjmení.</span><span class="sxs-lookup"><span data-stu-id="9f58a-108">The following example uses <xref:System.Linq.Enumerable.OrderBy%2A> to return a list of contacts ordered by last name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderBySimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbysimple1)]
 [!code-vb[DP L2E Examples#OrderBySimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbysimple1)]  
  
### <a name="example"></a><span data-ttu-id="9f58a-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="9f58a-109">Example</span></span>  
 <span data-ttu-id="9f58a-110">Následující příklad používá <xref:System.Linq.Enumerable.OrderBy%2A> pro řazení seznamu kontaktů podle délku příjmení.</span><span class="sxs-lookup"><span data-stu-id="9f58a-110">The following example uses <xref:System.Linq.Enumerable.OrderBy%2A> to sort a list of contacts by length of last name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderBySimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbysimple2)]
 [!code-vb[DP L2E Examples#OrderBySimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbysimple2)]  
  
## <a name="orderbydescending"></a><span data-ttu-id="9f58a-111">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="9f58a-111">OrderByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="9f58a-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="9f58a-112">Example</span></span>  
 <span data-ttu-id="9f58a-113">Následující příklad používá `orderby… descending` (`Order By … Descending` v jazyce Visual Basic), což je totéž jako <xref:System.Linq.Enumerable.OrderByDescending%2A> metoda seřadit ceník od nejvyšší po nejnižší.</span><span class="sxs-lookup"><span data-stu-id="9f58a-113">The following example uses `orderby… descending` (`Order By … Descending` in Visual Basic), which is equivalent to the <xref:System.Linq.Enumerable.OrderByDescending%2A> method, to sort the price list from highest to lowest.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByDescendingSimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbydescendingsimple1)]
 [!code-vb[DP L2E Examples#OrderByDescendingSimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbydescendingsimple1)]  
  
## <a name="thenby"></a><span data-ttu-id="9f58a-114">ThenBy</span><span class="sxs-lookup"><span data-stu-id="9f58a-114">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="9f58a-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="9f58a-115">Example</span></span>  
 <span data-ttu-id="9f58a-116">Následující příklad používá <xref:System.Linq.Queryable.OrderBy%2A> a <xref:System.Linq.Queryable.ThenBy%2A> vrácení seznamu kontaktů seřazené podle příjmení a poté podle křestní jméno.</span><span class="sxs-lookup"><span data-stu-id="9f58a-116">The following example uses <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenBy%2A> to return a list of contacts ordered by last name and then by first name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByThenBy](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbythenby)]
 [!code-vb[DP L2E Examples#OrderByThenBy](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbythenby)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="9f58a-117">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="9f58a-117">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="9f58a-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="9f58a-118">Example</span></span>  
 <span data-ttu-id="9f58a-119">Následující příklad používá `OrderBy… Descending`, což je totéž jako <xref:System.Linq.Enumerable.ThenByDescending%2A> metoda seřadit seznam produktů, nejprve podle názvu a pak podle seznamu cena od nejvyšší po nejnižší.</span><span class="sxs-lookup"><span data-stu-id="9f58a-119">The following example uses `OrderBy… Descending`, which is equivalent to the <xref:System.Linq.Enumerable.ThenByDescending%2A> method, to sort a list of products, first by name and then by list price from highest to lowest.</span></span>  
  
 [!code-csharp[DP L2E Examples#ThenByDescendingSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#thenbydescendingsimple)]
 [!code-vb[DP L2E Examples#ThenByDescendingSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#thenbydescendingsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="9f58a-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="9f58a-120">See Also</span></span>  
 [<span data-ttu-id="9f58a-121">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="9f58a-121">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
