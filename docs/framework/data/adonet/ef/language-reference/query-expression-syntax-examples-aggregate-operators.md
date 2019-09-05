---
title: 'Příklady syntaxe výrazů dotazů: Agregační operátory'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d729120c-4c1b-4f34-bbe9-33694fca2dde
ms.openlocfilehash: 5090616705c799f2905226b4892fa1fbe50bfbf3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249529"
---
# <a name="query-expression-syntax-examples-aggregate-operators"></a><span data-ttu-id="01d69-102">Příklady syntaxe výrazů dotazů: Agregační operátory</span><span class="sxs-lookup"><span data-stu-id="01d69-102">Query Expression Syntax Examples: Aggregate Operators</span></span>
<span data-ttu-id="01d69-103">Příklady v tomto tématu ukazují <xref:System.Linq.Enumerable.Average%2A> <xref:System.Linq.Enumerable.Max%2A>, jak použít metody, <xref:System.Linq.Enumerable.Count%2A>,, <xref:System.Linq.Enumerable.Min%2A>a <xref:System.Linq.Enumerable.Sum%2A> k dotazování [modelu prodeje AdventureWorks](https://archive.codeplex.com/?p=msftdbprodsamples) pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="01d69-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using query expression syntax.</span></span> <span data-ttu-id="01d69-104">Model prodeje společnosti AdventureWorks použitý v těchto příkladech je sestaven z tabulek Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="01d69-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="01d69-105">Příklady v tomto tématu používají následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="01d69-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="average"></a><span data-ttu-id="01d69-106">Average</span><span class="sxs-lookup"><span data-stu-id="01d69-106">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="01d69-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="01d69-107">Example</span></span>  
 <span data-ttu-id="01d69-108">Následující příklad používá <xref:System.Linq.Enumerable.Average%2A> metodu k nalezení průměrné ceníkové ceny produktů každého stylu.</span><span class="sxs-lookup"><span data-stu-id="01d69-108">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="01d69-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="01d69-109">Example</span></span>  
 <span data-ttu-id="01d69-110">Následující příklad používá <xref:System.Linq.Enumerable.Average%2A> k získání průměrného součtu z důvodu ID kontaktu.</span><span class="sxs-lookup"><span data-stu-id="01d69-110">The following example uses <xref:System.Linq.Enumerable.Average%2A> to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="01d69-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="01d69-111">Example</span></span>  
 <span data-ttu-id="01d69-112">Následující příklad používá <xref:System.Linq.Enumerable.Average%2A> k získání objednávek s průměrnou celkovou splatnou pro každý kontakt.</span><span class="sxs-lookup"><span data-stu-id="01d69-112">The following example uses <xref:System.Linq.Enumerable.Average%2A> to get the orders with the average total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="01d69-113">Count</span><span class="sxs-lookup"><span data-stu-id="01d69-113">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="01d69-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="01d69-114">Example</span></span>  
 <span data-ttu-id="01d69-115">Následující příklad používá <xref:System.Linq.Enumerable.Count%2A> k vrácení seznamu ID kontaktů a kolik objednávek má.</span><span class="sxs-lookup"><span data-stu-id="01d69-115">The following example uses <xref:System.Linq.Enumerable.Count%2A> to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countnested)]
 [!code-vb[DP L2E Examples#CountNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="01d69-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="01d69-116">Example</span></span>  
 <span data-ttu-id="01d69-117">Následující příklad seskupuje produkty podle barev a používá <xref:System.Linq.Enumerable.Count%2A> k vrácení počtu produktů v každé skupině barev.</span><span class="sxs-lookup"><span data-stu-id="01d69-117">The following example groups products by color and uses <xref:System.Linq.Enumerable.Count%2A> to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="max"></a><span data-ttu-id="01d69-118">Maximum</span><span class="sxs-lookup"><span data-stu-id="01d69-118">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="01d69-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="01d69-119">Example</span></span>  
 <span data-ttu-id="01d69-120">Následující příklad používá <xref:System.Linq.Enumerable.Max%2A> metodu k získání největšího celku v důsledku ID kontaktu.</span><span class="sxs-lookup"><span data-stu-id="01d69-120">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="01d69-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="01d69-121">Example</span></span>  
 <span data-ttu-id="01d69-122">Následující příklad používá <xref:System.Linq.Enumerable.Max%2A> metodu k získání objednávek, jejichž největší celková hodnota je splatná pro každé ID kontaktu.</span><span class="sxs-lookup"><span data-stu-id="01d69-122">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="01d69-123">Minimum</span><span class="sxs-lookup"><span data-stu-id="01d69-123">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="01d69-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="01d69-124">Example</span></span>  
 <span data-ttu-id="01d69-125">Následující příklad používá <xref:System.Linq.Enumerable.Min%2A> metodu k získání nejmenšího celku v důsledku ID kontaktu.</span><span class="sxs-lookup"><span data-stu-id="01d69-125">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="01d69-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="01d69-126">Example</span></span>  
 <span data-ttu-id="01d69-127">Následující příklad používá <xref:System.Linq.Enumerable.Min%2A> metodu k získání objednávek s nejmenším součtem v důsledku každého kontaktu.</span><span class="sxs-lookup"><span data-stu-id="01d69-127">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="01d69-128">Součet</span><span class="sxs-lookup"><span data-stu-id="01d69-128">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="01d69-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="01d69-129">Example</span></span>  
 <span data-ttu-id="01d69-130">Následující příklad používá <xref:System.Linq.Enumerable.Sum%2A> metodu k získání celkového součtu pro každé ID kontaktu.</span><span class="sxs-lookup"><span data-stu-id="01d69-130">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="01d69-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="01d69-131">See also</span></span>

- [<span data-ttu-id="01d69-132">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="01d69-132">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
