---
title: Výrazy porovnání
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec7637a9-01d5-4a95-8bb0-478311cd263b
ms.openlocfilehash: d0926bb1a0e35caa058f268f0a0c414e805a8674
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251175"
---
# <a name="comparison-expressions"></a><span data-ttu-id="5f8e9-102">Výrazy porovnání</span><span class="sxs-lookup"><span data-stu-id="5f8e9-102">Comparison Expressions</span></span>
<span data-ttu-id="5f8e9-103">Výraz porovnání kontroluje, zda je konstantní hodnota, hodnota vlastnosti nebo výsledek metody rovná, není rovno, větší než nebo menší než jiná hodnota.</span><span class="sxs-lookup"><span data-stu-id="5f8e9-103">A comparison expression checks whether a constant value, property value, or method result is equal, not equal, greater than, or less than another value.</span></span> <span data-ttu-id="5f8e9-104">Pokud určité porovnání není pro LINQ to Entities platné, vyvolá se výjimka.</span><span class="sxs-lookup"><span data-stu-id="5f8e9-104">If a particular comparison is not valid for LINQ to Entities, an exception will be thrown.</span></span> <span data-ttu-id="5f8e9-105">Všechna porovnání, implicitně i explicitní, vyžadují, aby všechny komponenty byly srovnatelné ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="5f8e9-105">All comparisons, both implicit and explicit, require that all components are comparable in the data source.</span></span> <span data-ttu-id="5f8e9-106">Výrazy porovnání se často používají v `Where` klauzulích pro omezení výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="5f8e9-106">Comparison expressions are frequently used in `Where` clauses for restricting the query results.</span></span>  
  
 <span data-ttu-id="5f8e9-107">Následující příklad v syntaxi výrazu dotazu zobrazuje dotaz, který vrací výsledky, kde je číslo prodejní objednávky rovno "SO43663":</span><span class="sxs-lookup"><span data-stu-id="5f8e9-107">The following example in query expression syntax shows a query that returns results where the sales order number is equal to "SO43663":</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression)]  
  
 <span data-ttu-id="5f8e9-108">Následující příklad v syntaxi dotazu založeného na metodách zobrazuje dotaz, který vrací výsledky, kde je číslo prodejní objednávky rovno "SO43663":</span><span class="sxs-lookup"><span data-stu-id="5f8e9-108">The following example in method-based query syntax shows a query that returns results where the sales order number is equal to "SO43663":</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression_mq)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression_mq)]  
  
 <span data-ttu-id="5f8e9-109">Následující příklad v syntaxi výrazu dotazu zobrazuje dotaz, který vrací informace o prodejní objednávce, kde je datum expedice rovno 8. července 2001:</span><span class="sxs-lookup"><span data-stu-id="5f8e9-109">The following example in query expression syntax shows a query that returns sales order information where the ship date is equal to July 8, 2001:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison)]  
  
 <span data-ttu-id="5f8e9-110">Následující příklad v syntaxi dotazu založeného na metodách zobrazuje dotaz, který vrací informace o prodejní objednávce, kde je datum expedice rovno 8. července 2001:</span><span class="sxs-lookup"><span data-stu-id="5f8e9-110">The following example in method-based query syntax shows a query that returns sales order information where the ship date is equal to July 8, 2001:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison_mq)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison_mq)]  
  
 <span data-ttu-id="5f8e9-111">Výrazy, které jsou výsledkem konstanty, jsou převedeny na serveru a není proveden žádný pokus o provedení místního vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="5f8e9-111">Expressions that yield a constant are converted at the server, and no attempt to do local evaluation is performed.</span></span> <span data-ttu-id="5f8e9-112">Následující příklad používá výraz v `Where` klauzuli, která je výsledkem konstanty.</span><span class="sxs-lookup"><span data-stu-id="5f8e9-112">The following example uses an expression in the `Where` clause that yields a constant.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 <span data-ttu-id="5f8e9-113">LINQ to Entities nepodporuje použití třídy uživatele jako konstanty.</span><span class="sxs-lookup"><span data-stu-id="5f8e9-113">LINQ to Entities does not support using a user class as a constant.</span></span> <span data-ttu-id="5f8e9-114">Odkaz na vlastnost třídy uživatele se však považuje za konstantu a bude převeden na výraz konstantního stromu příkazů a proveden ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="5f8e9-114">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myclass)]
 [!code-vb[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myclass)]  
  
 [!code-csharp[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#propertyasconstant)]
 [!code-vb[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#propertyasconstant)]  
  
 <span data-ttu-id="5f8e9-115">Metody, které vracejí konstantní výraz, nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="5f8e9-115">Methods that return a constant expression are not supported.</span></span> <span data-ttu-id="5f8e9-116">Následující příklad obsahuje metodu v `Where` klauzuli, která vrací konstantu.</span><span class="sxs-lookup"><span data-stu-id="5f8e9-116">The following example contains a method in the `Where` clause that returns a constant.</span></span> <span data-ttu-id="5f8e9-117">Tento příklad vyvolá výjimku za běhu.</span><span class="sxs-lookup"><span data-stu-id="5f8e9-117">This example will throw an exception at run time.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#methodasconstantfails)]
 [!code-vb[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#methodasconstantfails)]  
  
## <a name="see-also"></a><span data-ttu-id="5f8e9-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5f8e9-118">See also</span></span>

- [<span data-ttu-id="5f8e9-119">Výrazy v dotazech LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="5f8e9-119">Expressions in LINQ to Entities Queries</span></span>](expressions-in-linq-to-entities-queries.md)
