---
title: 'Příklady syntaxe výrazu dotazu: seskupování'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2d83d7c0-b3be-4c92-a630-25cd1285de31
ms.openlocfilehash: a5222110bc5ac41ecaaa8e5003262360fd4d9ff5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="query-expression-syntax-examples-grouping"></a><span data-ttu-id="3374c-102">Příklady syntaxe výrazu dotazu: seskupování</span><span class="sxs-lookup"><span data-stu-id="3374c-102">Query Expression Syntax Examples: Grouping</span></span>
<span data-ttu-id="3374c-103">V příkladech v tomto tématu ukazují, jak používat `GroupBy` metodu pro dotaz [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="3374c-103">The examples in this topic demonstrate how to use the `GroupBy` method to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using query expression syntax.</span></span> <span data-ttu-id="3374c-104">Model prodeje společnosti AdventureWorks použít v těchto příkladech je sestaven z kontaktu, adresu, produktu, SalesOrderHeader a podrobnosti prodejní objednávky tabulky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="3374c-104">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="3374c-105">V příkladech v tomto tématu použijte následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="3374c-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="3374c-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="3374c-106">Example</span></span>  
 <span data-ttu-id="3374c-107">Následující příklad vrací `Address` objekty seskupené podle PSČ.</span><span class="sxs-lookup"><span data-stu-id="3374c-107">The following example returns `Address` objects grouped by postal code.</span></span> <span data-ttu-id="3374c-108">Výsledky se promítá do anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="3374c-108">The results are projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple3)]
 [!code-vb[DP L2E Examples#GroupBySimple3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple3)]  
  
## <a name="example"></a><span data-ttu-id="3374c-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="3374c-109">Example</span></span>  
 <span data-ttu-id="3374c-110">Následující příklad vrací `Contact` objekty seskupené podle první písmeno poslední jméno kontaktu.</span><span class="sxs-lookup"><span data-stu-id="3374c-110">The following example returns `Contact` objects grouped by the first letter of the contact's last name.</span></span> <span data-ttu-id="3374c-111">Výsledky jsou také seřazené podle první písmeno příjmení a promítnout do anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="3374c-111">The results are also sorted by the first letter of last name and projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple2)]
 [!code-vb[DP L2E Examples#GroupBySimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple2)]  
  
## <a name="example"></a><span data-ttu-id="3374c-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="3374c-112">Example</span></span>  
 <span data-ttu-id="3374c-113">Následující příklad vrací `SalesOrderHeader` objekty seskupené podle ID zákazníka.</span><span class="sxs-lookup"><span data-stu-id="3374c-113">The following example returns `SalesOrderHeader` objects grouped by customer ID.</span></span> <span data-ttu-id="3374c-114">Vrátí počet prodeje pro každého zákazníka.</span><span class="sxs-lookup"><span data-stu-id="3374c-114">The number of sales for each customer is also returned.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupByCount](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbycount)]
 [!code-vb[DP L2E Examples#GroupByCount](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbycount)]  
  
## <a name="see-also"></a><span data-ttu-id="3374c-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="3374c-115">See Also</span></span>  
 [<span data-ttu-id="3374c-116">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="3374c-116">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
