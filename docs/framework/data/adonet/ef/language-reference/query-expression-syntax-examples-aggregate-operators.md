---
title: "Příklady syntaxe výrazu dotazu: Agregační operátory"
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
ms.assetid: d729120c-4c1b-4f34-bbe9-33694fca2dde
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2cdf1ffc9b7bd03aa7fa5bb6d4b5679cf936e80c
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="query-expression-syntax-examples-aggregate-operators"></a><span data-ttu-id="4aa47-102">Příklady syntaxe výrazu dotazu: Agregační operátory</span><span class="sxs-lookup"><span data-stu-id="4aa47-102">Query Expression Syntax Examples: Aggregate Operators</span></span>
<span data-ttu-id="4aa47-103">V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, a <xref:System.Linq.Enumerable.Sum%2A> metody k dotazování [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="4aa47-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) using query expression syntax.</span></span> <span data-ttu-id="4aa47-104">Model prodeje společnosti AdventureWorks použít v těchto příkladech je sestaven z kontaktu, adresu, produktu, SalesOrderHeader a podrobnosti prodejní objednávky tabulky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="4aa47-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="4aa47-105">V příkladech v tomto tématu použijte následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="4aa47-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="average"></a><span data-ttu-id="4aa47-106">Průměr</span><span class="sxs-lookup"><span data-stu-id="4aa47-106">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="4aa47-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="4aa47-107">Example</span></span>  
 <span data-ttu-id="4aa47-108">Následující příklad používá <xref:System.Linq.Enumerable.Average%2A> metody k vyhledání průměrná cena seznam produktů jednotlivých stylů.</span><span class="sxs-lookup"><span data-stu-id="4aa47-108">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="4aa47-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="4aa47-109">Example</span></span>  
 <span data-ttu-id="4aa47-110">Následující příklad používá <xref:System.Linq.Enumerable.Average%2A> získat průměr celkové potřebné pro každé obraťte se na ID.</span><span class="sxs-lookup"><span data-stu-id="4aa47-110">The following example uses <xref:System.Linq.Enumerable.Average%2A> to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="4aa47-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="4aa47-111">Example</span></span>  
 <span data-ttu-id="4aa47-112">Následující příklad používá <xref:System.Linq.Enumerable.Average%2A> získat příkazy se průměr celkové potřebné pro každý kontakt.</span><span class="sxs-lookup"><span data-stu-id="4aa47-112">The following example uses <xref:System.Linq.Enumerable.Average%2A> to get the orders with the average total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="4aa47-113">Počet</span><span class="sxs-lookup"><span data-stu-id="4aa47-113">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="4aa47-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="4aa47-114">Example</span></span>  
 <span data-ttu-id="4aa47-115">Následující příklad používá <xref:System.Linq.Enumerable.Count%2A> vrátí seznam obraťte se na ID a kolik řadí každý má.</span><span class="sxs-lookup"><span data-stu-id="4aa47-115">The following example uses <xref:System.Linq.Enumerable.Count%2A> to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countnested)]
 [!code-vb[DP L2E Examples#CountNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="4aa47-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="4aa47-116">Example</span></span>  
 <span data-ttu-id="4aa47-117">V následujícím příkladu skupiny produkty pomocí barev a používá <xref:System.Linq.Enumerable.Count%2A> k vrácení počtu produktů v každé skupině barev.</span><span class="sxs-lookup"><span data-stu-id="4aa47-117">The following example groups products by color and uses <xref:System.Linq.Enumerable.Count%2A> to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="max"></a><span data-ttu-id="4aa47-118">Max</span><span class="sxs-lookup"><span data-stu-id="4aa47-118">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="4aa47-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="4aa47-119">Example</span></span>  
 <span data-ttu-id="4aa47-120">Následující příklad používá <xref:System.Linq.Enumerable.Max%2A> metoda získat největší celkový splatnosti pro každou obraťte se na ID.</span><span class="sxs-lookup"><span data-stu-id="4aa47-120">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="4aa47-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="4aa47-121">Example</span></span>  
 <span data-ttu-id="4aa47-122">Následující příklad používá <xref:System.Linq.Enumerable.Max%2A> metodu za účelem získání objednávky se největší celkový termínem pro každou obraťte se na ID.</span><span class="sxs-lookup"><span data-stu-id="4aa47-122">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="4aa47-123">Min.</span><span class="sxs-lookup"><span data-stu-id="4aa47-123">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="4aa47-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="4aa47-124">Example</span></span>  
 <span data-ttu-id="4aa47-125">Následující příklad používá <xref:System.Linq.Enumerable.Min%2A> metoda získat nejmenší celkový splatnosti pro každou obraťte se na ID.</span><span class="sxs-lookup"><span data-stu-id="4aa47-125">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="4aa47-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="4aa47-126">Example</span></span>  
 <span data-ttu-id="4aa47-127">Následující příklad používá <xref:System.Linq.Enumerable.Min%2A> metoda získat příkazy se nejmenší celkem platnosti pro každý kontakt.</span><span class="sxs-lookup"><span data-stu-id="4aa47-127">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="4aa47-128">Součet</span><span class="sxs-lookup"><span data-stu-id="4aa47-128">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="4aa47-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="4aa47-129">Example</span></span>  
 <span data-ttu-id="4aa47-130">Následující příklad používá <xref:System.Linq.Enumerable.Sum%2A> metoda získat celkový splatnosti pro každou obraťte se na ID.</span><span class="sxs-lookup"><span data-stu-id="4aa47-130">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="4aa47-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="4aa47-131">See Also</span></span>  
 [<span data-ttu-id="4aa47-132">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="4aa47-132">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
