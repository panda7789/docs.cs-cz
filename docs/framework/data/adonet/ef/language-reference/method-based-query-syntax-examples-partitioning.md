---
title: 'Příklady syntaxe dotazů založených na volání metody: Dělení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b7b64874-c3c8-4bdb-862c-89a168d07827
ms.openlocfilehash: eaf98dc21499817446efca2f10edf7faea15761c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141655"
---
# <a name="method-based-query-syntax-examples-partitioning"></a><span data-ttu-id="05fa0-102">Příklady syntaxe dotazů založených na volání metody: Dělení</span><span class="sxs-lookup"><span data-stu-id="05fa0-102">Method-Based Query Syntax Examples: Partitioning</span></span>
<span data-ttu-id="05fa0-103">Příklady v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Skip%2A>, a <xref:System.Linq.Enumerable.Take%2A> metody k dotazování [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="05fa0-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Take%2A> methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using query expression syntax.</span></span> <span data-ttu-id="05fa0-104">Model prodeje AdventureWorks používá v těchto příkladech je sestaven z tabulky kontaktu, adresa, produktu, SalesOrderHeader a podrobnosti prodejní objednávky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="05fa0-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="05fa0-105">V příkladech v tomto tématu se používá následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="05fa0-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="skip"></a><span data-ttu-id="05fa0-106">Skip</span><span class="sxs-lookup"><span data-stu-id="05fa0-106">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="05fa0-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="05fa0-107">Example</span></span>  
 <span data-ttu-id="05fa0-108">V následujícím příkladu <xref:System.Linq.Enumerable.Skip%2A> metodu k získání všech, ale prvních pět kontakty tabulky Kontakt.</span><span class="sxs-lookup"><span data-stu-id="05fa0-108">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first five contacts of the Contact table.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipsimple)]
 [!code-vb[DP L2E Examples#SkipSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipsimple)]  
  
### <a name="example"></a><span data-ttu-id="05fa0-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="05fa0-109">Example</span></span>  
 <span data-ttu-id="05fa0-110">V následujícím příkladu <xref:System.Linq.Enumerable.Skip%2A> metodu k získání všech, ale prvních dvou adres v Praze.</span><span class="sxs-lookup"><span data-stu-id="05fa0-110">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP L2E Examples#SkipNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="05fa0-111">Take</span><span class="sxs-lookup"><span data-stu-id="05fa0-111">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="05fa0-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="05fa0-112">Example</span></span>  
 <span data-ttu-id="05fa0-113">V následujícím příkladu <xref:System.Linq.Enumerable.Take%2A> metodu k získání pouze prvních pět kontakty z tabulky Kontakt.</span><span class="sxs-lookup"><span data-stu-id="05fa0-113">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get only the first five contacts from the Contact table.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takesimple)]
 [!code-vb[DP L2E Examples#TakeSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takesimple)]  
  
### <a name="example"></a><span data-ttu-id="05fa0-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="05fa0-114">Example</span></span>  
 <span data-ttu-id="05fa0-115">V následujícím příkladu <xref:System.Linq.Enumerable.Take%2A> metodu k získání prvními třemi adresami v Seattlu.</span><span class="sxs-lookup"><span data-stu-id="05fa0-115">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takenested)]
 [!code-vb[DP L2E Examples#TakeNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="05fa0-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="05fa0-116">See also</span></span>

- [<span data-ttu-id="05fa0-117">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="05fa0-117">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
