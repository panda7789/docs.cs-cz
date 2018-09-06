---
title: 'Příklady syntaxe výrazů dotazů: seskupení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2d83d7c0-b3be-4c92-a630-25cd1285de31
ms.openlocfilehash: 519f9073954e8f7710c9e73b61f40b4fcfefd25b
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43740309"
---
# <a name="query-expression-syntax-examples-grouping"></a><span data-ttu-id="524c6-102">Příklady syntaxe výrazů dotazů: seskupení</span><span class="sxs-lookup"><span data-stu-id="524c6-102">Query Expression Syntax Examples: Grouping</span></span>
<span data-ttu-id="524c6-103">Příklady v tomto tématu ukazují, jak používat `GroupBy` metodu dotazu [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="524c6-103">The examples in this topic demonstrate how to use the `GroupBy` method to query the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using query expression syntax.</span></span> <span data-ttu-id="524c6-104">Prodeje společnosti AdventureWorks model používaný v těchto příkladech je sestaven z tabulky kontaktu, adresa, produktu, SalesOrderHeader a podrobnosti prodejní objednávky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="524c6-104">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="524c6-105">V příkladech v tomto tématu se používá následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="524c6-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="524c6-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="524c6-106">Example</span></span>  
 <span data-ttu-id="524c6-107">Následující příklad vrátí `Address` objekty seskupené podle PSČ.</span><span class="sxs-lookup"><span data-stu-id="524c6-107">The following example returns `Address` objects grouped by postal code.</span></span> <span data-ttu-id="524c6-108">Výsledky se promítnou do anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="524c6-108">The results are projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple3)]
 [!code-vb[DP L2E Examples#GroupBySimple3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple3)]  
  
## <a name="example"></a><span data-ttu-id="524c6-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="524c6-109">Example</span></span>  
 <span data-ttu-id="524c6-110">Následující příklad vrátí `Contact` objekty seskupené podle první písmeno příjmení kontaktu.</span><span class="sxs-lookup"><span data-stu-id="524c6-110">The following example returns `Contact` objects grouped by the first letter of the contact's last name.</span></span> <span data-ttu-id="524c6-111">Výsledky jsou také seřazené podle první písmeno příjmení a promítnout do anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="524c6-111">The results are also sorted by the first letter of last name and projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple2)]
 [!code-vb[DP L2E Examples#GroupBySimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple2)]  
  
## <a name="example"></a><span data-ttu-id="524c6-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="524c6-112">Example</span></span>  
 <span data-ttu-id="524c6-113">Následující příklad vrátí `SalesOrderHeader` objekty seskupené podle ID zákazníka.</span><span class="sxs-lookup"><span data-stu-id="524c6-113">The following example returns `SalesOrderHeader` objects grouped by customer ID.</span></span> <span data-ttu-id="524c6-114">Je také vrácen počet prodeje pro každého zákazníka.</span><span class="sxs-lookup"><span data-stu-id="524c6-114">The number of sales for each customer is also returned.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupByCount](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbycount)]
 [!code-vb[DP L2E Examples#GroupByCount](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbycount)]  
  
## <a name="see-also"></a><span data-ttu-id="524c6-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="524c6-115">See Also</span></span>  
 [<span data-ttu-id="524c6-116">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="524c6-116">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
