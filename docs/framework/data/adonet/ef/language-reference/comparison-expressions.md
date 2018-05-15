---
title: Výrazy porovnání
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec7637a9-01d5-4a95-8bb0-478311cd263b
ms.openlocfilehash: 5d201d331d766d865d0ee7afb164813084fa3651
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="comparison-expressions"></a><span data-ttu-id="cef3f-102">Výrazy porovnání</span><span class="sxs-lookup"><span data-stu-id="cef3f-102">Comparison Expressions</span></span>
<span data-ttu-id="cef3f-103">Výraz porovnání zkontroluje, zda je konstantní hodnota, hodnota vlastnosti nebo výsledek metody stejné, není rovno, větší nebo menší než jiná hodnota.</span><span class="sxs-lookup"><span data-stu-id="cef3f-103">A comparison expression checks whether a constant value, property value, or method result is equal, not equal, greater than, or less than another value.</span></span> <span data-ttu-id="cef3f-104">Pokud konkrétní porovnání není platný pro [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="cef3f-104">If a particular comparison is not valid for [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], an exception will be thrown.</span></span> <span data-ttu-id="cef3f-105">Všechny porovnání implicitní a explicitní, vyžadují, zda jsou všechny součásti ve zdroji dat porovnatelný.</span><span class="sxs-lookup"><span data-stu-id="cef3f-105">All comparisons, both implicit and explicit, require that all components are comparable in the data source.</span></span> <span data-ttu-id="cef3f-106">Výrazy porovnání se často používají v `Where` klauzule pro omezení výsledky dotazu.</span><span class="sxs-lookup"><span data-stu-id="cef3f-106">Comparison expressions are frequently used in `Where` clauses for restricting the query results.</span></span>  
  
 <span data-ttu-id="cef3f-107">Následující příklad v syntaxe výrazu dotazu obsahuje dotaz, který vrátí výsledky, kde je rovno "SO43663" prodeje pořadové číslo:</span><span class="sxs-lookup"><span data-stu-id="cef3f-107">The following example in query expression syntax shows a query that returns results where the sales order number is equal to "SO43663":</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression)]  
  
 <span data-ttu-id="cef3f-108">V syntaxi dotazu na základě metod následující příklad ukazuje dotaz, který vrátí výsledky, kde je rovno "SO43663" prodeje pořadové číslo:</span><span class="sxs-lookup"><span data-stu-id="cef3f-108">The following example in method-based query syntax shows a query that returns results where the sales order number is equal to "SO43663":</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression_mq)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression_mq)]  
  
 <span data-ttu-id="cef3f-109">Následující příklad v syntaxe výrazu dotazu ukazuje dotaz, který vrátí informace o objednávce prodeje, kde expedice je rovno 8 července 2001:</span><span class="sxs-lookup"><span data-stu-id="cef3f-109">The following example in query expression syntax shows a query that returns sales order information where the ship date is equal to July 8, 2001:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison)]  
  
 <span data-ttu-id="cef3f-110">V syntaxi dotazu na základě metod následující příklad ukazuje dotaz, který vrátí informace o objednávce prodeje, kde expedice je rovno 8 července 2001:</span><span class="sxs-lookup"><span data-stu-id="cef3f-110">The following example in method-based query syntax shows a query that returns sales order information where the ship date is equal to July 8, 2001:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison_mq)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison_mq)]  
  
 <span data-ttu-id="cef3f-111">Výrazy, které vrací konstanta se převedou na serveru a provádí žádný pokus o provést místní vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="cef3f-111">Expressions that yield a constant are converted at the server, and no attempt to do local evaluation is performed.</span></span> <span data-ttu-id="cef3f-112">Následující příklad používá výraz v `Where` klauzuli, která vypočítá konstanta.</span><span class="sxs-lookup"><span data-stu-id="cef3f-112">The following example uses an expression in the `Where` clause that yields a constant.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]<span data-ttu-id="cef3f-113"> nepodporuje použití třídy uživatele jako konstanta.</span><span class="sxs-lookup"><span data-stu-id="cef3f-113"> does not support using a user class as a constant.</span></span> <span data-ttu-id="cef3f-114">Však odkaz na vlastnost třídy uživatel se považuje za konstantu a budou převést na strom příkaz konstantní výraz a ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="cef3f-114">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myclass)]
 [!code-vb[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myclass)]  
  
 [!code-csharp[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#propertyasconstant)]
 [!code-vb[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#propertyasconstant)]  
  
 <span data-ttu-id="cef3f-115">Metody, které vracejí konstantní výraz nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="cef3f-115">Methods that return a constant expression are not supported.</span></span> <span data-ttu-id="cef3f-116">Následující příklad obsahuje metodu v `Where` klauzuli, která vrátí konstanta.</span><span class="sxs-lookup"><span data-stu-id="cef3f-116">The following example contains a method in the `Where` clause that returns a constant.</span></span> <span data-ttu-id="cef3f-117">Tento příklad vyvolá výjimku za běhu.</span><span class="sxs-lookup"><span data-stu-id="cef3f-117">This example will throw an exception at run time.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#methodasconstantfails)]
 [!code-vb[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#methodasconstantfails)]  
  
## <a name="see-also"></a><span data-ttu-id="cef3f-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="cef3f-118">See Also</span></span>  
 [<span data-ttu-id="cef3f-119">Výrazy v dotazech LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="cef3f-119">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
