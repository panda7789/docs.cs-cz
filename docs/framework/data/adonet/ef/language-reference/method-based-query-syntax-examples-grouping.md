---
title: 'Příklady syntaxe dotazů metoda: seskupování'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb23c25c-1075-4cc3-a8ff-4db72e536c0d
ms.openlocfilehash: 1bc2ab6f7dbfb3b2babcc5a9565a7bfd9fd962c4
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="method-based-query-syntax-examples-grouping"></a><span data-ttu-id="ccb8e-102">Příklady syntaxe dotazů metoda: seskupování</span><span class="sxs-lookup"><span data-stu-id="ccb8e-102">Method-Based Query Syntax Examples: Grouping</span></span>
<span data-ttu-id="ccb8e-103">V příkladech v tomto tématu ukazují, jak používat `GroupBy` metodu pro dotaz [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) pomocí syntaxe dotazu na základě metod.</span><span class="sxs-lookup"><span data-stu-id="ccb8e-103">The examples in this topic show you how to use the `GroupBy` method to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="ccb8e-104">Model prodeje společnosti AdventureWorks, který se používá v těchto příkladech je sestaven z kontaktu, adresu, produktu, SalesOrderHeader a podrobnosti prodejní objednávky tabulky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="ccb8e-104">The AdventureWorks Sales Model that is used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="ccb8e-105">V příkladech v tomto tématu použijte následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="ccb8e-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="ccb8e-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="ccb8e-106">Example</span></span>  
 <span data-ttu-id="ccb8e-107">Následující příklad používá `GroupBy` metoda vrátí `Address` objekty, které jsou seskupené podle PSČ.</span><span class="sxs-lookup"><span data-stu-id="ccb8e-107">The following example uses the `GroupBy` method to return `Address` objects that are grouped by postal code.</span></span> <span data-ttu-id="ccb8e-108">Výsledky se promítá do anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="ccb8e-108">The results are projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple3_mq)]
 [!code-vb[DP L2E Examples#GroupBySimple3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple3_mq)]  
  
## <a name="example"></a><span data-ttu-id="ccb8e-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="ccb8e-109">Example</span></span>  
 <span data-ttu-id="ccb8e-110">Následující příklad používá `GroupBy` metoda vrátí `Contact` objekty, které jsou seskupené podle první písmeno poslední jméno kontaktu.</span><span class="sxs-lookup"><span data-stu-id="ccb8e-110">The following example uses the `GroupBy` method to return `Contact` objects that are grouped by the first letter of the contact's last name.</span></span> <span data-ttu-id="ccb8e-111">Výsledky jsou také seřazené podle první písmeno příjmení a promítnout do anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="ccb8e-111">The results are also sorted by the first letter of the last name and projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple2_mq)]
 [!code-vb[DP L2E Examples#GroupBySimple2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple2_mq)]  
  
## <a name="example"></a><span data-ttu-id="ccb8e-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="ccb8e-112">Example</span></span>  
 <span data-ttu-id="ccb8e-113">Následující příklad používá `GroupBy` metoda vrátí `SalesOrderHeader` objekty, které jsou seskupené podle ID zákazníka.</span><span class="sxs-lookup"><span data-stu-id="ccb8e-113">The following example uses the `GroupBy` method to return `SalesOrderHeader` objects that are grouped by customer ID.</span></span> <span data-ttu-id="ccb8e-114">Vrátí počet prodeje pro každého zákazníka.</span><span class="sxs-lookup"><span data-stu-id="ccb8e-114">The number of sales for each customer is also returned.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupByCount_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbycount_mq)]
 [!code-vb[DP L2E Examples#GroupByCount_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbycount_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="ccb8e-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="ccb8e-115">See Also</span></span>  
 [<span data-ttu-id="ccb8e-116">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="ccb8e-116">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
