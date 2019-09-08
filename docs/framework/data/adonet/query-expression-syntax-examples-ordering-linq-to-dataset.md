---
title: 'Příklady syntaxe výrazů dotazů: Řazení (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 653a4a97-1e4a-4b2d-8d24-7dbe1f2a5c84
ms.openlocfilehash: 932f5e4f6073844a951d06dabec45e5ff3e743bf
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782992"
---
# <a name="query-expression-syntax-examples-ordering-linq-to-dataset"></a><span data-ttu-id="0e0be-102">Příklady syntaxe výrazů dotazů: Řazení (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="0e0be-102">Query Expression Syntax Examples: Ordering (LINQ to DataSet)</span></span>
<span data-ttu-id="0e0be-103">Příklady v tomto tématu <xref:System.Linq.Enumerable.OrderBy%2A>ukazují, jak použít <xref:System.Linq.Enumerable.ThenByDescending%2A> metody, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>a k dotazování <xref:System.Data.DataSet> a seřazení výsledků pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="0e0be-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenByDescending%2A> methods to query a <xref:System.Data.DataSet> and order the results using the query expression syntax.</span></span>  
  
 <span data-ttu-id="0e0be-104">Metoda použitá v těchto příkladech je určena při [načítání dat do datové sady.](loading-data-into-a-dataset.md) `FillDataSet`</span><span class="sxs-lookup"><span data-stu-id="0e0be-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="0e0be-105">V příkladech v tomto tématu se používá tabulka Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="0e0be-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="0e0be-106">Příklady v tomto tématu používají následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="0e0be-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="0e0be-107">Další informace najdete v tématu [jak: Vytvoření projektu LINQ to DataSet v aplikaci Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="0e0be-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="orderby"></a><span data-ttu-id="0e0be-108">OrderBy</span><span class="sxs-lookup"><span data-stu-id="0e0be-108">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="0e0be-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="0e0be-109">Example</span></span>  
 <span data-ttu-id="0e0be-110">Tento příklad používá <xref:System.Linq.Enumerable.OrderBy%2A> k vrácení seznamu kontaktů seřazené podle příjmení.</span><span class="sxs-lookup"><span data-stu-id="0e0be-110">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> to return a list of contacts ordered by last name.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderBySimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbysimple1)]
 [!code-vb[DP LINQ to DataSet Examples#OrderBySimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbysimple1)]  
  
### <a name="example"></a><span data-ttu-id="0e0be-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="0e0be-111">Example</span></span>  
 <span data-ttu-id="0e0be-112">Tento příklad používá <xref:System.Linq.Enumerable.OrderBy%2A> k řazení seznamu kontaktů podle délky příjmení.</span><span class="sxs-lookup"><span data-stu-id="0e0be-112">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> to sort a list of contacts by length of last name.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderBySimple2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbysimple2)]
 [!code-vb[DP LINQ to DataSet Examples#OrderBySimple2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbysimple2)]  
  
## <a name="orderbydescending"></a><span data-ttu-id="0e0be-113">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="0e0be-113">OrderByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="0e0be-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="0e0be-114">Example</span></span>  
 <span data-ttu-id="0e0be-115">Tento příklad používá `orderby… descending` (`Order By … Descending`), <xref:System.Linq.Enumerable.OrderByDescending%2A> který je ekvivalentní metodě, k řazení ceníku od nejvyšší po nejnižší.</span><span class="sxs-lookup"><span data-stu-id="0e0be-115">This example uses `orderby… descending` (`Order By … Descending`), which is equivalent to the <xref:System.Linq.Enumerable.OrderByDescending%2A> method, to sort the price list from highest to lowest.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderByDescendingSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbydescendingsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#OrderByDescendingSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbydescendingsimple1)]  
  
## <a name="reverse"></a><span data-ttu-id="0e0be-116">Zpět</span><span class="sxs-lookup"><span data-stu-id="0e0be-116">Reverse</span></span>  
  
### <a name="example"></a><span data-ttu-id="0e0be-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="0e0be-117">Example</span></span>  
 <span data-ttu-id="0e0be-118">Tento příklad používá <xref:System.Linq.Enumerable.Reverse%2A> k vytvoření seznamu objednávek, kde `OrderDate` je dřívější než 20. února 2002.</span><span class="sxs-lookup"><span data-stu-id="0e0be-118">This example uses <xref:System.Linq.Enumerable.Reverse%2A> to create a list of orders where `OrderDate` is earlier than Feb 20, 2002.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#reverse)]
 [!code-vb[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#reverse)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="0e0be-119">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="0e0be-119">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="0e0be-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="0e0be-120">Example</span></span>  
 <span data-ttu-id="0e0be-121">Tento příklad používá `OrderBy… Descending` , který je ekvivalentní <xref:System.Linq.Enumerable.ThenByDescending%2A> metodě, pro seřazení seznamu produktů, nejprve podle názvu a podle ceny za seznam, od nejvyšší po nejnižší.</span><span class="sxs-lookup"><span data-stu-id="0e0be-121">This example uses `OrderBy… Descending` , which is equivalent to the <xref:System.Linq.Enumerable.ThenByDescending%2A> method, to sort a list of products, first by name and then by list price, from highest to lowest.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ThenByDescendingSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#thenbydescendingsimple)]
 [!code-vb[DP LINQ to DataSet Examples#ThenByDescendingSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#thenbydescendingsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="0e0be-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0e0be-122">See also</span></span>

- [<span data-ttu-id="0e0be-123">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="0e0be-123">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="0e0be-124">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="0e0be-124">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="0e0be-125">Přehled standardních operátorů dotazůC#()</span><span class="sxs-lookup"><span data-stu-id="0e0be-125">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="0e0be-126">Přehled standardních operátorů dotazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0e0be-126">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
