---
title: "Příklady syntaxe výrazu dotazu: Omezení (LINQ na DataSet)"
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
ms.assetid: 1daf42c2-c9f4-4cda-b291-7641b9c6d3fe
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f7d2f0dabc8c32d387af21e14466254039fde502
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="query-expression-syntax-examples-restriction-linq-to-dataset"></a><span data-ttu-id="e5dfa-102">Příklady syntaxe výrazu dotazu: Omezení (LINQ na DataSet)</span><span class="sxs-lookup"><span data-stu-id="e5dfa-102">Query Expression Syntax Examples: Restriction (LINQ to DataSet)</span></span>
<span data-ttu-id="e5dfa-103">V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Where%2A> metodu pro dotaz <xref:System.Data.DataSet> pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="e5dfa-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Where%2A> method to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="e5dfa-104">`FillDataSet` Metodu použitou v těchto příkladech je uveden v [načítání dat do datové sady](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="e5dfa-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="e5dfa-105">V příkladech v tomto tématu použijte kontaktu, adresu, produktu, SalesOrderHeader a podrobnosti prodejní objednávky tabulky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e5dfa-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="e5dfa-106">V příkladech v tomto tématu použijte následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="e5dfa-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
[!code-csharp[DP LINQ to DataSetExamples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]        
  
 <span data-ttu-id="e5dfa-107">Další informace najdete v tématu [postupy: vytvoření LINQ na DataSet projekt v sadě Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="e5dfa-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="where"></a><span data-ttu-id="e5dfa-108">Where</span><span class="sxs-lookup"><span data-stu-id="e5dfa-108">Where</span></span>  
  
### <a name="example"></a><span data-ttu-id="e5dfa-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="e5dfa-109">Example</span></span>  
 <span data-ttu-id="e5dfa-110">Tento příklad vrátí všechny online objednávky.</span><span class="sxs-lookup"><span data-stu-id="e5dfa-110">This example returns all online orders.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where1)]  
 [!code-vb[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where1)]     
  
### <a name="example"></a><span data-ttu-id="e5dfa-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="e5dfa-111">Example</span></span>  
 <span data-ttu-id="e5dfa-112">Tento příklad vrátí objednávky, kde je větší než 2 a menší než 6 množství objednávky.</span><span class="sxs-lookup"><span data-stu-id="e5dfa-112">This example returns the orders where the order quantity is greater than 2 and less than 6.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where2)]  
 [!code-vb[DP LINQ to DataSet Examples#Where2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where2)]     
  
### <a name="example"></a><span data-ttu-id="e5dfa-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="e5dfa-113">Example</span></span>  
 <span data-ttu-id="e5dfa-114">Tento příklad vrátí všechny red barevnou produkty.</span><span class="sxs-lookup"><span data-stu-id="e5dfa-114">This example returns all red colored products.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]  
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]     
  
### <a name="example"></a><span data-ttu-id="e5dfa-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="e5dfa-115">Example</span></span>  
 <span data-ttu-id="e5dfa-116">Tento příklad používá <xref:System.Linq.Enumerable.Where%2A> metody k vyhledání objednávky, které byly provedeny po 1. prosince 2002 a pak používá <xref:System.Data.DataRow.GetChildRows%2A> metoda se získat podrobnosti pro každé pořadí.</span><span class="sxs-lookup"><span data-stu-id="e5dfa-116">This example uses the <xref:System.Linq.Enumerable.Where%2A> method to find orders that were made after December 1, 2002 and then uses the <xref:System.Data.DataRow.GetChildRows%2A> method to get the details for each order.</span></span>  
  
 [!code-csharp[DP LINQ to DataSetExamples#WhereDrillDown](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#wheredrilldown)]       
 [!code-vb[DP LINQ to DataSet Examples#WhereDrillDown](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#wheredrilldown)]  
  
## <a name="see-also"></a><span data-ttu-id="e5dfa-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="e5dfa-117">See Also</span></span>  
 [<span data-ttu-id="e5dfa-118">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="e5dfa-118">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="e5dfa-119">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="e5dfa-119">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="e5dfa-120">Přehled standardních operátorů dotazu</span><span class="sxs-lookup"><span data-stu-id="e5dfa-120">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
