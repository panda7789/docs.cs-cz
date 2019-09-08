---
title: 'Příklady syntaxe dotazů založených na volání metody: Připojit (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4fd5ed2c-b03a-4054-a3ed-3ddb380d7d9d
ms.openlocfilehash: ba6e33f98e063aab946db27b97106272c5adef63
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783670"
---
# <a name="method-based-query-syntax-examples-join-linq-to-dataset"></a><span data-ttu-id="bdd92-102">Příklady syntaxe dotazů založených na volání metody: Připojit (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="bdd92-102">Method-Based Query Syntax Examples: Join (LINQ to DataSet)</span></span>
<span data-ttu-id="bdd92-103">Spojování je důležitou operací v dotazech, které cílí na zdroje dat, které nemají žádné vztahy naviguje, například tabulky relačních databází.</span><span class="sxs-lookup"><span data-stu-id="bdd92-103">Joining is an important operation in queries that target data sources that have no navigable relationships to each other, such as relational database tables.</span></span> <span data-ttu-id="bdd92-104">Spojení dvou zdrojů dat je přidružení objektů v jednom zdroji dat s objekty, které sdílejí společný atribut v jiném zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="bdd92-104">A join of two data sources is the association of objects in one data source with objects that share a common attribute in the other data source.</span></span> <span data-ttu-id="bdd92-105">Další informace najdete v tématu Přehled [standardních operátorů dotazůC#()](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) nebo [standardní operátory dotazu (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bdd92-105">For more information, see [Standard Query Operators Overview (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) or [Standard Query Operators Overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
 <span data-ttu-id="bdd92-106">Příklady v tomto tématu ukazují, jak použít <xref:System.Linq.Enumerable.Join%2A> metodu pro <xref:System.Data.DataSet> dotazování pomocí syntaxe dotazu metody.</span><span class="sxs-lookup"><span data-stu-id="bdd92-106">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Join%2A> method to query a <xref:System.Data.DataSet> using the method query syntax.</span></span>  
  
 <span data-ttu-id="bdd92-107">Metoda použitá v těchto příkladech je určena při [načítání dat do datové sady.](loading-data-into-a-dataset.md) `FillDataSet`</span><span class="sxs-lookup"><span data-stu-id="bdd92-107">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="bdd92-108">V příkladech v tomto tématu se používá tabulka Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="bdd92-108">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="bdd92-109">Příklady v tomto tématu používají následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="bdd92-109">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="bdd92-110">Další informace najdete v tématu [jak: Vytvoření projektu LINQ to DataSet v aplikaci Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="bdd92-110">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="join"></a><span data-ttu-id="bdd92-111">Join</span><span class="sxs-lookup"><span data-stu-id="bdd92-111">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="bdd92-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="bdd92-112">Example</span></span>  
 <span data-ttu-id="bdd92-113">V tomto příkladu se provádí spojení `Contact` s tabulkami a. `SalesOrderHeader`</span><span class="sxs-lookup"><span data-stu-id="bdd92-113">This example performs a join over the `Contact` and `SalesOrderHeader` tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a><span data-ttu-id="bdd92-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="bdd92-114">Example</span></span>  
 <span data-ttu-id="bdd92-115">Tento příklad provede spojení `Contact` s tabulkami a a `SalesOrderHeader` seskupí výsledky podle ID kontaktu.</span><span class="sxs-lookup"><span data-stu-id="bdd92-115">This example performs a join over the `Contact` and `SalesOrderHeader` tables, grouping the results by contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="bdd92-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bdd92-116">See also</span></span>

- [<span data-ttu-id="bdd92-117">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="bdd92-117">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="bdd92-118">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="bdd92-118">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="bdd92-119">Přehled standardních operátorů dotazůC#()</span><span class="sxs-lookup"><span data-stu-id="bdd92-119">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="bdd92-120">Přehled standardních operátorů dotazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bdd92-120">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="bdd92-121">Připojit vzorky</span><span class="sxs-lookup"><span data-stu-id="bdd92-121">Join Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=187357)
- [<span data-ttu-id="bdd92-122">Ukázky datových sad</span><span class="sxs-lookup"><span data-stu-id="bdd92-122">Dataset Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=187358)
