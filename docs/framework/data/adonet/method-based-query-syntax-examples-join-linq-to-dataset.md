---
title: 'Příklady syntaxe dotazů založených na volání metody: Připojte se k (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4fd5ed2c-b03a-4054-a3ed-3ddb380d7d9d
ms.openlocfilehash: 84bd5f48c993dc5b15104b70081f739a1bec2e5c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59152474"
---
# <a name="method-based-query-syntax-examples-join-linq-to-dataset"></a><span data-ttu-id="038e6-102">Příklady syntaxe dotazů založených na volání metody: Připojte se k (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="038e6-102">Method-Based Query Syntax Examples: Join (LINQ to DataSet)</span></span>
<span data-ttu-id="038e6-103">Připojení je důležité operace v dotazech, které se zaměřují zdroje dat, které jste žádné relace navigaci k sobě navzájem, jako je například tabulek relační databáze.</span><span class="sxs-lookup"><span data-stu-id="038e6-103">Joining is an important operation in queries that target data sources that have no navigable relationships to each other, such as relational database tables.</span></span> <span data-ttu-id="038e6-104">Přidružení objektů v jednom zdroji dat s objekty, které sdílejí společný atribut v jiném zdroji dat. je spojení dvou datových zdrojů.</span><span class="sxs-lookup"><span data-stu-id="038e6-104">A join of two data sources is the association of objects in one data source with objects that share a common attribute in the other data source.</span></span> <span data-ttu-id="038e6-105">Další informace najdete v tématu [přehled standardních operátorů dotazu (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) nebo [přehled operátory standardního dotazu (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="038e6-105">For more information, see [Standard Query Operators Overview (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) or [Standard Query Operators Overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
 <span data-ttu-id="038e6-106">Příklady v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Join%2A> metodu dotazu <xref:System.Data.DataSet> pomocí syntaxe metody dotazu.</span><span class="sxs-lookup"><span data-stu-id="038e6-106">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Join%2A> method to query a <xref:System.Data.DataSet> using the method query syntax.</span></span>  
  
 <span data-ttu-id="038e6-107">`FillDataSet` Metodu použitou v těchto příkladech je zadán v [načítání dat do datová sada](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="038e6-107">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="038e6-108">Příklady v tomto tématu použijte tabulky Kontakt, adresa, produktu, SalesOrderHeader a podrobnosti prodejní objednávky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="038e6-108">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="038e6-109">V příkladech v tomto tématu se používá následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="038e6-109">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="038e6-110">Další informace najdete v tématu [jak: Vytvoření LINQ to DataSet projektu v sadě Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="038e6-110">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="join"></a><span data-ttu-id="038e6-111">Join</span><span class="sxs-lookup"><span data-stu-id="038e6-111">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="038e6-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="038e6-112">Example</span></span>  
 <span data-ttu-id="038e6-113">V tomto příkladu provádí spojení `Contact` a `SalesOrderHeader` tabulky.</span><span class="sxs-lookup"><span data-stu-id="038e6-113">This example performs a join over the `Contact` and `SalesOrderHeader` tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a><span data-ttu-id="038e6-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="038e6-114">Example</span></span>  
 <span data-ttu-id="038e6-115">V tomto příkladu provádí spojení `Contact` a `SalesOrderHeader` obraťte se na tabulky, seskupení výsledků podle ID.</span><span class="sxs-lookup"><span data-stu-id="038e6-115">This example performs a join over the `Contact` and `SalesOrderHeader` tables, grouping the results by contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="038e6-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="038e6-116">See also</span></span>

- [<span data-ttu-id="038e6-117">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="038e6-117">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="038e6-118">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="038e6-118">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [<span data-ttu-id="038e6-119">Přehled standardních operátorů dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="038e6-119">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="038e6-120">Přehled standardních operátorů dotazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="038e6-120">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="038e6-121">Připojte se k ukázky</span><span class="sxs-lookup"><span data-stu-id="038e6-121">Join Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=187357)
- [<span data-ttu-id="038e6-122">Datovou sadu ukázky</span><span class="sxs-lookup"><span data-stu-id="038e6-122">Dataset Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=187358)
