---
title: 'Příklady syntaxe dotazů založených na volání metody: Agregační operátory'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0e306067-5720-4782-9719-2286570a7e47
ms.openlocfilehash: d9007e4d650c79a636f908a638bb382457f6b29b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250268"
---
# <a name="method-based-query-syntax-examples-aggregate-operators"></a><span data-ttu-id="1d2eb-102">Příklady syntaxe dotazů založených na volání metody: Agregační operátory</span><span class="sxs-lookup"><span data-stu-id="1d2eb-102">Method-Based Query Syntax Examples: Aggregate Operators</span></span>
<span data-ttu-id="1d2eb-103">Příklady <xref:System.Linq.Enumerable.Aggregate%2A>v tomto tématu ukazují, jak použít metody, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>a <xref:System.Linq.Enumerable.Sum%2A> k dotazování [modelu prodeje společnosti AdventureWorks](https://archive.codeplex.com/?p=msftdbprodsamples) pomocí syntaxe dotazu založená na metodě.</span><span class="sxs-lookup"><span data-stu-id="1d2eb-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using method-based query syntax.</span></span> <span data-ttu-id="1d2eb-104">Model prodeje společnosti AdventureWorks použitý v těchto příkladech je sestaven z tabulek Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="1d2eb-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="1d2eb-105">Příklady v tomto tématu používají následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="1d2eb-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="average"></a><span data-ttu-id="1d2eb-106">Average</span><span class="sxs-lookup"><span data-stu-id="1d2eb-106">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="1d2eb-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d2eb-107">Example</span></span>  
 <span data-ttu-id="1d2eb-108">Následující příklad používá <xref:System.Linq.Enumerable.Average%2A> metodu k vyhledání průměrné ceny produktů v seznamu.</span><span class="sxs-lookup"><span data-stu-id="1d2eb-108">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average_mq)]
 [!code-vb[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average_mq)]  
  
### <a name="example"></a><span data-ttu-id="1d2eb-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d2eb-109">Example</span></span>  
 <span data-ttu-id="1d2eb-110">Následující příklad používá <xref:System.Linq.Enumerable.Average%2A> metodu k nalezení průměrné ceníkové ceny produktů každého stylu.</span><span class="sxs-lookup"><span data-stu-id="1d2eb-110">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="1d2eb-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d2eb-111">Example</span></span>  
 <span data-ttu-id="1d2eb-112">Následující příklad používá <xref:System.Linq.Enumerable.Average%2A> metodu k vyhledání průměrného součtu v důsledku.</span><span class="sxs-lookup"><span data-stu-id="1d2eb-112">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageprojection_mq)]
 [!code-vb[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="1d2eb-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d2eb-113">Example</span></span>  
 <span data-ttu-id="1d2eb-114">Následující příklad používá <xref:System.Linq.Enumerable.Average%2A> metodu k získání průměrného součtu pro každé ID kontaktu.</span><span class="sxs-lookup"><span data-stu-id="1d2eb-114">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="1d2eb-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d2eb-115">Example</span></span>  
 <span data-ttu-id="1d2eb-116">Následující příklad používá <xref:System.Linq.Enumerable.Average%2A> metodu k získání objednávek s průměrnou celkovou splatnou pro každý kontakt.</span><span class="sxs-lookup"><span data-stu-id="1d2eb-116">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the orders with the average total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="1d2eb-117">Count</span><span class="sxs-lookup"><span data-stu-id="1d2eb-117">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="1d2eb-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d2eb-118">Example</span></span>  
 <span data-ttu-id="1d2eb-119">Následující příklad používá <xref:System.Linq.Enumerable.Count%2A> metodu k vrácení počtu produktů v tabulce produktů.</span><span class="sxs-lookup"><span data-stu-id="1d2eb-119">The following example uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in the Product table.</span></span>  
  
 [!code-csharp[DP L2E Examples#Count](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#count)]
 [!code-vb[DP L2E Examples#Count](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#count)]  
  
### <a name="example"></a><span data-ttu-id="1d2eb-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d2eb-120">Example</span></span>  
 <span data-ttu-id="1d2eb-121">Následující příklad používá <xref:System.Linq.Enumerable.Count%2A> metodu k vrácení seznamu ID kontaktů a počtu jednotlivých objednávek.</span><span class="sxs-lookup"><span data-stu-id="1d2eb-121">The following example uses the <xref:System.Linq.Enumerable.Count%2A> method to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countnested)]
 [!code-vb[DP L2E Examples#CountNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="1d2eb-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d2eb-122">Example</span></span>  
 <span data-ttu-id="1d2eb-123">Následující příklad seskupuje produkty podle barev a použije <xref:System.Linq.Enumerable.Count%2A> metodu k vrácení počtu produktů v každé skupině barev.</span><span class="sxs-lookup"><span data-stu-id="1d2eb-123">The following example groups products by color and uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="longcount"></a><span data-ttu-id="1d2eb-124">LongCount</span><span class="sxs-lookup"><span data-stu-id="1d2eb-124">LongCount</span></span>  
  
### <a name="example"></a><span data-ttu-id="1d2eb-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d2eb-125">Example</span></span>  
 <span data-ttu-id="1d2eb-126">Následující příklad získá počet kontaktů jako dlouhé celé číslo.</span><span class="sxs-lookup"><span data-stu-id="1d2eb-126">The following example gets the contact count as a long integer.</span></span>  
  
 [!code-csharp[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#longcountsimple)]
 [!code-vb[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#longcountsimple)]  
  
## <a name="max"></a><span data-ttu-id="1d2eb-127">Maximum</span><span class="sxs-lookup"><span data-stu-id="1d2eb-127">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="1d2eb-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d2eb-128">Example</span></span>  
 <span data-ttu-id="1d2eb-129">Následující příklad používá <xref:System.Linq.Enumerable.Max%2A> metodu k získání největší celku v důsledku.</span><span class="sxs-lookup"><span data-stu-id="1d2eb-129">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxprojection_mq)]
 [!code-vb[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="1d2eb-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d2eb-130">Example</span></span>  
 <span data-ttu-id="1d2eb-131">Následující příklad používá <xref:System.Linq.Enumerable.Max%2A> metodu k získání největšího celku v důsledku ID kontaktu.</span><span class="sxs-lookup"><span data-stu-id="1d2eb-131">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="1d2eb-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d2eb-132">Example</span></span>  
 <span data-ttu-id="1d2eb-133">Následující příklad používá <xref:System.Linq.Enumerable.Max%2A> metodu k získání objednávek, jejichž největší celková hodnota je splatná pro každé ID kontaktu.</span><span class="sxs-lookup"><span data-stu-id="1d2eb-133">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="1d2eb-134">Minimum</span><span class="sxs-lookup"><span data-stu-id="1d2eb-134">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="1d2eb-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d2eb-135">Example</span></span>  
 <span data-ttu-id="1d2eb-136">Následující příklad používá <xref:System.Linq.Enumerable.Min%2A> metodu k získání nejmenšího celku z důvodu splnění.</span><span class="sxs-lookup"><span data-stu-id="1d2eb-136">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minprojection_mq)]
 [!code-vb[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="1d2eb-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d2eb-137">Example</span></span>  
 <span data-ttu-id="1d2eb-138">Následující příklad používá <xref:System.Linq.Enumerable.Min%2A> metodu k získání nejmenšího celku v důsledku ID kontaktu.</span><span class="sxs-lookup"><span data-stu-id="1d2eb-138">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="1d2eb-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d2eb-139">Example</span></span>  
 <span data-ttu-id="1d2eb-140">Následující příklad používá <xref:System.Linq.Enumerable.Min%2A> metodu k získání objednávek s nejmenším součtem v důsledku každého kontaktu.</span><span class="sxs-lookup"><span data-stu-id="1d2eb-140">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="1d2eb-141">Součet</span><span class="sxs-lookup"><span data-stu-id="1d2eb-141">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="1d2eb-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d2eb-142">Example</span></span>  
 <span data-ttu-id="1d2eb-143">Následující příklad používá <xref:System.Linq.Enumerable.Sum%2A> metodu k získání celkového počtu množství objednávek v tabulce SalesOrderDetail.</span><span class="sxs-lookup"><span data-stu-id="1d2eb-143">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total number of order quantities in the SalesOrderDetail table.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumprojection_mq)]
 [!code-vb[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="1d2eb-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d2eb-144">Example</span></span>  
 <span data-ttu-id="1d2eb-145">Následující příklad používá <xref:System.Linq.Enumerable.Sum%2A> metodu k získání celkového součtu pro každé ID kontaktu.</span><span class="sxs-lookup"><span data-stu-id="1d2eb-145">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="1d2eb-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1d2eb-146">See also</span></span>

- [<span data-ttu-id="1d2eb-147">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="1d2eb-147">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
