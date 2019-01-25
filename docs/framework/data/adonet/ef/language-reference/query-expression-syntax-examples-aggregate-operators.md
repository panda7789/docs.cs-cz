---
title: 'Příklady syntaxe výrazů dotazů: Agregační operátory'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d729120c-4c1b-4f34-bbe9-33694fca2dde
ms.openlocfilehash: 120dec2511d9a17422c3db83bb0981b74f9eebdd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616105"
---
# <a name="query-expression-syntax-examples-aggregate-operators"></a><span data-ttu-id="8ef82-102">Příklady syntaxe výrazů dotazů: Agregační operátory</span><span class="sxs-lookup"><span data-stu-id="8ef82-102">Query Expression Syntax Examples: Aggregate Operators</span></span>
<span data-ttu-id="8ef82-103">Příklady v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, a <xref:System.Linq.Enumerable.Sum%2A> metody k dotazování [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="8ef82-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using query expression syntax.</span></span> <span data-ttu-id="8ef82-104">Model prodeje AdventureWorks používá v těchto příkladech je sestaven z tabulky kontaktu, adresa, produktu, SalesOrderHeader a podrobnosti prodejní objednávky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="8ef82-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="8ef82-105">V příkladech v tomto tématu se používá následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="8ef82-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="average"></a><span data-ttu-id="8ef82-106">Průměr</span><span class="sxs-lookup"><span data-stu-id="8ef82-106">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="8ef82-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="8ef82-107">Example</span></span>  
 <span data-ttu-id="8ef82-108">V následujícím příkladu <xref:System.Linq.Enumerable.Average%2A> metody k vyhledání průměrná cena seznam produktů jednotlivých stylů.</span><span class="sxs-lookup"><span data-stu-id="8ef82-108">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="8ef82-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="8ef82-109">Example</span></span>  
 <span data-ttu-id="8ef82-110">Následující příklad používá <xref:System.Linq.Enumerable.Average%2A> k zjistit průměrné celkové potřebné pro každé obraťte se na ID.</span><span class="sxs-lookup"><span data-stu-id="8ef82-110">The following example uses <xref:System.Linq.Enumerable.Average%2A> to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="8ef82-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="8ef82-111">Example</span></span>  
 <span data-ttu-id="8ef82-112">Následující příklad používá <xref:System.Linq.Enumerable.Average%2A> získat objednávky s průměrem celkové potřebné pro každého kontaktu.</span><span class="sxs-lookup"><span data-stu-id="8ef82-112">The following example uses <xref:System.Linq.Enumerable.Average%2A> to get the orders with the average total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="8ef82-113">Počet</span><span class="sxs-lookup"><span data-stu-id="8ef82-113">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="8ef82-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="8ef82-114">Example</span></span>  
 <span data-ttu-id="8ef82-115">Následující příklad používá <xref:System.Linq.Enumerable.Count%2A> vrátí seznam ID kontaktu a kolik objednávky, každá má.</span><span class="sxs-lookup"><span data-stu-id="8ef82-115">The following example uses <xref:System.Linq.Enumerable.Count%2A> to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countnested)]
 [!code-vb[DP L2E Examples#CountNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="8ef82-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="8ef82-116">Example</span></span>  
 <span data-ttu-id="8ef82-117">Následující příklad skupiny produktů pomocí barev a používá <xref:System.Linq.Enumerable.Count%2A> k vrácení počtu produktů v každé skupině barvu.</span><span class="sxs-lookup"><span data-stu-id="8ef82-117">The following example groups products by color and uses <xref:System.Linq.Enumerable.Count%2A> to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="max"></a><span data-ttu-id="8ef82-118">Maximum</span><span class="sxs-lookup"><span data-stu-id="8ef82-118">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="8ef82-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="8ef82-119">Example</span></span>  
 <span data-ttu-id="8ef82-120">V následujícím příkladu <xref:System.Linq.Enumerable.Max%2A> metodu k získání největší dlužná pro každou obraťte se na ID.</span><span class="sxs-lookup"><span data-stu-id="8ef82-120">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="8ef82-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="8ef82-121">Example</span></span>  
 <span data-ttu-id="8ef82-122">V následujícím příkladu <xref:System.Linq.Enumerable.Max%2A> metodu k získání s největší celková částka objednávky pro každou obraťte se na ID.</span><span class="sxs-lookup"><span data-stu-id="8ef82-122">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="8ef82-123">Minimum</span><span class="sxs-lookup"><span data-stu-id="8ef82-123">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="8ef82-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="8ef82-124">Example</span></span>  
 <span data-ttu-id="8ef82-125">V následujícím příkladu <xref:System.Linq.Enumerable.Min%2A> metodu k získání nejmenší dlužná pro každou obraťte se na ID.</span><span class="sxs-lookup"><span data-stu-id="8ef82-125">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="8ef82-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="8ef82-126">Example</span></span>  
 <span data-ttu-id="8ef82-127">V následujícím příkladu <xref:System.Linq.Enumerable.Min%2A> metodu k získání objednávky nejmenší celkem termín pro každého kontaktu.</span><span class="sxs-lookup"><span data-stu-id="8ef82-127">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="8ef82-128">Součet</span><span class="sxs-lookup"><span data-stu-id="8ef82-128">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="8ef82-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="8ef82-129">Example</span></span>  
 <span data-ttu-id="8ef82-130">V následujícím příkladu <xref:System.Linq.Enumerable.Sum%2A> metodu k získání celkové termín pro každou obraťte se na ID.</span><span class="sxs-lookup"><span data-stu-id="8ef82-130">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="8ef82-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8ef82-131">See also</span></span>
- [<span data-ttu-id="8ef82-132">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="8ef82-132">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
