---
title: 'Příklady syntaxe výrazů dotazů: Operátory elementů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 32268fe2-de18-4065-8060-f250def83837
ms.openlocfilehash: 1b73e22e79c665763390561a1e48b2583ec6cd27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61614437"
---
# <a name="query-expression-syntax-examples-element-operators"></a><span data-ttu-id="99c6f-102">Příklady syntaxe výrazů dotazů: Operátory elementů</span><span class="sxs-lookup"><span data-stu-id="99c6f-102">Query Expression Syntax Examples: Element Operators</span></span>
<span data-ttu-id="99c6f-103">Příklady v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.First%2A> metodu dotazu [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="99c6f-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using the query expression syntax.</span></span> <span data-ttu-id="99c6f-104">Model prodeje AdventureWorks používá v těchto příkladech je sestaven z tabulky kontaktu, adresa, produktu, SalesOrderHeader a podrobnosti prodejní objednávky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="99c6f-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="99c6f-105">V příkladech v tomto tématu se používá následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="99c6f-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="99c6f-106">první</span><span class="sxs-lookup"><span data-stu-id="99c6f-106">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="99c6f-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="99c6f-107">Example</span></span>  
 <span data-ttu-id="99c6f-108">V následujícím příkladu <xref:System.Linq.Enumerable.First%2A> metoda vrátí první kontakt jejichž křestní jméno je "Brooke".</span><span class="sxs-lookup"><span data-stu-id="99c6f-108">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to return the first contact whose first name is "Brooke".</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstsimple)]
 [!code-vb[DP L2E Examples#FirstSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="99c6f-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="99c6f-109">See also</span></span>

- [<span data-ttu-id="99c6f-110">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="99c6f-110">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
