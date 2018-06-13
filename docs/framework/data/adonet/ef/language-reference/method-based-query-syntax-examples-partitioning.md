---
title: 'Příklady syntaxe dotazů metoda: vytváření oddílů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b7b64874-c3c8-4bdb-862c-89a168d07827
ms.openlocfilehash: 5e2707463fd3cb9a5761805bc335104486ac44d7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32767567"
---
# <a name="method-based-query-syntax-examples-partitioning"></a><span data-ttu-id="4433c-102">Příklady syntaxe dotazů metoda: vytváření oddílů</span><span class="sxs-lookup"><span data-stu-id="4433c-102">Method-Based Query Syntax Examples: Partitioning</span></span>
<span data-ttu-id="4433c-103">V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Skip%2A>, a <xref:System.Linq.Enumerable.Take%2A> metody k dotazování [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="4433c-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Take%2A> methods to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using query expression syntax.</span></span> <span data-ttu-id="4433c-104">Model prodeje společnosti AdventureWorks použít v těchto příkladech je sestaven z kontaktu, adresu, produktu, SalesOrderHeader a podrobnosti prodejní objednávky tabulky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="4433c-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="4433c-105">V příkladech v tomto tématu použijte následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="4433c-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="skip"></a><span data-ttu-id="4433c-106">Skip</span><span class="sxs-lookup"><span data-stu-id="4433c-106">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="4433c-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="4433c-107">Example</span></span>  
 <span data-ttu-id="4433c-108">Následující příklad používá <xref:System.Linq.Enumerable.Skip%2A> metodu za účelem získání všech ale prvních pět kontakty, obraťte se na tabulky.</span><span class="sxs-lookup"><span data-stu-id="4433c-108">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first five contacts of the Contact table.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipsimple)]
 [!code-vb[DP L2E Examples#SkipSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipsimple)]  
  
### <a name="example"></a><span data-ttu-id="4433c-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="4433c-109">Example</span></span>  
 <span data-ttu-id="4433c-110">Následující příklad používá <xref:System.Linq.Enumerable.Skip%2A> metodu za účelem získání všech ale nejprve dvou adres v Praze.</span><span class="sxs-lookup"><span data-stu-id="4433c-110">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP L2E Examples#SkipNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="4433c-111">Take</span><span class="sxs-lookup"><span data-stu-id="4433c-111">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="4433c-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="4433c-112">Example</span></span>  
 <span data-ttu-id="4433c-113">Následující příklad používá <xref:System.Linq.Enumerable.Take%2A> metoda získat pouze prvních pět kontakty z tabulky Kontakt.</span><span class="sxs-lookup"><span data-stu-id="4433c-113">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get only the first five contacts from the Contact table.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takesimple)]
 [!code-vb[DP L2E Examples#TakeSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takesimple)]  
  
### <a name="example"></a><span data-ttu-id="4433c-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="4433c-114">Example</span></span>  
 <span data-ttu-id="4433c-115">Následující příklad používá <xref:System.Linq.Enumerable.Take%2A> metoda získat prvními třemi adresami v Praze.</span><span class="sxs-lookup"><span data-stu-id="4433c-115">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takenested)]
 [!code-vb[DP L2E Examples#TakeNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="4433c-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="4433c-116">See Also</span></span>  
 [<span data-ttu-id="4433c-117">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="4433c-117">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
