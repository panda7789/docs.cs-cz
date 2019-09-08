---
title: 'Příklady syntaxe výrazů dotazů: Agregační operátory (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 85dafa07-e102-46e7-ab78-37bf06f257a6
ms.openlocfilehash: 44e38a53823cb52040a612d4762e33283f90e1d1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794524"
---
# <a name="query-expression-syntax-examples-aggregate-operators-linq-to-dataset"></a><span data-ttu-id="f8e40-102">Příklady syntaxe výrazů dotazů: Agregační operátory (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="f8e40-102">Query Expression Syntax Examples: Aggregate Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="f8e40-103">Příklady <xref:System.Linq.Enumerable.Average%2A>v tomto tématu ukazují, jak použít metody, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>a <xref:System.Linq.Enumerable.Sum%2A> k dotazování <xref:System.Data.DataSet> a agregaci dat pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="f8e40-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query a <xref:System.Data.DataSet> and aggregate data using query expression syntax.</span></span>  
  
 <span data-ttu-id="f8e40-104">Metoda použitá v těchto příkladech je určena při [načítání dat do datové sady.](loading-data-into-a-dataset.md) `FillDataSet`</span><span class="sxs-lookup"><span data-stu-id="f8e40-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="f8e40-105">V příkladech v tomto tématu se používá tabulka Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="f8e40-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="f8e40-106">Příklady v tomto tématu používají následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="f8e40-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="f8e40-107">Další informace najdete v tématu [jak: Vytvoření projektu LINQ to DataSet v aplikaci Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="f8e40-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="average"></a><span data-ttu-id="f8e40-108">Average</span><span class="sxs-lookup"><span data-stu-id="f8e40-108">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="f8e40-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="f8e40-109">Example</span></span>  
 <span data-ttu-id="f8e40-110">Tento příklad používá <xref:System.Linq.Enumerable.Average%2A> metodu k vyhledání průměrné ceny produktů každého stylu.</span><span class="sxs-lookup"><span data-stu-id="f8e40-110">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="f8e40-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="f8e40-111">Example</span></span>  
 <span data-ttu-id="f8e40-112">Tento příklad používá <xref:System.Linq.Enumerable.Average%2A> k získání průměrného součtu z důvodu ID kontaktu.</span><span class="sxs-lookup"><span data-stu-id="f8e40-112">This example uses <xref:System.Linq.Enumerable.Average%2A> to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="f8e40-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="f8e40-113">Example</span></span>  
 <span data-ttu-id="f8e40-114">Tento příklad používá <xref:System.Linq.Enumerable.Average%2A> k získání objednávek s průměrem `TotalDue` pro každý kontakt.</span><span class="sxs-lookup"><span data-stu-id="f8e40-114">This example uses <xref:System.Linq.Enumerable.Average%2A> to get the orders with the average `TotalDue` for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="f8e40-115">Count</span><span class="sxs-lookup"><span data-stu-id="f8e40-115">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="f8e40-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="f8e40-116">Example</span></span>  
 <span data-ttu-id="f8e40-117">Tento příklad používá <xref:System.Linq.Enumerable.Count%2A> k vrácení seznamu ID kontaktů a kolik objednávek má.</span><span class="sxs-lookup"><span data-stu-id="f8e40-117">This example uses <xref:System.Linq.Enumerable.Count%2A> to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countnested)]
 [!code-vb[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="f8e40-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="f8e40-118">Example</span></span>  
 <span data-ttu-id="f8e40-119">Tento příklad seskupuje produkty podle barev a <xref:System.Linq.Enumerable.Count%2A> použije k vrácení počtu produktů v každé skupině barev.</span><span class="sxs-lookup"><span data-stu-id="f8e40-119">This example groups products by color and uses <xref:System.Linq.Enumerable.Count%2A> to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="max"></a><span data-ttu-id="f8e40-120">Maximum</span><span class="sxs-lookup"><span data-stu-id="f8e40-120">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="f8e40-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="f8e40-121">Example</span></span>  
 <span data-ttu-id="f8e40-122">Tento příklad používá <xref:System.Linq.Enumerable.Max%2A> metodu k získání největšího celku z důvodu ID kontaktu.</span><span class="sxs-lookup"><span data-stu-id="f8e40-122">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="f8e40-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="f8e40-123">Example</span></span>  
 <span data-ttu-id="f8e40-124">Tento příklad používá <xref:System.Linq.Enumerable.Max%2A> metodu k získání objednávek s největším `TotalDue` číslem pro každé ID kontaktu.</span><span class="sxs-lookup"><span data-stu-id="f8e40-124">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest `TotalDue` for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="f8e40-125">Minimum</span><span class="sxs-lookup"><span data-stu-id="f8e40-125">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="f8e40-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="f8e40-126">Example</span></span>  
 <span data-ttu-id="f8e40-127">Tento příklad používá <xref:System.Linq.Enumerable.Min%2A> metodu k získání nejmenšího celku v důsledku ID kontaktu.</span><span class="sxs-lookup"><span data-stu-id="f8e40-127">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="f8e40-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="f8e40-128">Example</span></span>  
 <span data-ttu-id="f8e40-129">Tento příklad používá <xref:System.Linq.Enumerable.Min%2A> metodu k získání objednávek s nejmenším součtem v souvislosti s každým kontaktem.</span><span class="sxs-lookup"><span data-stu-id="f8e40-129">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="f8e40-130">Součet</span><span class="sxs-lookup"><span data-stu-id="f8e40-130">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="f8e40-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="f8e40-131">Example</span></span>  
 <span data-ttu-id="f8e40-132">V tomto příkladu se <xref:System.Linq.Enumerable.Sum%2A> používá metoda pro získání celkové částky za každé ID kontaktu.</span><span class="sxs-lookup"><span data-stu-id="f8e40-132">This example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="f8e40-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f8e40-133">See also</span></span>

- [<span data-ttu-id="f8e40-134">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="f8e40-134">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="f8e40-135">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="f8e40-135">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="f8e40-136">Přehled standardních operátorů dotazůC#()</span><span class="sxs-lookup"><span data-stu-id="f8e40-136">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="f8e40-137">Přehled standardních operátorů dotazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8e40-137">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
