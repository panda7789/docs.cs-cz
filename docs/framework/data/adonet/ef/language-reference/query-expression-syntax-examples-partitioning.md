---
title: 'Příklady syntaxe výrazů dotazů: Dělení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e41aed0-3be9-4f75-98de-860a85552a3c
ms.openlocfilehash: c8bfe57e6f49f382885507f7aa7093eff7720c2c
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/07/2019
ms.locfileid: "55827952"
---
# <a name="query-expression-syntax-examples-partitioning"></a><span data-ttu-id="9a89e-102">Příklady syntaxe výrazů dotazů: Dělení</span><span class="sxs-lookup"><span data-stu-id="9a89e-102">Query Expression Syntax Examples: Partitioning</span></span>
<span data-ttu-id="9a89e-103">Příklady v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Skip%2A> a <xref:System.Linq.Enumerable.Take%2A> metody k dotazování [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="9a89e-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using query expression syntax.</span></span> <span data-ttu-id="9a89e-104">Model prodeje AdventureWorks používá v těchto příkladech je sestaven z tabulky kontaktu, adresa, produktu, SalesOrderHeader a podrobnosti prodejní objednávky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="9a89e-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="9a89e-105">V příkladech v tomto tématu se používá následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="9a89e-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="skip"></a><span data-ttu-id="9a89e-106">Skip</span><span class="sxs-lookup"><span data-stu-id="9a89e-106">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="9a89e-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="9a89e-107">Example</span></span>  
 <span data-ttu-id="9a89e-108">V následujícím příkladu <xref:System.Linq.Enumerable.Skip%2A> metodu k získání všech, ale prvních dvou adres v Praze.</span><span class="sxs-lookup"><span data-stu-id="9a89e-108">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP L2E Examples#SkipNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="9a89e-109">Take</span><span class="sxs-lookup"><span data-stu-id="9a89e-109">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="9a89e-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="9a89e-110">Example</span></span>  
 <span data-ttu-id="9a89e-111">V následujícím příkladu <xref:System.Linq.Enumerable.Take%2A> metodu k získání prvními třemi adresami v Seattlu.</span><span class="sxs-lookup"><span data-stu-id="9a89e-111">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takenested)]
 [!code-vb[DP L2E Examples#TakeNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="9a89e-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9a89e-112">See also</span></span>
- [<span data-ttu-id="9a89e-113">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="9a89e-113">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
