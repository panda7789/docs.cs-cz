---
title: 'Příklady syntaxe dotazů založených na volání metody: Agregační operátory (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5ed5f01d-acb2-4dd4-be60-f04c2d570fa8
ms.openlocfilehash: 348070663e414f2768b6b57d880c41d4da6c7bb2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794930"
---
# <a name="method-based-query-syntax-examples-aggregate-operators-linq-to-dataset"></a><span data-ttu-id="b0bd7-102">Příklady syntaxe dotazů založených na volání metody: Agregační operátory (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="b0bd7-102">Method-Based Query Syntax Examples: Aggregate Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="b0bd7-103">Příklady v tomto <xref:System.Linq.Enumerable.Aggregate%2A>tématu ukazují, jak použít <xref:System.Linq.Enumerable.Sum%2A> operátory, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>a k dotazování <xref:System.Data.DataSet> a agregačních dat pomocí dotazu metody syntaktick.</span><span class="sxs-lookup"><span data-stu-id="b0bd7-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> operators to query a <xref:System.Data.DataSet> and aggregate data using method query syntax.</span></span>  
  
 <span data-ttu-id="b0bd7-104">Metoda použitá v těchto příkladech je určena při [načítání dat do datové sady.](loading-data-into-a-dataset.md) `FillDataSet`</span><span class="sxs-lookup"><span data-stu-id="b0bd7-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="b0bd7-105">V příkladech v tomto tématu se používá tabulka Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="b0bd7-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="b0bd7-106">Příklady v tomto tématu používají následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="b0bd7-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="b0bd7-107">Další informace najdete v tématu [jak: Vytvoření projektu LINQ to DataSet v aplikaci Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="b0bd7-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="aggregate"></a><span data-ttu-id="b0bd7-108">Aggregate</span><span class="sxs-lookup"><span data-stu-id="b0bd7-108">Aggregate</span></span>  
  
### <a name="example"></a><span data-ttu-id="b0bd7-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0bd7-109">Example</span></span>  
 <span data-ttu-id="b0bd7-110">Tento příklad používá <xref:System.Linq.Enumerable.Aggregate%2A> metodu k získání prvních 5 kontaktů `Contact` z tabulky a sestavení seznamu příjmení oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="b0bd7-110">This example uses the <xref:System.Linq.Enumerable.Aggregate%2A> method to get the first 5 contacts from the `Contact` table and build a comma-delimited list of the last names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Aggregate_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#aggregate_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Aggregate_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#aggregate_mq)]  
  
## <a name="average"></a><span data-ttu-id="b0bd7-111">Average</span><span class="sxs-lookup"><span data-stu-id="b0bd7-111">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="b0bd7-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0bd7-112">Example</span></span>  
 <span data-ttu-id="b0bd7-113">Tento příklad používá <xref:System.Linq.Enumerable.Average%2A> metodu k vyhledání průměrné ceny produktů v seznamu.</span><span class="sxs-lookup"><span data-stu-id="b0bd7-113">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Average_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#average_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Average_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#average_mq)]  
  
### <a name="example"></a><span data-ttu-id="b0bd7-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0bd7-114">Example</span></span>  
 <span data-ttu-id="b0bd7-115">Tento příklad používá <xref:System.Linq.Enumerable.Average%2A> metodu k vyhledání průměrné ceny produktů každého stylu.</span><span class="sxs-lookup"><span data-stu-id="b0bd7-115">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="b0bd7-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0bd7-116">Example</span></span>  
 <span data-ttu-id="b0bd7-117">V tomto příkladu se <xref:System.Linq.Enumerable.Average%2A> používá metoda k nalezení průměrného celku v důsledku.</span><span class="sxs-lookup"><span data-stu-id="b0bd7-117">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average total due.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averageprojection_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageProjection_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averageprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="b0bd7-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0bd7-118">Example</span></span>  
 <span data-ttu-id="b0bd7-119">Tento příklad používá <xref:System.Linq.Enumerable.Average%2A> metodu k získání průměrného součtu pro každé ID kontaktu.</span><span class="sxs-lookup"><span data-stu-id="b0bd7-119">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="b0bd7-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0bd7-120">Example</span></span>  
 <span data-ttu-id="b0bd7-121">Tento příklad používá <xref:System.Linq.Enumerable.Average%2A> metodu k získání objednávek s průměrem `TotalDue` pro každý kontakt.</span><span class="sxs-lookup"><span data-stu-id="b0bd7-121">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the orders with the average `TotalDue` for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="b0bd7-122">Count</span><span class="sxs-lookup"><span data-stu-id="b0bd7-122">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="b0bd7-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0bd7-123">Example</span></span>  
 <span data-ttu-id="b0bd7-124">V tomto příkladu je <xref:System.Linq.Enumerable.Count%2A> použita metoda, která vrátí počet produktů `Product` v tabulce.</span><span class="sxs-lookup"><span data-stu-id="b0bd7-124">This example uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in the `Product` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Count](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#count)]
 [!code-vb[DP LINQ to DataSet Examples#Count](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#count)]  
  
### <a name="example"></a><span data-ttu-id="b0bd7-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0bd7-125">Example</span></span>  
 <span data-ttu-id="b0bd7-126">V tomto příkladu se <xref:System.Linq.Enumerable.Count%2A> používá metoda, která vrátí seznam ID kontaktů a počet jednotlivých objednávek.</span><span class="sxs-lookup"><span data-stu-id="b0bd7-126">This example uses the <xref:System.Linq.Enumerable.Count%2A> method to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countnested)]
 [!code-vb[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="b0bd7-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0bd7-127">Example</span></span>  
 <span data-ttu-id="b0bd7-128">Tento příklad seskupuje produkty podle barev a pomocí <xref:System.Linq.Enumerable.Count%2A> metody vrátí počet produktů v každé skupině barev.</span><span class="sxs-lookup"><span data-stu-id="b0bd7-128">This example groups products by color and uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="longcount"></a><span data-ttu-id="b0bd7-129">LongCount</span><span class="sxs-lookup"><span data-stu-id="b0bd7-129">LongCount</span></span>  
  
### <a name="example"></a><span data-ttu-id="b0bd7-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0bd7-130">Example</span></span>  
 <span data-ttu-id="b0bd7-131">Tento příklad získá počet kontaktů jako dlouhé celé číslo.</span><span class="sxs-lookup"><span data-stu-id="b0bd7-131">This example gets the contact count as a long integer.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#LongCountSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#longcountsimple)]
 [!code-vb[DP LINQ to DataSet Examples#LongCountSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#longcountsimple)]  
  
## <a name="max"></a><span data-ttu-id="b0bd7-132">Maximum</span><span class="sxs-lookup"><span data-stu-id="b0bd7-132">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="b0bd7-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0bd7-133">Example</span></span>  
 <span data-ttu-id="b0bd7-134">Tento příklad používá <xref:System.Linq.Enumerable.Max%2A> metodu k získání největšího celku z důvodu splnění.</span><span class="sxs-lookup"><span data-stu-id="b0bd7-134">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxprojection_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxProjection_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="b0bd7-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0bd7-135">Example</span></span>  
 <span data-ttu-id="b0bd7-136">Tento příklad používá <xref:System.Linq.Enumerable.Max%2A> metodu k získání největšího celku z důvodu ID kontaktu.</span><span class="sxs-lookup"><span data-stu-id="b0bd7-136">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="b0bd7-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0bd7-137">Example</span></span>  
 <span data-ttu-id="b0bd7-138">Tento příklad používá <xref:System.Linq.Enumerable.Max%2A> metodu k získání objednávek s největším `TotalDue` číslem pro každé ID kontaktu.</span><span class="sxs-lookup"><span data-stu-id="b0bd7-138">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest `TotalDue` for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="b0bd7-139">Minimum</span><span class="sxs-lookup"><span data-stu-id="b0bd7-139">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="b0bd7-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0bd7-140">Example</span></span>  
 <span data-ttu-id="b0bd7-141">Tento příklad používá <xref:System.Linq.Enumerable.Min%2A> metodu k získání nejmenšího celku z důvodu splnění.</span><span class="sxs-lookup"><span data-stu-id="b0bd7-141">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#minprojection_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinProjection_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#minprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="b0bd7-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0bd7-142">Example</span></span>  
 <span data-ttu-id="b0bd7-143">Tento příklad používá <xref:System.Linq.Enumerable.Min%2A> metodu k získání nejmenšího celku v důsledku ID kontaktu.</span><span class="sxs-lookup"><span data-stu-id="b0bd7-143">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="b0bd7-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0bd7-144">Example</span></span>  
 <span data-ttu-id="b0bd7-145">Tento příklad používá <xref:System.Linq.Enumerable.Min%2A> metodu k získání objednávek s nejmenším součtem v souvislosti s každým kontaktem.</span><span class="sxs-lookup"><span data-stu-id="b0bd7-145">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="b0bd7-146">Součet</span><span class="sxs-lookup"><span data-stu-id="b0bd7-146">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="b0bd7-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0bd7-147">Example</span></span>  
 <span data-ttu-id="b0bd7-148">Tento příklad používá <xref:System.Linq.Enumerable.Sum%2A> metodu k získání celkového počtu množství objednávek `SalesOrderDetail` v tabulce.</span><span class="sxs-lookup"><span data-stu-id="b0bd7-148">This example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total number of order quantities in the `SalesOrderDetail` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SumProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#sumprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="b0bd7-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0bd7-149">Example</span></span>  
 <span data-ttu-id="b0bd7-150">V tomto příkladu se <xref:System.Linq.Enumerable.Sum%2A> používá metoda pro získání celkové částky za každé ID kontaktu.</span><span class="sxs-lookup"><span data-stu-id="b0bd7-150">This example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="b0bd7-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b0bd7-151">See also</span></span>

- [<span data-ttu-id="b0bd7-152">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="b0bd7-152">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="b0bd7-153">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="b0bd7-153">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="b0bd7-154">Přehled standardních operátorů dotazůC#()</span><span class="sxs-lookup"><span data-stu-id="b0bd7-154">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="b0bd7-155">Přehled standardních operátorů dotazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0bd7-155">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
