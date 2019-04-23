---
title: 'Příklady syntaxe výrazů dotazů: Řazení (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 653a4a97-1e4a-4b2d-8d24-7dbe1f2a5c84
ms.openlocfilehash: b8f605eaa3a186ebb6bad7800d6576bd4d5a34b3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59203896"
---
# <a name="query-expression-syntax-examples-ordering-linq-to-dataset"></a><span data-ttu-id="3b83b-102">Příklady syntaxe výrazů dotazů: Řazení (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="3b83b-102">Query Expression Syntax Examples: Ordering (LINQ to DataSet)</span></span>
<span data-ttu-id="3b83b-103">Příklady v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, a <xref:System.Linq.Enumerable.ThenByDescending%2A> metody pro dotazování <xref:System.Data.DataSet> a řazení výsledků pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="3b83b-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenByDescending%2A> methods to query a <xref:System.Data.DataSet> and order the results using the query expression syntax.</span></span>  
  
 <span data-ttu-id="3b83b-104">`FillDataSet` Metodu použitou v těchto příkladech je zadán v [načítání dat do datová sada](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="3b83b-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="3b83b-105">Příklady v tomto tématu použijte tabulky Kontakt, adresa, produktu, SalesOrderHeader a podrobnosti prodejní objednávky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="3b83b-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="3b83b-106">V příkladech v tomto tématu se používá následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="3b83b-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="3b83b-107">Další informace najdete v tématu [jak: Vytvoření LINQ to DataSet projektu v sadě Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="3b83b-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="orderby"></a><span data-ttu-id="3b83b-108">Řadit podle</span><span class="sxs-lookup"><span data-stu-id="3b83b-108">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="3b83b-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="3b83b-109">Example</span></span>  
 <span data-ttu-id="3b83b-110">Tento příklad používá <xref:System.Linq.Enumerable.OrderBy%2A> vrátila seznam kontaktů seřazené podle příjmení.</span><span class="sxs-lookup"><span data-stu-id="3b83b-110">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> to return a list of contacts ordered by last name.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderBySimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbysimple1)]
 [!code-vb[DP LINQ to DataSet Examples#OrderBySimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbysimple1)]  
  
### <a name="example"></a><span data-ttu-id="3b83b-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="3b83b-111">Example</span></span>  
 <span data-ttu-id="3b83b-112">Tento příklad používá <xref:System.Linq.Enumerable.OrderBy%2A> seřadíte seznam kontaktů podle délky příjmení.</span><span class="sxs-lookup"><span data-stu-id="3b83b-112">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> to sort a list of contacts by length of last name.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderBySimple2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbysimple2)]
 [!code-vb[DP LINQ to DataSet Examples#OrderBySimple2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbysimple2)]  
  
## <a name="orderbydescending"></a><span data-ttu-id="3b83b-113">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="3b83b-113">OrderByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="3b83b-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="3b83b-114">Example</span></span>  
 <span data-ttu-id="3b83b-115">Tento příklad používá `orderby… descending` (`Order By … Descending`), což je totéž jako <xref:System.Linq.Enumerable.OrderByDescending%2A> metoda seřadíte seznam cena od nejvyšší k nejnižší.</span><span class="sxs-lookup"><span data-stu-id="3b83b-115">This example uses `orderby… descending` (`Order By … Descending`), which is equivalent to the <xref:System.Linq.Enumerable.OrderByDescending%2A> method, to sort the price list from highest to lowest.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderByDescendingSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbydescendingsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#OrderByDescendingSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbydescendingsimple1)]  
  
## <a name="reverse"></a><span data-ttu-id="3b83b-116">reverzní</span><span class="sxs-lookup"><span data-stu-id="3b83b-116">Reverse</span></span>  
  
### <a name="example"></a><span data-ttu-id="3b83b-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="3b83b-117">Example</span></span>  
 <span data-ttu-id="3b83b-118">Tento příklad používá <xref:System.Linq.Enumerable.Reverse%2A> pro vytvoření seznamu objednávek, ve kterém `OrderDate` je starší než 20. února 2002.</span><span class="sxs-lookup"><span data-stu-id="3b83b-118">This example uses <xref:System.Linq.Enumerable.Reverse%2A> to create a list of orders where `OrderDate` is earlier than Feb 20, 2002.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#reverse)]
 [!code-vb[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#reverse)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="3b83b-119">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="3b83b-119">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="3b83b-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="3b83b-120">Example</span></span>  
 <span data-ttu-id="3b83b-121">Tento příklad používá `OrderBy… Descending` , což je totéž jako <xref:System.Linq.Enumerable.ThenByDescending%2A> metoda seřadíte seznam produktů, nejprve podle názvu a pak podle ceníku od nejvyšší k nejnižší.</span><span class="sxs-lookup"><span data-stu-id="3b83b-121">This example uses `OrderBy… Descending` , which is equivalent to the <xref:System.Linq.Enumerable.ThenByDescending%2A> method, to sort a list of products, first by name and then by list price, from highest to lowest.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ThenByDescendingSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#thenbydescendingsimple)]
 [!code-vb[DP LINQ to DataSet Examples#ThenByDescendingSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#thenbydescendingsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="3b83b-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3b83b-122">See also</span></span>

- [<span data-ttu-id="3b83b-123">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="3b83b-123">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="3b83b-124">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="3b83b-124">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [<span data-ttu-id="3b83b-125">Přehled standardních operátorů dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="3b83b-125">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="3b83b-126">Přehled standardních operátorů dotazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b83b-126">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
