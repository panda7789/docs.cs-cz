---
title: 'Příklady syntaxe výrazů dotazů: Operátory elementů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 32268fe2-de18-4065-8060-f250def83837
ms.openlocfilehash: ddd352fe3bf731c2d436937616d21c0a7257acdc
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398474"
---
# <a name="query-expression-syntax-examples-element-operators"></a><span data-ttu-id="0f462-102">Příklady syntaxe výrazů dotazů: Operátory elementů</span><span class="sxs-lookup"><span data-stu-id="0f462-102">Query Expression Syntax Examples: Element Operators</span></span>
<span data-ttu-id="0f462-103">Příklady v tomto tématu ukazují, jak použít <xref:System.Linq.Enumerable.First%2A> metodu pro dotazování [modelu prodeje společnosti AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="0f462-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using the query expression syntax.</span></span> <span data-ttu-id="0f462-104">Model prodeje společnosti AdventureWorks použitý v těchto příkladech je sestaven z tabulek Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="0f462-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="0f462-105">Příklady v tomto tématu používají následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="0f462-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="0f462-106">První</span><span class="sxs-lookup"><span data-stu-id="0f462-106">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="0f462-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="0f462-107">Example</span></span>  
 <span data-ttu-id="0f462-108">Následující příklad používá <xref:System.Linq.Enumerable.First%2A> metodu k vrácení prvního kontaktu, jehož křestní jméno je "Brooke".</span><span class="sxs-lookup"><span data-stu-id="0f462-108">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to return the first contact whose first name is "Brooke".</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstsimple)]
 [!code-vb[DP L2E Examples#FirstSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="0f462-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0f462-109">See also</span></span>

- [<span data-ttu-id="0f462-110">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="0f462-110">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
