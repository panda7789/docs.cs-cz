---
title: 'Příklady syntaxe dotazů založených na volání metody: Seskupování'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb23c25c-1075-4cc3-a8ff-4db72e536c0d
ms.openlocfilehash: 8f09983aa90be666cc13ae4eba018db2ae706daa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59219223"
---
# <a name="method-based-query-syntax-examples-grouping"></a><span data-ttu-id="3ce61-102">Příklady syntaxe dotazů založených na volání metody: Seskupování</span><span class="sxs-lookup"><span data-stu-id="3ce61-102">Method-Based Query Syntax Examples: Grouping</span></span>
<span data-ttu-id="3ce61-103">Příklady v tomto tématu ukazují, jak používat `GroupBy` metodu dotazu [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) pomocí syntaxe dotazů založených na volání metody.</span><span class="sxs-lookup"><span data-stu-id="3ce61-103">The examples in this topic show you how to use the `GroupBy` method to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using method-based query syntax.</span></span> <span data-ttu-id="3ce61-104">Model prodeje AdventureWorks, který se používá v těchto příkladech je sestaven z tabulky kontaktu, adresa, produktu, SalesOrderHeader a podrobnosti prodejní objednávky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="3ce61-104">The AdventureWorks Sales Model that is used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="3ce61-105">V příkladech v tomto tématu se používá následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="3ce61-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="3ce61-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="3ce61-106">Example</span></span>  
 <span data-ttu-id="3ce61-107">V následujícím příkladu `GroupBy` metoda vrátí `Address` objekty, které jsou seskupeny podle PSČ.</span><span class="sxs-lookup"><span data-stu-id="3ce61-107">The following example uses the `GroupBy` method to return `Address` objects that are grouped by postal code.</span></span> <span data-ttu-id="3ce61-108">Výsledky se promítnou do anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="3ce61-108">The results are projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple3_mq)]
 [!code-vb[DP L2E Examples#GroupBySimple3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple3_mq)]  
  
## <a name="example"></a><span data-ttu-id="3ce61-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="3ce61-109">Example</span></span>  
 <span data-ttu-id="3ce61-110">V následujícím příkladu `GroupBy` metoda vrátí `Contact` objekty, které jsou seskupeny podle první písmeno příjmení kontaktu.</span><span class="sxs-lookup"><span data-stu-id="3ce61-110">The following example uses the `GroupBy` method to return `Contact` objects that are grouped by the first letter of the contact's last name.</span></span> <span data-ttu-id="3ce61-111">Výsledky jsou také seřazené podle první písmeno příjmení a promítnout do anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="3ce61-111">The results are also sorted by the first letter of the last name and projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple2_mq)]
 [!code-vb[DP L2E Examples#GroupBySimple2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple2_mq)]  
  
## <a name="example"></a><span data-ttu-id="3ce61-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="3ce61-112">Example</span></span>  
 <span data-ttu-id="3ce61-113">V následujícím příkladu `GroupBy` metoda vrátí `SalesOrderHeader` objekty, které jsou seskupeny podle ID zákazníka.</span><span class="sxs-lookup"><span data-stu-id="3ce61-113">The following example uses the `GroupBy` method to return `SalesOrderHeader` objects that are grouped by customer ID.</span></span> <span data-ttu-id="3ce61-114">Je také vrácen počet prodeje pro každého zákazníka.</span><span class="sxs-lookup"><span data-stu-id="3ce61-114">The number of sales for each customer is also returned.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupByCount_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbycount_mq)]
 [!code-vb[DP L2E Examples#GroupByCount_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbycount_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="3ce61-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3ce61-115">See also</span></span>

- [<span data-ttu-id="3ce61-116">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="3ce61-116">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
