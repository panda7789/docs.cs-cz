---
title: 'Příklady syntaxe výrazů dotazů: Dělení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e41aed0-3be9-4f75-98de-860a85552a3c
ms.openlocfilehash: e205a50b70a29d056af23ba64eb630b50e304ecb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59165279"
---
# <a name="query-expression-syntax-examples-partitioning"></a><span data-ttu-id="6ad18-102">Příklady syntaxe výrazů dotazů: Dělení</span><span class="sxs-lookup"><span data-stu-id="6ad18-102">Query Expression Syntax Examples: Partitioning</span></span>
<span data-ttu-id="6ad18-103">Příklady v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Skip%2A> a <xref:System.Linq.Enumerable.Take%2A> metody k dotazování [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="6ad18-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using query expression syntax.</span></span> <span data-ttu-id="6ad18-104">Model prodeje AdventureWorks používá v těchto příkladech je sestaven z tabulky kontaktu, adresa, produktu, SalesOrderHeader a podrobnosti prodejní objednávky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="6ad18-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="6ad18-105">V příkladech v tomto tématu se používá následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="6ad18-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="skip"></a><span data-ttu-id="6ad18-106">Skip</span><span class="sxs-lookup"><span data-stu-id="6ad18-106">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="6ad18-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ad18-107">Example</span></span>  
 <span data-ttu-id="6ad18-108">V následujícím příkladu <xref:System.Linq.Enumerable.Skip%2A> metodu k získání všech, ale prvních dvou adres v Praze.</span><span class="sxs-lookup"><span data-stu-id="6ad18-108">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP L2E Examples#SkipNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="6ad18-109">Take</span><span class="sxs-lookup"><span data-stu-id="6ad18-109">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="6ad18-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ad18-110">Example</span></span>  
 <span data-ttu-id="6ad18-111">V následujícím příkladu <xref:System.Linq.Enumerable.Take%2A> metodu k získání prvními třemi adresami v Seattlu.</span><span class="sxs-lookup"><span data-stu-id="6ad18-111">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takenested)]
 [!code-vb[DP L2E Examples#TakeNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="6ad18-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6ad18-112">See also</span></span>

- [<span data-ttu-id="6ad18-113">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="6ad18-113">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
