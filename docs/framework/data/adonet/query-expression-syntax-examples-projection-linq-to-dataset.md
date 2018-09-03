---
title: 'Příklady syntaxe výrazů dotazů: Projekce (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 48c9f5ed-76bf-4228-ab10-5217bbb295a3
ms.openlocfilehash: 92e013647b4f4b6ba14d46add24d5d71a6875bb0
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43470733"
---
# <a name="query-expression-syntax-examples-projection--linq-to-dataset"></a><span data-ttu-id="057dd-102">Příklady syntaxe výrazů dotazů: Projekce (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="057dd-102">Query Expression Syntax Examples: Projection  (LINQ to DataSet)</span></span>
<span data-ttu-id="057dd-103">Příklady v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Select%2A> a <xref:System.Linq.Enumerable.SelectMany%2A> metody pro dotazování <xref:System.Data.DataSet> pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="057dd-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="057dd-104">`FillDataSet` Metodu použitou v těchto příkladech je zadán v [načítání dat do datová sada](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="057dd-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="057dd-105">Příklady v tomto tématu použijte tabulky Kontakt, adresa, produktu, SalesOrderHeader a podrobnosti prodejní objednávky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="057dd-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="057dd-106">V příkladech v tomto tématu se používá následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="057dd-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="057dd-107">Další informace najdete v tématu [postupy: vytvoření LINQ to DataSet projektu v sadě Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="057dd-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="select"></a><span data-ttu-id="057dd-108">Vyberte</span><span class="sxs-lookup"><span data-stu-id="057dd-108">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="057dd-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="057dd-109">Example</span></span>  
 <span data-ttu-id="057dd-110">V tomto příkladu <xref:System.Linq.Enumerable.Select%2A> metody, která vrátí všechny řádky z `Product` tabulky a zobrazení názvů produktů.</span><span class="sxs-lookup"><span data-stu-id="057dd-110">This example uses the <xref:System.Linq.Enumerable.Select%2A> method to return all the rows from the `Product` table and display the product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="example"></a><span data-ttu-id="057dd-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="057dd-111">Example</span></span>  
 <span data-ttu-id="057dd-112">Tento příklad používá <xref:System.Linq.Enumerable.Select%2A> k vrácení sekvence pouze názvy produktů.</span><span class="sxs-lookup"><span data-stu-id="057dd-112">This example uses <xref:System.Linq.Enumerable.Select%2A> to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple2)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple2)]  
  
## <a name="selectmany"></a><span data-ttu-id="057dd-113">Operátor SelectMany</span><span class="sxs-lookup"><span data-stu-id="057dd-113">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="057dd-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="057dd-114">Example</span></span>  
 <span data-ttu-id="057dd-115">Tento příklad používá `From …, …` (ekvivalent <xref:System.Linq.Enumerable.SelectMany%2A> metoda) Chcete-li vybrat všechny objednávky where `TotalDue` je menší než 500,00.</span><span class="sxs-lookup"><span data-stu-id="057dd-115">This example uses `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom)]  
  
### <a name="example"></a><span data-ttu-id="057dd-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="057dd-116">Example</span></span>  
 <span data-ttu-id="057dd-117">V tomto příkladu `From …, …` (ekvivalent <xref:System.Linq.Enumerable.SelectMany%2A> metoda) Chcete-li vybrat všechny objednávky, kde byla provedena pořadí 1. října 2002 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="057dd-117">This example uses `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom2)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom2)]  
  
### <a name="example"></a><span data-ttu-id="057dd-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="057dd-118">Example</span></span>  
 <span data-ttu-id="057dd-119">V tomto příkladu `From …, …` (ekvivalent <xref:System.Linq.Enumerable.SelectMany%2A> – metoda) Chcete-li vybrat všechny objednávky, kde je větší než 10000.00 a používá celkového pořadí `From` přiřazení žádosti o celkové dvakrát, aby.</span><span class="sxs-lookup"><span data-stu-id="057dd-119">This example uses a `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order total is greater than 10000.00 and uses `From` assignment to avoid requesting the total twice.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyFromAssignment](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanyfromassignment)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyFromAssignment](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanyfromassignment)]  
  
## <a name="see-also"></a><span data-ttu-id="057dd-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="057dd-120">See Also</span></span>  
 [<span data-ttu-id="057dd-121">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="057dd-121">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="057dd-122">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="057dd-122">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="057dd-123">Přehled standardních operátorů dotazu</span><span class="sxs-lookup"><span data-stu-id="057dd-123">Standard Query Operators Overview</span></span>](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
