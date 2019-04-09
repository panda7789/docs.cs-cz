---
title: 'Příklady syntaxe výrazů dotazů: Agregační operátory (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 85dafa07-e102-46e7-ab78-37bf06f257a6
ms.openlocfilehash: e7151fd85c7e3988051ed87a60acc2b53a8af646
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122769"
---
# <a name="query-expression-syntax-examples-aggregate-operators-linq-to-dataset"></a><span data-ttu-id="88e67-102">Příklady syntaxe výrazů dotazů: Agregační operátory (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="88e67-102">Query Expression Syntax Examples: Aggregate Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="88e67-103">Příklady v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, a <xref:System.Linq.Enumerable.Sum%2A> metody pro dotazování <xref:System.Data.DataSet> a agregace dat pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="88e67-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query a <xref:System.Data.DataSet> and aggregate data using query expression syntax.</span></span>  
  
 <span data-ttu-id="88e67-104">`FillDataSet` Metodu použitou v těchto příkladech je zadán v [načítání dat do datová sada](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="88e67-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="88e67-105">Příklady v tomto tématu použijte tabulky Kontakt, adresa, produktu, SalesOrderHeader a podrobnosti prodejní objednávky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="88e67-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="88e67-106">V příkladech v tomto tématu se používá následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="88e67-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="88e67-107">Další informace najdete v tématu [jak: Vytvoření LINQ to DataSet projektu v sadě Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="88e67-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="average"></a><span data-ttu-id="88e67-108">Průměr</span><span class="sxs-lookup"><span data-stu-id="88e67-108">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="88e67-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="88e67-109">Example</span></span>  
 <span data-ttu-id="88e67-110">V tomto příkladu <xref:System.Linq.Enumerable.Average%2A> metody k vyhledání průměrná cena seznam produktů jednotlivých stylů.</span><span class="sxs-lookup"><span data-stu-id="88e67-110">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="88e67-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="88e67-111">Example</span></span>  
 <span data-ttu-id="88e67-112">Tento příklad používá <xref:System.Linq.Enumerable.Average%2A> k zjistit průměrné celkové potřebné pro každé obraťte se na ID.</span><span class="sxs-lookup"><span data-stu-id="88e67-112">This example uses <xref:System.Linq.Enumerable.Average%2A> to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="88e67-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="88e67-113">Example</span></span>  
 <span data-ttu-id="88e67-114">Tento příklad používá <xref:System.Linq.Enumerable.Average%2A> získat objednávky s průměrem `TotalDue` každého kontaktu.</span><span class="sxs-lookup"><span data-stu-id="88e67-114">This example uses <xref:System.Linq.Enumerable.Average%2A> to get the orders with the average `TotalDue` for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="88e67-115">Počet</span><span class="sxs-lookup"><span data-stu-id="88e67-115">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="88e67-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="88e67-116">Example</span></span>  
 <span data-ttu-id="88e67-117">Tento příklad používá <xref:System.Linq.Enumerable.Count%2A> vrátí seznam ID kontaktu a kolik objednávky, každá má.</span><span class="sxs-lookup"><span data-stu-id="88e67-117">This example uses <xref:System.Linq.Enumerable.Count%2A> to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countnested)]
 [!code-vb[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="88e67-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="88e67-118">Example</span></span>  
 <span data-ttu-id="88e67-119">Tento příklad skupiny produktů pomocí barev a používá <xref:System.Linq.Enumerable.Count%2A> k vrácení počtu produktů v každé skupině barvu.</span><span class="sxs-lookup"><span data-stu-id="88e67-119">This example groups products by color and uses <xref:System.Linq.Enumerable.Count%2A> to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="max"></a><span data-ttu-id="88e67-120">Maximum</span><span class="sxs-lookup"><span data-stu-id="88e67-120">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="88e67-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="88e67-121">Example</span></span>  
 <span data-ttu-id="88e67-122">V tomto příkladu <xref:System.Linq.Enumerable.Max%2A> metodu k získání největší dlužná pro každou obraťte se na ID.</span><span class="sxs-lookup"><span data-stu-id="88e67-122">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="88e67-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="88e67-123">Example</span></span>  
 <span data-ttu-id="88e67-124">V tomto příkladu <xref:System.Linq.Enumerable.Max%2A> metodu k získání objednávky s nejvyšší `TotalDue` pro každou obraťte se na ID.</span><span class="sxs-lookup"><span data-stu-id="88e67-124">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest `TotalDue` for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="88e67-125">Minimum</span><span class="sxs-lookup"><span data-stu-id="88e67-125">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="88e67-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="88e67-126">Example</span></span>  
 <span data-ttu-id="88e67-127">V tomto příkladu <xref:System.Linq.Enumerable.Min%2A> metodu k získání nejmenší dlužná pro každou obraťte se na ID.</span><span class="sxs-lookup"><span data-stu-id="88e67-127">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="88e67-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="88e67-128">Example</span></span>  
 <span data-ttu-id="88e67-129">V tomto příkladu <xref:System.Linq.Enumerable.Min%2A> metodu k získání objednávky nejmenší celkem termín pro každého kontaktu.</span><span class="sxs-lookup"><span data-stu-id="88e67-129">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="88e67-130">Součet</span><span class="sxs-lookup"><span data-stu-id="88e67-130">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="88e67-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="88e67-131">Example</span></span>  
 <span data-ttu-id="88e67-132">V tomto příkladu <xref:System.Linq.Enumerable.Sum%2A> metodu k získání celkové splatnosti pro každou obraťte se na ID.</span><span class="sxs-lookup"><span data-stu-id="88e67-132">This example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="88e67-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="88e67-133">See also</span></span>

- [<span data-ttu-id="88e67-134">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="88e67-134">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="88e67-135">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="88e67-135">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [<span data-ttu-id="88e67-136">Přehled standardních operátorů dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="88e67-136">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="88e67-137">Přehled standardních operátorů dotazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="88e67-137">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
