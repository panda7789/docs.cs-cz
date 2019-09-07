---
title: 'Příklady syntaxe dotazů založených na volání metody: Dělení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b7b64874-c3c8-4bdb-862c-89a168d07827
ms.openlocfilehash: 168fea5ffe6b8fbb4c08b95578beebbdee171c9f
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398481"
---
# <a name="method-based-query-syntax-examples-partitioning"></a><span data-ttu-id="ce1fd-102">Příklady syntaxe dotazů založených na volání metody: Dělení</span><span class="sxs-lookup"><span data-stu-id="ce1fd-102">Method-Based Query Syntax Examples: Partitioning</span></span>
<span data-ttu-id="ce1fd-103">Příklady v tomto tématu ukazují <xref:System.Linq.Enumerable.Skip%2A>, jak používat metody a <xref:System.Linq.Enumerable.Take%2A> k dotazování [modelu prodeje AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="ce1fd-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Take%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="ce1fd-104">Model prodeje společnosti AdventureWorks použitý v těchto příkladech je sestaven z tabulek Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="ce1fd-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="ce1fd-105">Příklady v tomto tématu používají následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="ce1fd-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="skip"></a><span data-ttu-id="ce1fd-106">Skip</span><span class="sxs-lookup"><span data-stu-id="ce1fd-106">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="ce1fd-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce1fd-107">Example</span></span>  
 <span data-ttu-id="ce1fd-108">Následující příklad používá <xref:System.Linq.Enumerable.Skip%2A> metodu k získání všech, ale prvních pět kontaktů tabulky kontaktů.</span><span class="sxs-lookup"><span data-stu-id="ce1fd-108">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first five contacts of the Contact table.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipsimple)]
 [!code-vb[DP L2E Examples#SkipSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipsimple)]  
  
### <a name="example"></a><span data-ttu-id="ce1fd-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce1fd-109">Example</span></span>  
 <span data-ttu-id="ce1fd-110">Následující příklad používá <xref:System.Linq.Enumerable.Skip%2A> metodu k získání všech kromě prvních dvou adres v Praze.</span><span class="sxs-lookup"><span data-stu-id="ce1fd-110">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP L2E Examples#SkipNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="ce1fd-111">Take</span><span class="sxs-lookup"><span data-stu-id="ce1fd-111">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="ce1fd-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce1fd-112">Example</span></span>  
 <span data-ttu-id="ce1fd-113">Následující příklad používá <xref:System.Linq.Enumerable.Take%2A> metodu k získání pouze prvních pěti kontaktů z tabulky kontaktů.</span><span class="sxs-lookup"><span data-stu-id="ce1fd-113">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get only the first five contacts from the Contact table.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takesimple)]
 [!code-vb[DP L2E Examples#TakeSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takesimple)]  
  
### <a name="example"></a><span data-ttu-id="ce1fd-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce1fd-114">Example</span></span>  
 <span data-ttu-id="ce1fd-115">Následující příklad používá <xref:System.Linq.Enumerable.Take%2A> metodu k získání prvních tří adres v Praze.</span><span class="sxs-lookup"><span data-stu-id="ce1fd-115">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takenested)]
 [!code-vb[DP L2E Examples#TakeNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="ce1fd-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ce1fd-116">See also</span></span>

- [<span data-ttu-id="ce1fd-117">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="ce1fd-117">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
