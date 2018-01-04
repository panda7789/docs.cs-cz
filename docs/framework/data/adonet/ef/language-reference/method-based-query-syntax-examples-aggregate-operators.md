---
title: "Příklady syntaxe dotazu na základě metod: Agregační operátory"
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
ms.assetid: 0e306067-5720-4782-9719-2286570a7e47
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e965720f7952715b7fec648c794dd8a0b8b9cd1e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="method-based-query-syntax-examples-aggregate-operators"></a><span data-ttu-id="f3f1c-102">Příklady syntaxe dotazu na základě metod: Agregační operátory</span><span class="sxs-lookup"><span data-stu-id="f3f1c-102">Method-Based Query Syntax Examples: Aggregate Operators</span></span>
<span data-ttu-id="f3f1c-103">V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, a <xref:System.Linq.Enumerable.Sum%2A> metody k dotazování [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) pomocí syntaxe dotazu na základě metod.</span><span class="sxs-lookup"><span data-stu-id="f3f1c-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="f3f1c-104">Model prodeje společnosti AdventureWorks použít v těchto příkladech je sestaven z kontaktu, adresu, produktu, SalesOrderHeader a podrobnosti prodejní objednávky tabulky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="f3f1c-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="f3f1c-105">V příkladech v tomto tématu použijte následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="f3f1c-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="average"></a><span data-ttu-id="f3f1c-106">Průměr</span><span class="sxs-lookup"><span data-stu-id="f3f1c-106">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="f3f1c-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3f1c-107">Example</span></span>  
 <span data-ttu-id="f3f1c-108">Následující příklad používá <xref:System.Linq.Enumerable.Average%2A> metody k vyhledání průměrná cena seznam produktů.</span><span class="sxs-lookup"><span data-stu-id="f3f1c-108">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average_mq)]
 [!code-vb[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average_mq)]  
  
### <a name="example"></a><span data-ttu-id="f3f1c-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3f1c-109">Example</span></span>  
 <span data-ttu-id="f3f1c-110">Následující příklad používá <xref:System.Linq.Enumerable.Average%2A> metody k vyhledání průměrná cena seznam produktů jednotlivých stylů.</span><span class="sxs-lookup"><span data-stu-id="f3f1c-110">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="f3f1c-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3f1c-111">Example</span></span>  
 <span data-ttu-id="f3f1c-112">Následující příklad používá <xref:System.Linq.Enumerable.Average%2A> metody k vyhledání celkový kvůli průměr.</span><span class="sxs-lookup"><span data-stu-id="f3f1c-112">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageprojection_mq)]
 [!code-vb[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="f3f1c-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3f1c-113">Example</span></span>  
 <span data-ttu-id="f3f1c-114">Následující příklad používá <xref:System.Linq.Enumerable.Average%2A> ID metoda získat průměr celkové potřebné pro každý kontakt.</span><span class="sxs-lookup"><span data-stu-id="f3f1c-114">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="f3f1c-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3f1c-115">Example</span></span>  
 <span data-ttu-id="f3f1c-116">Následující příklad používá <xref:System.Linq.Enumerable.Average%2A> metoda získat příkazy se průměr celkové potřebné pro každý kontakt.</span><span class="sxs-lookup"><span data-stu-id="f3f1c-116">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the orders with the average total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="f3f1c-117">Počet</span><span class="sxs-lookup"><span data-stu-id="f3f1c-117">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="f3f1c-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3f1c-118">Example</span></span>  
 <span data-ttu-id="f3f1c-119">Následující příklad používá <xref:System.Linq.Enumerable.Count%2A> metody, která vrátí počet produktů, v tabulce produktu.</span><span class="sxs-lookup"><span data-stu-id="f3f1c-119">The following example uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in the Product table.</span></span>  
  
 [!code-csharp[DP L2E Examples#Count](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#count)]
 [!code-vb[DP L2E Examples#Count](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#count)]  
  
### <a name="example"></a><span data-ttu-id="f3f1c-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3f1c-120">Example</span></span>  
 <span data-ttu-id="f3f1c-121">Následující příklad používá <xref:System.Linq.Enumerable.Count%2A> metoda vrátí seznam obraťte se na ID a kolik řadí každý má.</span><span class="sxs-lookup"><span data-stu-id="f3f1c-121">The following example uses the <xref:System.Linq.Enumerable.Count%2A> method to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countnested)]
 [!code-vb[DP L2E Examples#CountNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="f3f1c-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3f1c-122">Example</span></span>  
 <span data-ttu-id="f3f1c-123">V následujícím příkladu skupiny produkty pomocí barev a používá <xref:System.Linq.Enumerable.Count%2A> metody, která vrátí počet produktů v každé skupině barev.</span><span class="sxs-lookup"><span data-stu-id="f3f1c-123">The following example groups products by color and uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="longcount"></a><span data-ttu-id="f3f1c-124">LongCount</span><span class="sxs-lookup"><span data-stu-id="f3f1c-124">LongCount</span></span>  
  
### <a name="example"></a><span data-ttu-id="f3f1c-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3f1c-125">Example</span></span>  
 <span data-ttu-id="f3f1c-126">Následující příklad získá kontaktní počet jako dlouhých celých čísel.</span><span class="sxs-lookup"><span data-stu-id="f3f1c-126">The following example gets the contact count as a long integer.</span></span>  
  
 [!code-csharp[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#longcountsimple)]
 [!code-vb[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#longcountsimple)]  
  
## <a name="max"></a><span data-ttu-id="f3f1c-127">maximální počet</span><span class="sxs-lookup"><span data-stu-id="f3f1c-127">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="f3f1c-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3f1c-128">Example</span></span>  
 <span data-ttu-id="f3f1c-129">Následující příklad používá <xref:System.Linq.Enumerable.Max%2A> metoda získat největší celkový splatnosti.</span><span class="sxs-lookup"><span data-stu-id="f3f1c-129">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxprojection_mq)]
 [!code-vb[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="f3f1c-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3f1c-130">Example</span></span>  
 <span data-ttu-id="f3f1c-131">Následující příklad používá <xref:System.Linq.Enumerable.Max%2A> metoda získat největší celkový splatnosti pro každou obraťte se na ID.</span><span class="sxs-lookup"><span data-stu-id="f3f1c-131">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="f3f1c-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3f1c-132">Example</span></span>  
 <span data-ttu-id="f3f1c-133">Následující příklad používá <xref:System.Linq.Enumerable.Max%2A> metodu za účelem získání objednávky se největší celkový termínem pro každou obraťte se na ID.</span><span class="sxs-lookup"><span data-stu-id="f3f1c-133">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="f3f1c-134">Min.</span><span class="sxs-lookup"><span data-stu-id="f3f1c-134">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="f3f1c-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3f1c-135">Example</span></span>  
 <span data-ttu-id="f3f1c-136">Následující příklad používá <xref:System.Linq.Enumerable.Min%2A> metoda získat nejmenší celkový splatnosti.</span><span class="sxs-lookup"><span data-stu-id="f3f1c-136">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minprojection_mq)]
 [!code-vb[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="f3f1c-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3f1c-137">Example</span></span>  
 <span data-ttu-id="f3f1c-138">Následující příklad používá <xref:System.Linq.Enumerable.Min%2A> metoda získat nejmenší celkový splatnosti pro každou obraťte se na ID.</span><span class="sxs-lookup"><span data-stu-id="f3f1c-138">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="f3f1c-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3f1c-139">Example</span></span>  
 <span data-ttu-id="f3f1c-140">Následující příklad používá <xref:System.Linq.Enumerable.Min%2A> metoda získat příkazy se nejmenší celkem platnosti pro každý kontakt.</span><span class="sxs-lookup"><span data-stu-id="f3f1c-140">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="f3f1c-141">Součet</span><span class="sxs-lookup"><span data-stu-id="f3f1c-141">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="f3f1c-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3f1c-142">Example</span></span>  
 <span data-ttu-id="f3f1c-143">Následující příklad používá <xref:System.Linq.Enumerable.Sum%2A> metoda získat celkový počet počty pořadí v tabulce Podrobnosti prodejní objednávky.</span><span class="sxs-lookup"><span data-stu-id="f3f1c-143">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total number of order quantities in the SalesOrderDetail table.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumprojection_mq)]
 [!code-vb[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="f3f1c-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3f1c-144">Example</span></span>  
 <span data-ttu-id="f3f1c-145">Následující příklad používá <xref:System.Linq.Enumerable.Sum%2A> metoda získat celkový splatnosti pro každou obraťte se na ID.</span><span class="sxs-lookup"><span data-stu-id="f3f1c-145">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="f3f1c-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3f1c-146">See Also</span></span>  
 [<span data-ttu-id="f3f1c-147">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="f3f1c-147">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
