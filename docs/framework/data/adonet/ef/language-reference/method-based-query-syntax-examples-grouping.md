---
title: 'Příklady syntaxe dotazů založených na volání metody: Seskupování'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb23c25c-1075-4cc3-a8ff-4db72e536c0d
ms.openlocfilehash: 513d66c036b81b93e9692f060443ed193625898e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398503"
---
# <a name="method-based-query-syntax-examples-grouping"></a><span data-ttu-id="e0f8d-102">Příklady syntaxe dotazů založených na volání metody: Seskupování</span><span class="sxs-lookup"><span data-stu-id="e0f8d-102">Method-Based Query Syntax Examples: Grouping</span></span>
<span data-ttu-id="e0f8d-103">Příklady v tomto tématu ukazují, jak použít `GroupBy` metodu pro dotazování [modelu prodeje AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) pomocí syntaxe dotazu založeného na metodách.</span><span class="sxs-lookup"><span data-stu-id="e0f8d-103">The examples in this topic show you how to use the `GroupBy` method to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="e0f8d-104">Model prodeje společnosti AdventureWorks, který se používá v těchto příkladech, je sestaven z tabulek Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e0f8d-104">The AdventureWorks Sales Model that is used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="e0f8d-105">Příklady v tomto tématu používají následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="e0f8d-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="e0f8d-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="e0f8d-106">Example</span></span>  
 <span data-ttu-id="e0f8d-107">Následující příklad používá `GroupBy` metodu pro vrácení `Address` objektů, které jsou seskupeny podle poštovního směrovacího čísla.</span><span class="sxs-lookup"><span data-stu-id="e0f8d-107">The following example uses the `GroupBy` method to return `Address` objects that are grouped by postal code.</span></span> <span data-ttu-id="e0f8d-108">Výsledky se projektují do anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="e0f8d-108">The results are projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple3_mq)]
 [!code-vb[DP L2E Examples#GroupBySimple3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple3_mq)]  
  
## <a name="example"></a><span data-ttu-id="e0f8d-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="e0f8d-109">Example</span></span>  
 <span data-ttu-id="e0f8d-110">Následující příklad používá `GroupBy` metodu k vrácení `Contact` objektů, které jsou seskupeny podle prvního písmene příjmení kontaktu.</span><span class="sxs-lookup"><span data-stu-id="e0f8d-110">The following example uses the `GroupBy` method to return `Contact` objects that are grouped by the first letter of the contact's last name.</span></span> <span data-ttu-id="e0f8d-111">Výsledky jsou také seřazené podle prvního písmene příjmení a projekt se pak do anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="e0f8d-111">The results are also sorted by the first letter of the last name and projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple2_mq)]
 [!code-vb[DP L2E Examples#GroupBySimple2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple2_mq)]  
  
## <a name="example"></a><span data-ttu-id="e0f8d-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="e0f8d-112">Example</span></span>  
 <span data-ttu-id="e0f8d-113">Následující příklad používá `GroupBy` metodu pro vrácení `SalesOrderHeader` objektů, které jsou seskupeny podle ID zákazníka.</span><span class="sxs-lookup"><span data-stu-id="e0f8d-113">The following example uses the `GroupBy` method to return `SalesOrderHeader` objects that are grouped by customer ID.</span></span> <span data-ttu-id="e0f8d-114">Vrátí se také počet prodejů pro každého zákazníka.</span><span class="sxs-lookup"><span data-stu-id="e0f8d-114">The number of sales for each customer is also returned.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupByCount_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbycount_mq)]
 [!code-vb[DP L2E Examples#GroupByCount_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbycount_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="e0f8d-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e0f8d-115">See also</span></span>

- [<span data-ttu-id="e0f8d-116">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="e0f8d-116">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
