---
title: "Příklady syntaxe dotazů metoda: Agregační operátory (LINQ na DataSet)"
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
ms.assetid: 5ed5f01d-acb2-4dd4-be60-f04c2d570fa8
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 56188c42fabc678c2f5689f0ca09136c5556f189
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="method-based-query-syntax-examples-aggregate-operators-linq-to-dataset"></a><span data-ttu-id="898da-102">Příklady syntaxe dotazů metoda: Agregační operátory (LINQ na DataSet)</span><span class="sxs-lookup"><span data-stu-id="898da-102">Method-Based Query Syntax Examples: Aggregate Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="898da-103">V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, a <xref:System.Linq.Enumerable.Sum%2A> operátory k dotazování <xref:System.Data.DataSet> a agregace dat pomocí dotazu – metoda syntaxe.</span><span class="sxs-lookup"><span data-stu-id="898da-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> operators to query a <xref:System.Data.DataSet> and aggregate data using method query syntax.</span></span>  
  
 <span data-ttu-id="898da-104">`FillDataSet` Metodu použitou v těchto příkladech je uveden v [načítání dat do datové sady](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="898da-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="898da-105">V příkladech v tomto tématu použijte kontaktu, adresu, produktu, SalesOrderHeader a podrobnosti prodejní objednávky tabulky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="898da-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="898da-106">V příkladech v tomto tématu použijte následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="898da-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="898da-107">Další informace najdete v tématu [postupy: vytvoření LINQ na DataSet projekt v sadě Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="898da-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="aggregate"></a><span data-ttu-id="898da-108">Aggregate</span><span class="sxs-lookup"><span data-stu-id="898da-108">Aggregate</span></span>  
  
### <a name="example"></a><span data-ttu-id="898da-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="898da-109">Example</span></span>  
 <span data-ttu-id="898da-110">Tento příklad používá <xref:System.Linq.Enumerable.Aggregate%2A> metoda získat prvních 5 kontakty ze `Contact` tabulky a sestavení čárkami oddělený seznam názvů poslední.</span><span class="sxs-lookup"><span data-stu-id="898da-110">This example uses the <xref:System.Linq.Enumerable.Aggregate%2A> method to get the first 5 contacts from the `Contact` table and build a comma-delimited list of the last names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Aggregate_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#aggregate_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Aggregate_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#aggregate_mq)]  
  
## <a name="average"></a><span data-ttu-id="898da-111">Průměr</span><span class="sxs-lookup"><span data-stu-id="898da-111">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="898da-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="898da-112">Example</span></span>  
 <span data-ttu-id="898da-113">Tento příklad používá <xref:System.Linq.Enumerable.Average%2A> metody k vyhledání průměrná cena seznam produktů.</span><span class="sxs-lookup"><span data-stu-id="898da-113">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Average_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#average_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Average_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#average_mq)]  
  
### <a name="example"></a><span data-ttu-id="898da-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="898da-114">Example</span></span>  
 <span data-ttu-id="898da-115">Tento příklad používá <xref:System.Linq.Enumerable.Average%2A> metody k vyhledání průměrná cena seznam produktů jednotlivých stylů.</span><span class="sxs-lookup"><span data-stu-id="898da-115">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="898da-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="898da-116">Example</span></span>  
 <span data-ttu-id="898da-117">Tento příklad používá <xref:System.Linq.Enumerable.Average%2A> metody k vyhledání celkový kvůli průměr.</span><span class="sxs-lookup"><span data-stu-id="898da-117">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average total due.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averageprojection_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageProjection_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averageprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="898da-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="898da-118">Example</span></span>  
 <span data-ttu-id="898da-119">Tento příklad používá <xref:System.Linq.Enumerable.Average%2A> ID metoda získat průměr celkové potřebné pro každý kontakt.</span><span class="sxs-lookup"><span data-stu-id="898da-119">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="898da-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="898da-120">Example</span></span>  
 <span data-ttu-id="898da-121">Tento příklad používá <xref:System.Linq.Enumerable.Average%2A> metoda získat příkazy se průměr `TotalDue` pro každý kontakt.</span><span class="sxs-lookup"><span data-stu-id="898da-121">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the orders with the average `TotalDue` for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="898da-122">Počet</span><span class="sxs-lookup"><span data-stu-id="898da-122">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="898da-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="898da-123">Example</span></span>  
 <span data-ttu-id="898da-124">Tento příklad používá <xref:System.Linq.Enumerable.Count%2A> metody, která vrátí počet produktů `Product` tabulky.</span><span class="sxs-lookup"><span data-stu-id="898da-124">This example uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in the `Product` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Count](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#count)]
 [!code-vb[DP LINQ to DataSet Examples#Count](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#count)]  
  
### <a name="example"></a><span data-ttu-id="898da-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="898da-125">Example</span></span>  
 <span data-ttu-id="898da-126">Tento příklad používá <xref:System.Linq.Enumerable.Count%2A> metoda vrátí seznam obraťte se na ID a kolik řadí každý má.</span><span class="sxs-lookup"><span data-stu-id="898da-126">This example uses the <xref:System.Linq.Enumerable.Count%2A> method to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countnested)]
 [!code-vb[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="898da-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="898da-127">Example</span></span>  
 <span data-ttu-id="898da-128">Tento příklad skupiny produkty pomocí barev a používá <xref:System.Linq.Enumerable.Count%2A> metody, která vrátí počet produktů v každé skupině barev.</span><span class="sxs-lookup"><span data-stu-id="898da-128">This example groups products by color and uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="longcount"></a><span data-ttu-id="898da-129">LongCount</span><span class="sxs-lookup"><span data-stu-id="898da-129">LongCount</span></span>  
  
### <a name="example"></a><span data-ttu-id="898da-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="898da-130">Example</span></span>  
 <span data-ttu-id="898da-131">Tento příklad získá kontaktní počet jako dlouhých celých čísel.</span><span class="sxs-lookup"><span data-stu-id="898da-131">This example gets the contact count as a long integer.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#LongCountSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#longcountsimple)]
 [!code-vb[DP LINQ to DataSet Examples#LongCountSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#longcountsimple)]  
  
## <a name="max"></a><span data-ttu-id="898da-132">Max</span><span class="sxs-lookup"><span data-stu-id="898da-132">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="898da-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="898da-133">Example</span></span>  
 <span data-ttu-id="898da-134">Tento příklad používá <xref:System.Linq.Enumerable.Max%2A> metoda získat největší celkový splatnosti.</span><span class="sxs-lookup"><span data-stu-id="898da-134">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxprojection_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxProjection_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="898da-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="898da-135">Example</span></span>  
 <span data-ttu-id="898da-136">Tento příklad používá <xref:System.Linq.Enumerable.Max%2A> metoda získat největší celkový splatnosti pro každou obraťte se na ID.</span><span class="sxs-lookup"><span data-stu-id="898da-136">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="898da-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="898da-137">Example</span></span>  
 <span data-ttu-id="898da-138">Tento příklad používá <xref:System.Linq.Enumerable.Max%2A> metoda získat objednávky s nejvyšší `TotalDue` pro každou obraťte se na ID.</span><span class="sxs-lookup"><span data-stu-id="898da-138">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest `TotalDue` for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="898da-139">Min.</span><span class="sxs-lookup"><span data-stu-id="898da-139">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="898da-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="898da-140">Example</span></span>  
 <span data-ttu-id="898da-141">Tento příklad používá <xref:System.Linq.Enumerable.Min%2A> metoda získat nejmenší celkový splatnosti.</span><span class="sxs-lookup"><span data-stu-id="898da-141">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#minprojection_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinProjection_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#minprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="898da-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="898da-142">Example</span></span>  
 <span data-ttu-id="898da-143">Tento příklad používá <xref:System.Linq.Enumerable.Min%2A> metoda získat nejmenší celkový splatnosti pro každou obraťte se na ID.</span><span class="sxs-lookup"><span data-stu-id="898da-143">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="898da-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="898da-144">Example</span></span>  
 <span data-ttu-id="898da-145">Tento příklad používá <xref:System.Linq.Enumerable.Min%2A> metoda získat příkazy se nejmenší celkem platnosti pro každý kontakt.</span><span class="sxs-lookup"><span data-stu-id="898da-145">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="898da-146">Součet</span><span class="sxs-lookup"><span data-stu-id="898da-146">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="898da-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="898da-147">Example</span></span>  
 <span data-ttu-id="898da-148">Tento příklad používá <xref:System.Linq.Enumerable.Sum%2A> metoda získat celkový počet počty pořadí v `SalesOrderDetail` tabulky.</span><span class="sxs-lookup"><span data-stu-id="898da-148">This example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total number of order quantities in the `SalesOrderDetail` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SumProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#sumprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="898da-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="898da-149">Example</span></span>  
 <span data-ttu-id="898da-150">Tento příklad používá <xref:System.Linq.Enumerable.Sum%2A> metoda získat celkový splatnosti pro každou obraťte se na ID.</span><span class="sxs-lookup"><span data-stu-id="898da-150">This example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="898da-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="898da-151">See Also</span></span>  
 [<span data-ttu-id="898da-152">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="898da-152">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="898da-153">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="898da-153">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="898da-154">Přehled standardních operátorů dotazu</span><span class="sxs-lookup"><span data-stu-id="898da-154">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
