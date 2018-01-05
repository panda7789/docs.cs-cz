---
title: "Příklady syntaxe výrazu dotazu: Projekce (LINQ na DataSet)"
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
ms.assetid: 48c9f5ed-76bf-4228-ab10-5217bbb295a3
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3c44a510317dbc5f888bf5f2c8db8424df15cbd1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="query-expression-syntax-examples-projection--linq-to-dataset"></a><span data-ttu-id="af65f-102">Příklady syntaxe výrazu dotazu: Projekce (LINQ na DataSet)</span><span class="sxs-lookup"><span data-stu-id="af65f-102">Query Expression Syntax Examples: Projection  (LINQ to DataSet)</span></span>
<span data-ttu-id="af65f-103">V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Select%2A> a <xref:System.Linq.Enumerable.SelectMany%2A> metody pro dotazování <xref:System.Data.DataSet> pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="af65f-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="af65f-104">`FillDataSet` Metodu použitou v těchto příkladech je uveden v [načítání dat do datové sady](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="af65f-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="af65f-105">V příkladech v tomto tématu použijte kontaktu, adresu, produktu, SalesOrderHeader a podrobnosti prodejní objednávky tabulky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="af65f-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="af65f-106">V příkladech v tomto tématu použijte následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="af65f-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="af65f-107">Další informace najdete v tématu [postupy: vytvoření LINQ na DataSet projekt v sadě Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="af65f-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="select"></a><span data-ttu-id="af65f-108">Vyberte</span><span class="sxs-lookup"><span data-stu-id="af65f-108">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="af65f-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="af65f-109">Example</span></span>  
 <span data-ttu-id="af65f-110">Tento příklad používá <xref:System.Linq.Enumerable.Select%2A> metody, která vrátí všechny řádky z `Product` tabulky a zobrazení názvy produktů.</span><span class="sxs-lookup"><span data-stu-id="af65f-110">This example uses the <xref:System.Linq.Enumerable.Select%2A> method to return all the rows from the `Product` table and display the product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="example"></a><span data-ttu-id="af65f-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="af65f-111">Example</span></span>  
 <span data-ttu-id="af65f-112">Tento příklad používá <xref:System.Linq.Enumerable.Select%2A> vrátit posloupnost pouze názvy produktů.</span><span class="sxs-lookup"><span data-stu-id="af65f-112">This example uses <xref:System.Linq.Enumerable.Select%2A> to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple2)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple2)]  
  
## <a name="selectmany"></a><span data-ttu-id="af65f-113">Označit více</span><span class="sxs-lookup"><span data-stu-id="af65f-113">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="af65f-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="af65f-114">Example</span></span>  
 <span data-ttu-id="af65f-115">Tento příklad používá `From …, …` (ekvivalent <xref:System.Linq.Enumerable.SelectMany%2A> metoda) Chcete-li vybrat všechny řadí kde `TotalDue` je menší než 500,00.</span><span class="sxs-lookup"><span data-stu-id="af65f-115">This example uses `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom)]  
  
### <a name="example"></a><span data-ttu-id="af65f-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="af65f-116">Example</span></span>  
 <span data-ttu-id="af65f-117">Tento příklad používá `From …, …` (ekvivalent <xref:System.Linq.Enumerable.SelectMany%2A> metoda) Chcete-li vybrat všechny objednávky, kde byla provedena pořadí na 1. října 2002 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="af65f-117">This example uses `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom2)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom2)]  
  
### <a name="example"></a><span data-ttu-id="af65f-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="af65f-118">Example</span></span>  
 <span data-ttu-id="af65f-119">Tento příklad používá `From …, …` (ekvivalent <xref:System.Linq.Enumerable.SelectMany%2A> metoda) vyberete všechny objednávky, kde pořadí celkový počet je větší než 10000.00 a používá `From` přiřazení, aby se zabránilo požaduje celkový počet dvakrát.</span><span class="sxs-lookup"><span data-stu-id="af65f-119">This example uses a `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order total is greater than 10000.00 and uses `From` assignment to avoid requesting the total twice.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyFromAssignment](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanyfromassignment)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyFromAssignment](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanyfromassignment)]  
  
## <a name="see-also"></a><span data-ttu-id="af65f-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="af65f-120">See Also</span></span>  
 [<span data-ttu-id="af65f-121">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="af65f-121">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="af65f-122">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="af65f-122">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="af65f-123">Přehled standardních operátorů dotazu</span><span class="sxs-lookup"><span data-stu-id="af65f-123">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
