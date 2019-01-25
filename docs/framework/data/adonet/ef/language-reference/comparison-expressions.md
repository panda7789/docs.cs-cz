---
title: Výrazy porovnání
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec7637a9-01d5-4a95-8bb0-478311cd263b
ms.openlocfilehash: cca909e67464d08c0bb4ff8a0d0186d9d600ce18
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596342"
---
# <a name="comparison-expressions"></a><span data-ttu-id="44634-102">Výrazy porovnání</span><span class="sxs-lookup"><span data-stu-id="44634-102">Comparison Expressions</span></span>
<span data-ttu-id="44634-103">Výrazu porovnání kontroluje, zda je konstantní hodnota, hodnota vlastnosti nebo výsledek metody stejné, není rovno, větší než nebo menší než jiná hodnota.</span><span class="sxs-lookup"><span data-stu-id="44634-103">A comparison expression checks whether a constant value, property value, or method result is equal, not equal, greater than, or less than another value.</span></span> <span data-ttu-id="44634-104">Pokud je konkrétní porovnání není platný pro [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="44634-104">If a particular comparison is not valid for [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], an exception will be thrown.</span></span> <span data-ttu-id="44634-105">Všechny porovnání implicitní a explicitní, vyžadují, že jsou všechny součásti ve zdroji dat srovnatelné.</span><span class="sxs-lookup"><span data-stu-id="44634-105">All comparisons, both implicit and explicit, require that all components are comparable in the data source.</span></span> <span data-ttu-id="44634-106">Porovnání výrazů jsou často používána ve `Where` klauzule pro omezení výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="44634-106">Comparison expressions are frequently used in `Where` clauses for restricting the query results.</span></span>  
  
 <span data-ttu-id="44634-107">Následující příklad v syntaxe výrazu dotazu ukazuje dotaz, který vrátí výsledky, kde se rovná "SO43663" číslo prodejní objednávky:</span><span class="sxs-lookup"><span data-stu-id="44634-107">The following example in query expression syntax shows a query that returns results where the sales order number is equal to "SO43663":</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression)]  
  
 <span data-ttu-id="44634-108">Následující příklad v syntaxi dotazů založených na volání metody ukazuje dotaz, který vrátí výsledky, kde se rovná "SO43663" číslo prodejní objednávky:</span><span class="sxs-lookup"><span data-stu-id="44634-108">The following example in method-based query syntax shows a query that returns results where the sales order number is equal to "SO43663":</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression_mq)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression_mq)]  
  
 <span data-ttu-id="44634-109">Následující příklad v syntaxe výrazu dotazu ukazuje dotaz, který vrací informace prodejní objednávky, kde se rovná 8. července 2001 příjemce datum:</span><span class="sxs-lookup"><span data-stu-id="44634-109">The following example in query expression syntax shows a query that returns sales order information where the ship date is equal to July 8, 2001:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison)]  
  
 <span data-ttu-id="44634-110">Následující příklad v syntaxi dotazů založených na volání metody ukazuje dotaz, který vrací informace prodejní objednávky, kde se rovná 8. července 2001 příjemce datum:</span><span class="sxs-lookup"><span data-stu-id="44634-110">The following example in method-based query syntax shows a query that returns sales order information where the ship date is equal to July 8, 2001:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison_mq)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison_mq)]  
  
 <span data-ttu-id="44634-111">Výrazů, které vrací konstantu se převedou na serveru a provést žádný pokus o provést místní testování.</span><span class="sxs-lookup"><span data-stu-id="44634-111">Expressions that yield a constant are converted at the server, and no attempt to do local evaluation is performed.</span></span> <span data-ttu-id="44634-112">Následující příklad používá výraz v `Where` klauzuli, která vrací konstantu.</span><span class="sxs-lookup"><span data-stu-id="44634-112">The following example uses an expression in the `Where` clause that yields a constant.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] <span data-ttu-id="44634-113">nepodporuje použití třídy uživatelů jako konstanta.</span><span class="sxs-lookup"><span data-stu-id="44634-113">does not support using a user class as a constant.</span></span> <span data-ttu-id="44634-114">Však odkaz na vlastnost ve třídě uživatele je považován za konstantu a bude převeden na příkaz konstantní výraz stromu a ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="44634-114">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myclass)]
 [!code-vb[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myclass)]  
  
 [!code-csharp[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#propertyasconstant)]
 [!code-vb[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#propertyasconstant)]  
  
 <span data-ttu-id="44634-115">Metody, které vracejí konstantního výrazu nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="44634-115">Methods that return a constant expression are not supported.</span></span> <span data-ttu-id="44634-116">Následující příklad obsahuje metodu v `Where` klauzuli, která vrátí konstantu.</span><span class="sxs-lookup"><span data-stu-id="44634-116">The following example contains a method in the `Where` clause that returns a constant.</span></span> <span data-ttu-id="44634-117">Tento příklad vyvolá výjimku v době běhu.</span><span class="sxs-lookup"><span data-stu-id="44634-117">This example will throw an exception at run time.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#methodasconstantfails)]
 [!code-vb[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#methodasconstantfails)]  
  
## <a name="see-also"></a><span data-ttu-id="44634-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="44634-118">See also</span></span>
- [<span data-ttu-id="44634-119">Výrazy v dotazech LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="44634-119">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
