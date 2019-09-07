---
title: 'Příklady syntaxe výrazů dotazů: Seskupování'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2d83d7c0-b3be-4c92-a630-25cd1285de31
ms.openlocfilehash: c9876c72a03f7827ec4b28d78f06ed372460caff
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398454"
---
# <a name="query-expression-syntax-examples-grouping"></a><span data-ttu-id="f2e51-102">Příklady syntaxe výrazů dotazů: Seskupování</span><span class="sxs-lookup"><span data-stu-id="f2e51-102">Query Expression Syntax Examples: Grouping</span></span>
<span data-ttu-id="f2e51-103">Příklady v tomto tématu ukazují, jak použít `GroupBy` metodu pro dotazování [modelu prodeje AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="f2e51-103">The examples in this topic demonstrate how to use the `GroupBy` method to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="f2e51-104">Model prodeje společnosti AdventureWorks použitý v těchto příkladech je sestaven z tabulek Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="f2e51-104">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="f2e51-105">Příklady v tomto tématu používají následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="f2e51-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="f2e51-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="f2e51-106">Example</span></span>  
 <span data-ttu-id="f2e51-107">Následující příklad vrátí `Address` objekty seskupené podle poštovního směrovacího čísla.</span><span class="sxs-lookup"><span data-stu-id="f2e51-107">The following example returns `Address` objects grouped by postal code.</span></span> <span data-ttu-id="f2e51-108">Výsledky se projektují do anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="f2e51-108">The results are projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple3)]
 [!code-vb[DP L2E Examples#GroupBySimple3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple3)]  
  
## <a name="example"></a><span data-ttu-id="f2e51-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="f2e51-109">Example</span></span>  
 <span data-ttu-id="f2e51-110">Následující příklad vrátí `Contact` objekty seskupené podle prvního písmene příjmení kontaktu.</span><span class="sxs-lookup"><span data-stu-id="f2e51-110">The following example returns `Contact` objects grouped by the first letter of the contact's last name.</span></span> <span data-ttu-id="f2e51-111">Výsledky se také řadí podle prvního písmene příjmení a projekt se pak do anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="f2e51-111">The results are also sorted by the first letter of last name and projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple2)]
 [!code-vb[DP L2E Examples#GroupBySimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple2)]  
  
## <a name="example"></a><span data-ttu-id="f2e51-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="f2e51-112">Example</span></span>  
 <span data-ttu-id="f2e51-113">Následující příklad vrátí `SalesOrderHeader` objekty seskupené podle ID zákazníka.</span><span class="sxs-lookup"><span data-stu-id="f2e51-113">The following example returns `SalesOrderHeader` objects grouped by customer ID.</span></span> <span data-ttu-id="f2e51-114">Vrátí se také počet prodejů pro každého zákazníka.</span><span class="sxs-lookup"><span data-stu-id="f2e51-114">The number of sales for each customer is also returned.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupByCount](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbycount)]
 [!code-vb[DP L2E Examples#GroupByCount](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbycount)]  
  
## <a name="see-also"></a><span data-ttu-id="f2e51-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f2e51-115">See also</span></span>

- [<span data-ttu-id="f2e51-116">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="f2e51-116">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
