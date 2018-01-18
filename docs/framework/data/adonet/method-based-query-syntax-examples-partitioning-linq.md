---
title: "Příklady syntaxe dotazů metoda: Vytváření oddílů (LINQ"
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
ms.assetid: a582c53f-f203-44ae-a797-d7f169a4fbb5
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 4cc73f3fd8988af78dc139b777ebaf9fa37b3e0e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="method-based-query-syntax-examples-partitioning-linq"></a><span data-ttu-id="71d81-102">Příklady syntaxe dotazů metoda: Vytváření oddílů (LINQ</span><span class="sxs-lookup"><span data-stu-id="71d81-102">Method-Based Query Syntax Examples: Partitioning (LINQ</span></span>
<span data-ttu-id="71d81-103">V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Skip%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A>, <xref:System.Linq.Enumerable.Take%2A>, a <xref:System.Linq.Enumerable.TakeWhile%2A> metody pro dotazování <xref:System.Data.DataSet> pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="71d81-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A>, <xref:System.Linq.Enumerable.Take%2A>, and <xref:System.Linq.Enumerable.TakeWhile%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="71d81-104">`FillDataSet` Metodu použitou v těchto příkladech je uveden v [načítání dat do datové sady](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="71d81-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="71d81-105">V příkladech v tomto tématu použijte kontaktu, adresu, produktu, SalesOrderHeader a podrobnosti prodejní objednávky tabulky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="71d81-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="71d81-106">V příkladech v tomto tématu použijte následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="71d81-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="71d81-107">Další informace najdete v tématu [postupy: vytvoření LINQ na DataSet projekt v sadě Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="71d81-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="skip"></a><span data-ttu-id="71d81-108">Skip</span><span class="sxs-lookup"><span data-stu-id="71d81-108">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="71d81-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="71d81-109">Example</span></span>  
 <span data-ttu-id="71d81-110">Tento příklad používá <xref:System.Linq.Enumerable.Skip%2A> metodu za účelem získání všech ale prvních pět kontakty z `Contact` tabulky.</span><span class="sxs-lookup"><span data-stu-id="71d81-110">This example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first five contacts of the `Contact` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipsimple)]
 [!code-vb[DP LINQ to DataSet Examples#SkipSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipsimple)]  
  
### <a name="example"></a><span data-ttu-id="71d81-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="71d81-111">Example</span></span>  
 <span data-ttu-id="71d81-112">Tento příklad používá <xref:System.Linq.Enumerable.Skip%2A> metodu za účelem získání všech ale nejprve dvou adres v Praze.</span><span class="sxs-lookup"><span data-stu-id="71d81-112">This example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipnested)]  
  
## <a name="skipwhile"></a><span data-ttu-id="71d81-113">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="71d81-113">SkipWhile</span></span>  
  
### <a name="example"></a><span data-ttu-id="71d81-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="71d81-114">Example</span></span>  
 <span data-ttu-id="71d81-115">Tento příklad používá <xref:System.Linq.Enumerable.OrderBy%2A> a <xref:System.Linq.Enumerable.SkipWhile%2A> metody vrátit produkty z `Product` tabulku s větší než 300.00 podle ceníku.</span><span class="sxs-lookup"><span data-stu-id="71d81-115">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> and <xref:System.Linq.Enumerable.SkipWhile%2A> methods to return products from the `Product` table with a list price greater than 300.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipWhileSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipwhilesimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SkipWhileSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipwhilesimple_mq)]  
  
## <a name="take"></a><span data-ttu-id="71d81-116">Take</span><span class="sxs-lookup"><span data-stu-id="71d81-116">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="71d81-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="71d81-117">Example</span></span>  
 <span data-ttu-id="71d81-118">Tento příklad používá <xref:System.Linq.Enumerable.Take%2A> metoda získat pouze prvních pět kontaktuje z `Contact` tabulky.</span><span class="sxs-lookup"><span data-stu-id="71d81-118">This example uses the <xref:System.Linq.Enumerable.Take%2A> method to get only the first five contacts from the `Contact` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takesimple)]
 [!code-vb[DP LINQ to DataSet Examples#TakeSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takesimple)]  
  
### <a name="example"></a><span data-ttu-id="71d81-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="71d81-119">Example</span></span>  
 <span data-ttu-id="71d81-120">Tento příklad používá <xref:System.Linq.Enumerable.Take%2A> metoda získat prvními třemi adresami v Praze.</span><span class="sxs-lookup"><span data-stu-id="71d81-120">This example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takenested)]
 [!code-vb[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takenested)]  
  
## <a name="takewhile"></a><span data-ttu-id="71d81-121">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="71d81-121">TakeWhile</span></span>  
  
### <a name="example"></a><span data-ttu-id="71d81-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="71d81-122">Example</span></span>  
 <span data-ttu-id="71d81-123">Tento příklad používá <xref:System.Linq.Enumerable.OrderBy%2A> a <xref:System.Linq.Enumerable.TakeWhile%2A> vrátit produkty z `Product` tabulku s seznamu cenu nižší než 300.00.</span><span class="sxs-lookup"><span data-stu-id="71d81-123">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> and <xref:System.Linq.Enumerable.TakeWhile%2A> to return products from the `Product` table with a list price less than 300.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeWhileSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takewhilesimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#TakeWhileSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takewhilesimple_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="71d81-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="71d81-124">See Also</span></span>  
 [<span data-ttu-id="71d81-125">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="71d81-125">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="71d81-126">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="71d81-126">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="71d81-127">Přehled standardních operátorů dotazu</span><span class="sxs-lookup"><span data-stu-id="71d81-127">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
