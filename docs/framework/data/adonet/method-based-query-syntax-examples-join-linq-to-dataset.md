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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: c4f5e5d975627377c8d2098e42637076a5e04db5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="method-based-query-syntax-examples-join-linq-to-dataset"></a><span data-ttu-id="6b597-102">Příklady syntaxe dotazů metoda: Spojení (LINQ na DataSet)</span><span class="sxs-lookup"><span data-stu-id="6b597-102">Method-Based Query Syntax Examples: Join (LINQ to DataSet)</span></span>
<span data-ttu-id="6b597-103">Připojení je důležité operace v dotazech, které cílí zdrojů dat, které nemají žádné navigaci relace mezi sebou, jako jsou tabulky relační databáze.</span><span class="sxs-lookup"><span data-stu-id="6b597-103">Joining is an important operation in queries that target data sources that have no navigable relationships to each other, such as relational database tables.</span></span> <span data-ttu-id="6b597-104">Spojení dvou zdrojů dat je přidružení objektů v jeden zdroj dat s objekty, které sdílejí společný atribut v datovém zdroji.</span><span class="sxs-lookup"><span data-stu-id="6b597-104">A join of two data sources is the association of objects in one data source with objects that share a common attribute in the other data source.</span></span> <span data-ttu-id="6b597-105">Další informace najdete v tématu [standardní přehled operátory dotazu](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span><span class="sxs-lookup"><span data-stu-id="6b597-105">For more information, see [Standard Query Operators Overview](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
 <span data-ttu-id="6b597-106">V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Join%2A> metodu pro dotaz <xref:System.Data.DataSet> pomocí syntaxe dotazu metoda.</span><span class="sxs-lookup"><span data-stu-id="6b597-106">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Join%2A> method to query a <xref:System.Data.DataSet> using the method query syntax.</span></span>  
  
 <span data-ttu-id="6b597-107">`FillDataSet` Metodu použitou v těchto příkladech je uveden v [načítání dat do datové sady](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="6b597-107">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="6b597-108">V příkladech v tomto tématu použijte kontaktu, adresu, produktu, SalesOrderHeader a podrobnosti prodejní objednávky tabulky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="6b597-108">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="6b597-109">V příkladech v tomto tématu použijte následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="6b597-109">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="6b597-110">Další informace najdete v tématu [postupy: vytvoření LINQ na DataSet projekt v sadě Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="6b597-110">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="join"></a><span data-ttu-id="6b597-111">Join</span><span class="sxs-lookup"><span data-stu-id="6b597-111">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="6b597-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="6b597-112">Example</span></span>  
 <span data-ttu-id="6b597-113">Tento příklad spojí přes `Contact` a `SalesOrderHeader` tabulky.</span><span class="sxs-lookup"><span data-stu-id="6b597-113">This example performs a join over the `Contact` and `SalesOrderHeader` tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a><span data-ttu-id="6b597-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="6b597-114">Example</span></span>  
 <span data-ttu-id="6b597-115">Tento příklad spojí přes `Contact` a `SalesOrderHeader` obraťte se na tabulky, seskupení výsledků podle ID.</span><span class="sxs-lookup"><span data-stu-id="6b597-115">This example performs a join over the `Contact` and `SalesOrderHeader` tables, grouping the results by contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="6b597-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="6b597-116">See Also</span></span>  
 [<span data-ttu-id="6b597-117">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="6b597-117">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="6b597-118">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="6b597-118">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="6b597-119">Přehled standardních operátorů dotazu</span><span class="sxs-lookup"><span data-stu-id="6b597-119">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)  
 [<span data-ttu-id="6b597-120">JOIN – ukázky</span><span class="sxs-lookup"><span data-stu-id="6b597-120">Join Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=187357)  
 [<span data-ttu-id="6b597-121">Ukázky datové sady</span><span class="sxs-lookup"><span data-stu-id="6b597-121">Dataset Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=187358)
