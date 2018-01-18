---
title: "Příklady syntaxe dotazů metoda: Spojení (LINQ na DataSet)"
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
ms.assetid: 4fd5ed2c-b03a-4054-a3ed-3ddb380d7d9d
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 42797c371b9aecfdc30db4abdcd065ffcd413c04
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="method-based-query-syntax-examples-join-linq-to-dataset"></a><span data-ttu-id="21571-102">Příklady syntaxe dotazů metoda: Spojení (LINQ na DataSet)</span><span class="sxs-lookup"><span data-stu-id="21571-102">Method-Based Query Syntax Examples: Join (LINQ to DataSet)</span></span>
<span data-ttu-id="21571-103">Připojení je důležité operace v dotazech, které cílí zdrojů dat, které nemají žádné navigaci relace mezi sebou, jako jsou tabulky relační databáze.</span><span class="sxs-lookup"><span data-stu-id="21571-103">Joining is an important operation in queries that target data sources that have no navigable relationships to each other, such as relational database tables.</span></span> <span data-ttu-id="21571-104">Spojení dvou zdrojů dat je přidružení objektů v jeden zdroj dat s objekty, které sdílejí společný atribut v datovém zdroji.</span><span class="sxs-lookup"><span data-stu-id="21571-104">A join of two data sources is the association of objects in one data source with objects that share a common attribute in the other data source.</span></span> <span data-ttu-id="21571-105">Další informace najdete v tématu [standardní přehled operátory dotazu](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span><span class="sxs-lookup"><span data-stu-id="21571-105">For more information, see [Standard Query Operators Overview](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
 <span data-ttu-id="21571-106">V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Join%2A> metodu pro dotaz <xref:System.Data.DataSet> pomocí syntaxe dotazu metoda.</span><span class="sxs-lookup"><span data-stu-id="21571-106">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Join%2A> method to query a <xref:System.Data.DataSet> using the method query syntax.</span></span>  
  
 <span data-ttu-id="21571-107">`FillDataSet` Metodu použitou v těchto příkladech je uveden v [načítání dat do datové sady](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="21571-107">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="21571-108">V příkladech v tomto tématu použijte kontaktu, adresu, produktu, SalesOrderHeader a podrobnosti prodejní objednávky tabulky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="21571-108">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="21571-109">V příkladech v tomto tématu použijte následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="21571-109">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="21571-110">Další informace najdete v tématu [postupy: vytvoření LINQ na DataSet projekt v sadě Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="21571-110">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="join"></a><span data-ttu-id="21571-111">Join</span><span class="sxs-lookup"><span data-stu-id="21571-111">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="21571-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="21571-112">Example</span></span>  
 <span data-ttu-id="21571-113">Tento příklad spojí přes `Contact` a `SalesOrderHeader` tabulky.</span><span class="sxs-lookup"><span data-stu-id="21571-113">This example performs a join over the `Contact` and `SalesOrderHeader` tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a><span data-ttu-id="21571-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="21571-114">Example</span></span>  
 <span data-ttu-id="21571-115">Tento příklad spojí přes `Contact` a `SalesOrderHeader` obraťte se na tabulky, seskupení výsledků podle ID.</span><span class="sxs-lookup"><span data-stu-id="21571-115">This example performs a join over the `Contact` and `SalesOrderHeader` tables, grouping the results by contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="21571-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="21571-116">See Also</span></span>  
 [<span data-ttu-id="21571-117">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="21571-117">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="21571-118">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="21571-118">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="21571-119">Přehled standardních operátorů dotazu</span><span class="sxs-lookup"><span data-stu-id="21571-119">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)  
 [<span data-ttu-id="21571-120">JOIN – ukázky</span><span class="sxs-lookup"><span data-stu-id="21571-120">Join Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=187357)  
 [<span data-ttu-id="21571-121">Ukázky datové sady</span><span class="sxs-lookup"><span data-stu-id="21571-121">Dataset Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=187358)
