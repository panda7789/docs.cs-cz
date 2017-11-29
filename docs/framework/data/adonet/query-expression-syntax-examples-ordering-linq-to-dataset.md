---
title: "Příklady syntaxe výrazu dotazu: Řazení (LINQ na DataSet)"
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
ms.assetid: 653a4a97-1e4a-4b2d-8d24-7dbe1f2a5c84
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 179d9936f08e8587ef159a232292ff73ea86cd4b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="query-expression-syntax-examples-ordering-linq-to-dataset"></a><span data-ttu-id="7ac6b-102">Příklady syntaxe výrazu dotazu: Řazení (LINQ na DataSet)</span><span class="sxs-lookup"><span data-stu-id="7ac6b-102">Query Expression Syntax Examples: Ordering (LINQ to DataSet)</span></span>
<span data-ttu-id="7ac6b-103">V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, a <xref:System.Linq.Enumerable.ThenByDescending%2A> metody pro dotazování <xref:System.Data.DataSet> a řazení výsledků pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="7ac6b-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenByDescending%2A> methods to query a <xref:System.Data.DataSet> and order the results using the query expression syntax.</span></span>  
  
 <span data-ttu-id="7ac6b-104">`FillDataSet` Metodu použitou v těchto příkladech je uveden v [načítání dat do datové sady](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="7ac6b-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="7ac6b-105">V příkladech v tomto tématu použijte kontaktu, adresu, produktu, SalesOrderHeader a podrobnosti prodejní objednávky tabulky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="7ac6b-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="7ac6b-106">V příkladech v tomto tématu použijte následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="7ac6b-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="7ac6b-107">Další informace najdete v tématu [postupy: vytvoření LINQ na DataSet projekt v sadě Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="7ac6b-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="orderby"></a><span data-ttu-id="7ac6b-108">Řadit podle</span><span class="sxs-lookup"><span data-stu-id="7ac6b-108">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="7ac6b-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="7ac6b-109">Example</span></span>  
 <span data-ttu-id="7ac6b-110">Tento příklad používá <xref:System.Linq.Enumerable.OrderBy%2A> vrácení seznamu kontaktů seřazené podle příjmení.</span><span class="sxs-lookup"><span data-stu-id="7ac6b-110">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> to return a list of contacts ordered by last name.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderBySimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbysimple1)]
 [!code-vb[DP LINQ to DataSet Examples#OrderBySimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbysimple1)]  
  
### <a name="example"></a><span data-ttu-id="7ac6b-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="7ac6b-111">Example</span></span>  
 <span data-ttu-id="7ac6b-112">Tento příklad používá <xref:System.Linq.Enumerable.OrderBy%2A> pro řazení seznamu kontaktů podle délku příjmení.</span><span class="sxs-lookup"><span data-stu-id="7ac6b-112">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> to sort a list of contacts by length of last name.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderBySimple2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbysimple2)]
 [!code-vb[DP LINQ to DataSet Examples#OrderBySimple2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbysimple2)]  
  
## <a name="orderbydescending"></a><span data-ttu-id="7ac6b-113">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="7ac6b-113">OrderByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="7ac6b-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="7ac6b-114">Example</span></span>  
 <span data-ttu-id="7ac6b-115">Tento příklad používá `orderby… descending` (`Order By … Descending`), což je totéž jako <xref:System.Linq.Enumerable.OrderByDescending%2A> metoda seřadit ceník od nejvyšší po nejnižší.</span><span class="sxs-lookup"><span data-stu-id="7ac6b-115">This example uses `orderby… descending` (`Order By … Descending`), which is equivalent to the <xref:System.Linq.Enumerable.OrderByDescending%2A> method, to sort the price list from highest to lowest.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderByDescendingSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbydescendingsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#OrderByDescendingSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbydescendingsimple1)]  
  
## <a name="reverse"></a><span data-ttu-id="7ac6b-116">Reverse</span><span class="sxs-lookup"><span data-stu-id="7ac6b-116">Reverse</span></span>  
  
### <a name="example"></a><span data-ttu-id="7ac6b-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="7ac6b-117">Example</span></span>  
 <span data-ttu-id="7ac6b-118">Tento příklad používá <xref:System.Linq.Enumerable.Reverse%2A> můžete vytvořit seznam objednávek kde `OrderDate` je starší než 20. února 2002.</span><span class="sxs-lookup"><span data-stu-id="7ac6b-118">This example uses <xref:System.Linq.Enumerable.Reverse%2A> to create a list of orders where `OrderDate` is earlier than Feb 20, 2002.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#reverse)]
 [!code-vb[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#reverse)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="7ac6b-119">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="7ac6b-119">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="7ac6b-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="7ac6b-120">Example</span></span>  
 <span data-ttu-id="7ac6b-121">Tento příklad používá `OrderBy… Descending` , což je totéž jako <xref:System.Linq.Enumerable.ThenByDescending%2A> metoda seřadit seznam produktů, nejprve podle názvu a pak podle ceníku, od nejvyšší po nejnižší.</span><span class="sxs-lookup"><span data-stu-id="7ac6b-121">This example uses `OrderBy… Descending` , which is equivalent to the <xref:System.Linq.Enumerable.ThenByDescending%2A> method, to sort a list of products, first by name and then by list price, from highest to lowest.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ThenByDescendingSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#thenbydescendingsimple)]
 [!code-vb[DP LINQ to DataSet Examples#ThenByDescendingSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#thenbydescendingsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="7ac6b-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="7ac6b-122">See Also</span></span>  
 [<span data-ttu-id="7ac6b-123">Načítání dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="7ac6b-123">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="7ac6b-124">LINQ na DataSet příklady</span><span class="sxs-lookup"><span data-stu-id="7ac6b-124">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="7ac6b-125">Přehled standardních operátorů dotazu</span><span class="sxs-lookup"><span data-stu-id="7ac6b-125">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
