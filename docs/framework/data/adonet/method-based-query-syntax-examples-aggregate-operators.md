---
title: 'Příklady syntaxe dotazů založených na volání metody: Agregační operátory (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5ed5f01d-acb2-4dd4-be60-f04c2d570fa8
ms.openlocfilehash: 88d9c7299c9dbf024a07f223ef7ec7d03f8066d8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215128"
---
# <a name="method-based-query-syntax-examples-aggregate-operators-linq-to-dataset"></a><span data-ttu-id="41e81-102">Příklady syntaxe dotazů založených na volání metody: Agregační operátory (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="41e81-102">Method-Based Query Syntax Examples: Aggregate Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="41e81-103">Příklady v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, a <xref:System.Linq.Enumerable.Sum%2A> operátory pro dotazování <xref:System.Data.DataSet> a agregace dat pomocí dotazů – metoda syntaxe.</span><span class="sxs-lookup"><span data-stu-id="41e81-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> operators to query a <xref:System.Data.DataSet> and aggregate data using method query syntax.</span></span>  
  
 <span data-ttu-id="41e81-104">`FillDataSet` Metodu použitou v těchto příkladech je zadán v [načítání dat do datová sada](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="41e81-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="41e81-105">Příklady v tomto tématu použijte tabulky Kontakt, adresa, produktu, SalesOrderHeader a podrobnosti prodejní objednávky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="41e81-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="41e81-106">V příkladech v tomto tématu se používá následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="41e81-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="41e81-107">Další informace najdete v tématu [jak: Vytvoření LINQ to DataSet projektu v sadě Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="41e81-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="aggregate"></a><span data-ttu-id="41e81-108">Aggregate</span><span class="sxs-lookup"><span data-stu-id="41e81-108">Aggregate</span></span>  
  
### <a name="example"></a><span data-ttu-id="41e81-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="41e81-109">Example</span></span>  
 <span data-ttu-id="41e81-110">V tomto příkladu <xref:System.Linq.Enumerable.Aggregate%2A> metodu k získání prvních 5 kontakty z `Contact` tabulky a sestavte seznam oddělený čárkami příjmení.</span><span class="sxs-lookup"><span data-stu-id="41e81-110">This example uses the <xref:System.Linq.Enumerable.Aggregate%2A> method to get the first 5 contacts from the `Contact` table and build a comma-delimited list of the last names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Aggregate_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#aggregate_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Aggregate_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#aggregate_mq)]  
  
## <a name="average"></a><span data-ttu-id="41e81-111">Průměr</span><span class="sxs-lookup"><span data-stu-id="41e81-111">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="41e81-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="41e81-112">Example</span></span>  
 <span data-ttu-id="41e81-113">V tomto příkladu <xref:System.Linq.Enumerable.Average%2A> metody k vyhledání průměrná cena seznamu produktů.</span><span class="sxs-lookup"><span data-stu-id="41e81-113">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Average_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#average_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Average_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#average_mq)]  
  
### <a name="example"></a><span data-ttu-id="41e81-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="41e81-114">Example</span></span>  
 <span data-ttu-id="41e81-115">V tomto příkladu <xref:System.Linq.Enumerable.Average%2A> metody k vyhledání průměrná cena seznam produktů jednotlivých stylů.</span><span class="sxs-lookup"><span data-stu-id="41e81-115">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="41e81-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="41e81-116">Example</span></span>  
 <span data-ttu-id="41e81-117">V tomto příkladu <xref:System.Linq.Enumerable.Average%2A> metody k vyhledání průměrné celkové potřebné.</span><span class="sxs-lookup"><span data-stu-id="41e81-117">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average total due.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averageprojection_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageProjection_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averageprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="41e81-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="41e81-118">Example</span></span>  
 <span data-ttu-id="41e81-119">V tomto příkladu <xref:System.Linq.Enumerable.Average%2A> ID metodu k získání celkové potřebné průměr pro každého kontaktu.</span><span class="sxs-lookup"><span data-stu-id="41e81-119">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="41e81-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="41e81-120">Example</span></span>  
 <span data-ttu-id="41e81-121">V tomto příkladu <xref:System.Linq.Enumerable.Average%2A> metodu k získání objednávky s průměrem `TotalDue` každého kontaktu.</span><span class="sxs-lookup"><span data-stu-id="41e81-121">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the orders with the average `TotalDue` for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="41e81-122">Počet</span><span class="sxs-lookup"><span data-stu-id="41e81-122">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="41e81-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="41e81-123">Example</span></span>  
 <span data-ttu-id="41e81-124">V tomto příkladu <xref:System.Linq.Enumerable.Count%2A> metody, která vrátí počet produktů `Product` tabulky.</span><span class="sxs-lookup"><span data-stu-id="41e81-124">This example uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in the `Product` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Count](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#count)]
 [!code-vb[DP LINQ to DataSet Examples#Count](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#count)]  
  
### <a name="example"></a><span data-ttu-id="41e81-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="41e81-125">Example</span></span>  
 <span data-ttu-id="41e81-126">V tomto příkladu <xref:System.Linq.Enumerable.Count%2A> metoda vrátí seznam ID kontaktu a kolik objednávky, každá má.</span><span class="sxs-lookup"><span data-stu-id="41e81-126">This example uses the <xref:System.Linq.Enumerable.Count%2A> method to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countnested)]
 [!code-vb[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="41e81-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="41e81-127">Example</span></span>  
 <span data-ttu-id="41e81-128">Tento příklad skupiny produktů pomocí barev a používá <xref:System.Linq.Enumerable.Count%2A> metody, která vrátí počet produktů v každé skupině barvu.</span><span class="sxs-lookup"><span data-stu-id="41e81-128">This example groups products by color and uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="longcount"></a><span data-ttu-id="41e81-129">LongCount</span><span class="sxs-lookup"><span data-stu-id="41e81-129">LongCount</span></span>  
  
### <a name="example"></a><span data-ttu-id="41e81-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="41e81-130">Example</span></span>  
 <span data-ttu-id="41e81-131">V tomto příkladu získá kontaktní počet jako dlouhé celé číslo.</span><span class="sxs-lookup"><span data-stu-id="41e81-131">This example gets the contact count as a long integer.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#LongCountSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#longcountsimple)]
 [!code-vb[DP LINQ to DataSet Examples#LongCountSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#longcountsimple)]  
  
## <a name="max"></a><span data-ttu-id="41e81-132">Maximum</span><span class="sxs-lookup"><span data-stu-id="41e81-132">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="41e81-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="41e81-133">Example</span></span>  
 <span data-ttu-id="41e81-134">V tomto příkladu <xref:System.Linq.Enumerable.Max%2A> metodu k získání největší celková částka.</span><span class="sxs-lookup"><span data-stu-id="41e81-134">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxprojection_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxProjection_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="41e81-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="41e81-135">Example</span></span>  
 <span data-ttu-id="41e81-136">V tomto příkladu <xref:System.Linq.Enumerable.Max%2A> metodu k získání největší dlužná pro každou obraťte se na ID.</span><span class="sxs-lookup"><span data-stu-id="41e81-136">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="41e81-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="41e81-137">Example</span></span>  
 <span data-ttu-id="41e81-138">V tomto příkladu <xref:System.Linq.Enumerable.Max%2A> metodu k získání objednávky s nejvyšší `TotalDue` pro každou obraťte se na ID.</span><span class="sxs-lookup"><span data-stu-id="41e81-138">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest `TotalDue` for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="41e81-139">Minimum</span><span class="sxs-lookup"><span data-stu-id="41e81-139">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="41e81-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="41e81-140">Example</span></span>  
 <span data-ttu-id="41e81-141">V tomto příkladu <xref:System.Linq.Enumerable.Min%2A> metodu k získání nejmenší celková částka.</span><span class="sxs-lookup"><span data-stu-id="41e81-141">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#minprojection_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinProjection_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#minprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="41e81-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="41e81-142">Example</span></span>  
 <span data-ttu-id="41e81-143">V tomto příkladu <xref:System.Linq.Enumerable.Min%2A> metodu k získání nejmenší dlužná pro každou obraťte se na ID.</span><span class="sxs-lookup"><span data-stu-id="41e81-143">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="41e81-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="41e81-144">Example</span></span>  
 <span data-ttu-id="41e81-145">V tomto příkladu <xref:System.Linq.Enumerable.Min%2A> metodu k získání objednávky nejmenší celkem termín pro každého kontaktu.</span><span class="sxs-lookup"><span data-stu-id="41e81-145">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="41e81-146">Součet</span><span class="sxs-lookup"><span data-stu-id="41e81-146">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="41e81-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="41e81-147">Example</span></span>  
 <span data-ttu-id="41e81-148">V tomto příkladu <xref:System.Linq.Enumerable.Sum%2A> metodu k získání celkového počtu množství objednávek v `SalesOrderDetail` tabulky.</span><span class="sxs-lookup"><span data-stu-id="41e81-148">This example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total number of order quantities in the `SalesOrderDetail` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SumProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#sumprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="41e81-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="41e81-149">Example</span></span>  
 <span data-ttu-id="41e81-150">V tomto příkladu <xref:System.Linq.Enumerable.Sum%2A> metodu k získání celkové splatnosti pro každou obraťte se na ID.</span><span class="sxs-lookup"><span data-stu-id="41e81-150">This example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="41e81-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="41e81-151">See also</span></span>

- [<span data-ttu-id="41e81-152">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="41e81-152">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="41e81-153">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="41e81-153">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [<span data-ttu-id="41e81-154">Přehled standardních operátorů dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="41e81-154">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="41e81-155">Přehled standardních operátorů dotazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41e81-155">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
