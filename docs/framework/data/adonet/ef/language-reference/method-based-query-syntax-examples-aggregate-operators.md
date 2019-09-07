---
title: 'Příklady syntaxe dotazů založených na volání metody: Agregační operátory'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0e306067-5720-4782-9719-2286570a7e47
ms.openlocfilehash: 17d3a5e221fc5f917e9e266b3af4fb844c6fd85e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397504"
---
# <a name="method-based-query-syntax-examples-aggregate-operators"></a><span data-ttu-id="9522c-102">Příklady syntaxe dotazů založených na volání metody: Agregační operátory</span><span class="sxs-lookup"><span data-stu-id="9522c-102">Method-Based Query Syntax Examples: Aggregate Operators</span></span>
<span data-ttu-id="9522c-103">Příklady <xref:System.Linq.Enumerable.Aggregate%2A>v tomto tématu ukazují, jak použít metody, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>a <xref:System.Linq.Enumerable.Sum%2A> k dotazování [modelu prodeje společnosti AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) pomocí syntaxe dotazu založená na metodě.</span><span class="sxs-lookup"><span data-stu-id="9522c-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="9522c-104">Model prodeje společnosti AdventureWorks použitý v těchto příkladech je sestaven z tabulek Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="9522c-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="9522c-105">Příklady v tomto tématu používají následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="9522c-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="average"></a><span data-ttu-id="9522c-106">Average</span><span class="sxs-lookup"><span data-stu-id="9522c-106">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="9522c-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="9522c-107">Example</span></span>  
 <span data-ttu-id="9522c-108">Následující příklad používá <xref:System.Linq.Enumerable.Average%2A> metodu k vyhledání průměrné ceny produktů v seznamu.</span><span class="sxs-lookup"><span data-stu-id="9522c-108">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average_mq)]
 [!code-vb[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average_mq)]  
  
### <a name="example"></a><span data-ttu-id="9522c-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="9522c-109">Example</span></span>  
 <span data-ttu-id="9522c-110">Následující příklad používá <xref:System.Linq.Enumerable.Average%2A> metodu k nalezení průměrné ceníkové ceny produktů každého stylu.</span><span class="sxs-lookup"><span data-stu-id="9522c-110">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="9522c-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="9522c-111">Example</span></span>  
 <span data-ttu-id="9522c-112">Následující příklad používá <xref:System.Linq.Enumerable.Average%2A> metodu k vyhledání průměrného součtu v důsledku.</span><span class="sxs-lookup"><span data-stu-id="9522c-112">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageprojection_mq)]
 [!code-vb[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="9522c-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="9522c-113">Example</span></span>  
 <span data-ttu-id="9522c-114">Následující příklad používá <xref:System.Linq.Enumerable.Average%2A> metodu k získání průměrného součtu pro každé ID kontaktu.</span><span class="sxs-lookup"><span data-stu-id="9522c-114">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="9522c-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="9522c-115">Example</span></span>  
 <span data-ttu-id="9522c-116">Následující příklad používá <xref:System.Linq.Enumerable.Average%2A> metodu k získání objednávek s průměrnou celkovou splatnou pro každý kontakt.</span><span class="sxs-lookup"><span data-stu-id="9522c-116">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the orders with the average total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="9522c-117">Count</span><span class="sxs-lookup"><span data-stu-id="9522c-117">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="9522c-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="9522c-118">Example</span></span>  
 <span data-ttu-id="9522c-119">Následující příklad používá <xref:System.Linq.Enumerable.Count%2A> metodu k vrácení počtu produktů v tabulce produktů.</span><span class="sxs-lookup"><span data-stu-id="9522c-119">The following example uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in the Product table.</span></span>  
  
 [!code-csharp[DP L2E Examples#Count](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#count)]
 [!code-vb[DP L2E Examples#Count](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#count)]  
  
### <a name="example"></a><span data-ttu-id="9522c-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="9522c-120">Example</span></span>  
 <span data-ttu-id="9522c-121">Následující příklad používá <xref:System.Linq.Enumerable.Count%2A> metodu k vrácení seznamu ID kontaktů a počtu jednotlivých objednávek.</span><span class="sxs-lookup"><span data-stu-id="9522c-121">The following example uses the <xref:System.Linq.Enumerable.Count%2A> method to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countnested)]
 [!code-vb[DP L2E Examples#CountNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="9522c-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="9522c-122">Example</span></span>  
 <span data-ttu-id="9522c-123">Následující příklad seskupuje produkty podle barev a použije <xref:System.Linq.Enumerable.Count%2A> metodu k vrácení počtu produktů v každé skupině barev.</span><span class="sxs-lookup"><span data-stu-id="9522c-123">The following example groups products by color and uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="longcount"></a><span data-ttu-id="9522c-124">LongCount</span><span class="sxs-lookup"><span data-stu-id="9522c-124">LongCount</span></span>  
  
### <a name="example"></a><span data-ttu-id="9522c-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="9522c-125">Example</span></span>  
 <span data-ttu-id="9522c-126">Následující příklad získá počet kontaktů jako dlouhé celé číslo.</span><span class="sxs-lookup"><span data-stu-id="9522c-126">The following example gets the contact count as a long integer.</span></span>  
  
 [!code-csharp[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#longcountsimple)]
 [!code-vb[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#longcountsimple)]  
  
## <a name="max"></a><span data-ttu-id="9522c-127">Maximum</span><span class="sxs-lookup"><span data-stu-id="9522c-127">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="9522c-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="9522c-128">Example</span></span>  
 <span data-ttu-id="9522c-129">Následující příklad používá <xref:System.Linq.Enumerable.Max%2A> metodu k získání největší celku v důsledku.</span><span class="sxs-lookup"><span data-stu-id="9522c-129">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxprojection_mq)]
 [!code-vb[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="9522c-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="9522c-130">Example</span></span>  
 <span data-ttu-id="9522c-131">Následující příklad používá <xref:System.Linq.Enumerable.Max%2A> metodu k získání největšího celku v důsledku ID kontaktu.</span><span class="sxs-lookup"><span data-stu-id="9522c-131">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="9522c-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="9522c-132">Example</span></span>  
 <span data-ttu-id="9522c-133">Následující příklad používá <xref:System.Linq.Enumerable.Max%2A> metodu k získání objednávek, jejichž největší celková hodnota je splatná pro každé ID kontaktu.</span><span class="sxs-lookup"><span data-stu-id="9522c-133">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="9522c-134">Minimum</span><span class="sxs-lookup"><span data-stu-id="9522c-134">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="9522c-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="9522c-135">Example</span></span>  
 <span data-ttu-id="9522c-136">Následující příklad používá <xref:System.Linq.Enumerable.Min%2A> metodu k získání nejmenšího celku z důvodu splnění.</span><span class="sxs-lookup"><span data-stu-id="9522c-136">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minprojection_mq)]
 [!code-vb[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="9522c-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="9522c-137">Example</span></span>  
 <span data-ttu-id="9522c-138">Následující příklad používá <xref:System.Linq.Enumerable.Min%2A> metodu k získání nejmenšího celku v důsledku ID kontaktu.</span><span class="sxs-lookup"><span data-stu-id="9522c-138">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="9522c-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="9522c-139">Example</span></span>  
 <span data-ttu-id="9522c-140">Následující příklad používá <xref:System.Linq.Enumerable.Min%2A> metodu k získání objednávek s nejmenším součtem v důsledku každého kontaktu.</span><span class="sxs-lookup"><span data-stu-id="9522c-140">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="9522c-141">Součet</span><span class="sxs-lookup"><span data-stu-id="9522c-141">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="9522c-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="9522c-142">Example</span></span>  
 <span data-ttu-id="9522c-143">Následující příklad používá <xref:System.Linq.Enumerable.Sum%2A> metodu k získání celkového počtu množství objednávek v tabulce SalesOrderDetail.</span><span class="sxs-lookup"><span data-stu-id="9522c-143">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total number of order quantities in the SalesOrderDetail table.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumprojection_mq)]
 [!code-vb[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="9522c-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="9522c-144">Example</span></span>  
 <span data-ttu-id="9522c-145">Následující příklad používá <xref:System.Linq.Enumerable.Sum%2A> metodu k získání celkového součtu pro každé ID kontaktu.</span><span class="sxs-lookup"><span data-stu-id="9522c-145">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="9522c-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9522c-146">See also</span></span>

- [<span data-ttu-id="9522c-147">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="9522c-147">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
