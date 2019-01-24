---
title: 'Příklady syntaxe dotazů založených na volání metody: Agregační operátory (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5ed5f01d-acb2-4dd4-be60-f04c2d570fa8
ms.openlocfilehash: 2119d272c3e0bf934318dcf8c0292854d014d271
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54497407"
---
# <a name="method-based-query-syntax-examples-aggregate-operators-linq-to-dataset"></a><span data-ttu-id="0230f-102">Příklady syntaxe dotazů založených na volání metody: Agregační operátory (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="0230f-102">Method-Based Query Syntax Examples: Aggregate Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="0230f-103">Příklady v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, a <xref:System.Linq.Enumerable.Sum%2A> operátory pro dotazování <xref:System.Data.DataSet> a agregace dat pomocí dotazů – metoda syntaxe.</span><span class="sxs-lookup"><span data-stu-id="0230f-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> operators to query a <xref:System.Data.DataSet> and aggregate data using method query syntax.</span></span>  
  
 <span data-ttu-id="0230f-104">`FillDataSet` Metodu použitou v těchto příkladech je zadán v [načítání dat do datová sada](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="0230f-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="0230f-105">Příklady v tomto tématu použijte tabulky Kontakt, adresa, produktu, SalesOrderHeader a podrobnosti prodejní objednávky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="0230f-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="0230f-106">V příkladech v tomto tématu se používá následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="0230f-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="0230f-107">Další informace najdete v tématu [jak: Vytvoření LINQ to DataSet projektu v sadě Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="0230f-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="aggregate"></a><span data-ttu-id="0230f-108">Aggregate</span><span class="sxs-lookup"><span data-stu-id="0230f-108">Aggregate</span></span>  
  
### <a name="example"></a><span data-ttu-id="0230f-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="0230f-109">Example</span></span>  
 <span data-ttu-id="0230f-110">V tomto příkladu <xref:System.Linq.Enumerable.Aggregate%2A> metodu k získání prvních 5 kontakty z `Contact` tabulky a sestavte seznam oddělený čárkami příjmení.</span><span class="sxs-lookup"><span data-stu-id="0230f-110">This example uses the <xref:System.Linq.Enumerable.Aggregate%2A> method to get the first 5 contacts from the `Contact` table and build a comma-delimited list of the last names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Aggregate_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#aggregate_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Aggregate_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#aggregate_mq)]  
  
## <a name="average"></a><span data-ttu-id="0230f-111">Průměr</span><span class="sxs-lookup"><span data-stu-id="0230f-111">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="0230f-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="0230f-112">Example</span></span>  
 <span data-ttu-id="0230f-113">V tomto příkladu <xref:System.Linq.Enumerable.Average%2A> metody k vyhledání průměrná cena seznamu produktů.</span><span class="sxs-lookup"><span data-stu-id="0230f-113">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Average_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#average_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Average_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#average_mq)]  
  
### <a name="example"></a><span data-ttu-id="0230f-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="0230f-114">Example</span></span>  
 <span data-ttu-id="0230f-115">V tomto příkladu <xref:System.Linq.Enumerable.Average%2A> metody k vyhledání průměrná cena seznam produktů jednotlivých stylů.</span><span class="sxs-lookup"><span data-stu-id="0230f-115">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="0230f-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="0230f-116">Example</span></span>  
 <span data-ttu-id="0230f-117">V tomto příkladu <xref:System.Linq.Enumerable.Average%2A> metody k vyhledání průměrné celkové potřebné.</span><span class="sxs-lookup"><span data-stu-id="0230f-117">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average total due.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averageprojection_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageProjection_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averageprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="0230f-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="0230f-118">Example</span></span>  
 <span data-ttu-id="0230f-119">V tomto příkladu <xref:System.Linq.Enumerable.Average%2A> ID metodu k získání celkové potřebné průměr pro každého kontaktu.</span><span class="sxs-lookup"><span data-stu-id="0230f-119">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="0230f-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="0230f-120">Example</span></span>  
 <span data-ttu-id="0230f-121">V tomto příkladu <xref:System.Linq.Enumerable.Average%2A> metodu k získání objednávky s průměrem `TotalDue` každého kontaktu.</span><span class="sxs-lookup"><span data-stu-id="0230f-121">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the orders with the average `TotalDue` for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="0230f-122">Počet</span><span class="sxs-lookup"><span data-stu-id="0230f-122">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="0230f-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="0230f-123">Example</span></span>  
 <span data-ttu-id="0230f-124">V tomto příkladu <xref:System.Linq.Enumerable.Count%2A> metody, která vrátí počet produktů `Product` tabulky.</span><span class="sxs-lookup"><span data-stu-id="0230f-124">This example uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in the `Product` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Count](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#count)]
 [!code-vb[DP LINQ to DataSet Examples#Count](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#count)]  
  
### <a name="example"></a><span data-ttu-id="0230f-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="0230f-125">Example</span></span>  
 <span data-ttu-id="0230f-126">V tomto příkladu <xref:System.Linq.Enumerable.Count%2A> metoda vrátí seznam ID kontaktu a kolik objednávky, každá má.</span><span class="sxs-lookup"><span data-stu-id="0230f-126">This example uses the <xref:System.Linq.Enumerable.Count%2A> method to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countnested)]
 [!code-vb[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="0230f-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="0230f-127">Example</span></span>  
 <span data-ttu-id="0230f-128">Tento příklad skupiny produktů pomocí barev a používá <xref:System.Linq.Enumerable.Count%2A> metody, která vrátí počet produktů v každé skupině barvu.</span><span class="sxs-lookup"><span data-stu-id="0230f-128">This example groups products by color and uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="longcount"></a><span data-ttu-id="0230f-129">LongCount</span><span class="sxs-lookup"><span data-stu-id="0230f-129">LongCount</span></span>  
  
### <a name="example"></a><span data-ttu-id="0230f-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="0230f-130">Example</span></span>  
 <span data-ttu-id="0230f-131">V tomto příkladu získá kontaktní počet jako dlouhé celé číslo.</span><span class="sxs-lookup"><span data-stu-id="0230f-131">This example gets the contact count as a long integer.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#LongCountSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#longcountsimple)]
 [!code-vb[DP LINQ to DataSet Examples#LongCountSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#longcountsimple)]  
  
## <a name="max"></a><span data-ttu-id="0230f-132">Maximum</span><span class="sxs-lookup"><span data-stu-id="0230f-132">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="0230f-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="0230f-133">Example</span></span>  
 <span data-ttu-id="0230f-134">V tomto příkladu <xref:System.Linq.Enumerable.Max%2A> metodu k získání největší celková částka.</span><span class="sxs-lookup"><span data-stu-id="0230f-134">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxprojection_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxProjection_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="0230f-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="0230f-135">Example</span></span>  
 <span data-ttu-id="0230f-136">V tomto příkladu <xref:System.Linq.Enumerable.Max%2A> metodu k získání největší dlužná pro každou obraťte se na ID.</span><span class="sxs-lookup"><span data-stu-id="0230f-136">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="0230f-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="0230f-137">Example</span></span>  
 <span data-ttu-id="0230f-138">V tomto příkladu <xref:System.Linq.Enumerable.Max%2A> metodu k získání objednávky s nejvyšší `TotalDue` pro každou obraťte se na ID.</span><span class="sxs-lookup"><span data-stu-id="0230f-138">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest `TotalDue` for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="0230f-139">Minimum</span><span class="sxs-lookup"><span data-stu-id="0230f-139">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="0230f-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="0230f-140">Example</span></span>  
 <span data-ttu-id="0230f-141">V tomto příkladu <xref:System.Linq.Enumerable.Min%2A> metodu k získání nejmenší celková částka.</span><span class="sxs-lookup"><span data-stu-id="0230f-141">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#minprojection_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinProjection_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#minprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="0230f-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="0230f-142">Example</span></span>  
 <span data-ttu-id="0230f-143">V tomto příkladu <xref:System.Linq.Enumerable.Min%2A> metodu k získání nejmenší dlužná pro každou obraťte se na ID.</span><span class="sxs-lookup"><span data-stu-id="0230f-143">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="0230f-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="0230f-144">Example</span></span>  
 <span data-ttu-id="0230f-145">V tomto příkladu <xref:System.Linq.Enumerable.Min%2A> metodu k získání objednávky nejmenší celkem termín pro každého kontaktu.</span><span class="sxs-lookup"><span data-stu-id="0230f-145">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="0230f-146">Součet</span><span class="sxs-lookup"><span data-stu-id="0230f-146">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="0230f-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="0230f-147">Example</span></span>  
 <span data-ttu-id="0230f-148">V tomto příkladu <xref:System.Linq.Enumerable.Sum%2A> metodu k získání celkového počtu množství objednávek v `SalesOrderDetail` tabulky.</span><span class="sxs-lookup"><span data-stu-id="0230f-148">This example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total number of order quantities in the `SalesOrderDetail` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SumProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#sumprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="0230f-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="0230f-149">Example</span></span>  
 <span data-ttu-id="0230f-150">V tomto příkladu <xref:System.Linq.Enumerable.Sum%2A> metodu k získání celkové splatnosti pro každou obraťte se na ID.</span><span class="sxs-lookup"><span data-stu-id="0230f-150">This example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="0230f-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0230f-151">See also</span></span>
- [<span data-ttu-id="0230f-152">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="0230f-152">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="0230f-153">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="0230f-153">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [<span data-ttu-id="0230f-154">Přehled standardních operátorů dotazu</span><span class="sxs-lookup"><span data-stu-id="0230f-154">Standard Query Operators Overview</span></span>](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
