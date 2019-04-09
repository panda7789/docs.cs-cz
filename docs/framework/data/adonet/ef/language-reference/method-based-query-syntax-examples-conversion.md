---
title: 'Příklady syntaxe dotazů založených na volání metody: Konverze'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 19f66872-d5ab-49f8-969f-e53f9632a13d
ms.openlocfilehash: bf6c889fff2635cd50597e72151c46fbb4d9b97d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150615"
---
# <a name="method-based-query-syntax-examples-conversion"></a><span data-ttu-id="aeb81-102">Příklady syntaxe dotazů založených na volání metody: Konverze</span><span class="sxs-lookup"><span data-stu-id="aeb81-102">Method-Based Query Syntax Examples: Conversion</span></span>
<span data-ttu-id="aeb81-103">Příklady v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A> a <xref:System.Linq.Enumerable.ToList%2A> metody k dotazování [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) pomocí syntaxe dotazů založených na volání metody.</span><span class="sxs-lookup"><span data-stu-id="aeb81-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A> and <xref:System.Linq.Enumerable.ToList%2A> methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using method-based query syntax.</span></span> <span data-ttu-id="aeb81-104">Model prodeje AdventureWorks používá v těchto příkladech je sestaven z tabulky kontaktu, adresa, produktu, SalesOrderHeader a podrobnosti prodejní objednávky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="aeb81-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="aeb81-105">V příkladech v tomto tématu se používá následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="aeb81-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="toarray"></a><span data-ttu-id="aeb81-106">ToArray –</span><span class="sxs-lookup"><span data-stu-id="aeb81-106">ToArray</span></span>  
  
### <a name="example"></a><span data-ttu-id="aeb81-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="aeb81-107">Example</span></span>  
 <span data-ttu-id="aeb81-108">V následujícím příkladu <xref:System.Linq.Enumerable.ToArray%2A> metodu pro vyhodnocení okamžitě sekvence na pole.</span><span class="sxs-lookup"><span data-stu-id="aeb81-108">The following example uses the <xref:System.Linq.Enumerable.ToArray%2A> method to immediately evaluate a sequence into an array.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToArray](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#toarray)]
 [!code-vb[DP L2E Examples#ToArray](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#toarray)]  
  
## <a name="todictionary"></a><span data-ttu-id="aeb81-109">Metody ToDictionary</span><span class="sxs-lookup"><span data-stu-id="aeb81-109">ToDictionary</span></span>  
  
### <a name="example"></a><span data-ttu-id="aeb81-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="aeb81-110">Example</span></span>  
 <span data-ttu-id="aeb81-111">V následujícím příkladu <xref:System.Linq.Enumerable.ToDictionary%2A> metoda okamžitě vyhodnocení sekvenci a související výraz klíče do slovníku.</span><span class="sxs-lookup"><span data-stu-id="aeb81-111">The following example uses the <xref:System.Linq.Enumerable.ToDictionary%2A> method to immediately evaluate a sequence and a related key expression into a dictionary.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#todictionary)]
 [!code-vb[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#todictionary)]  
  
## <a name="tolist"></a><span data-ttu-id="aeb81-112">ToList –</span><span class="sxs-lookup"><span data-stu-id="aeb81-112">ToList</span></span>  
  
### <a name="example"></a><span data-ttu-id="aeb81-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="aeb81-113">Example</span></span>  
 <span data-ttu-id="aeb81-114">V následujícím příkladu <xref:System.Linq.Enumerable.ToList%2A> metodu pro vyhodnocení okamžitě pořadí do <xref:System.Collections.Generic.List%601>, kde `T` je typu <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="aeb81-114">The following example uses the <xref:System.Linq.Enumerable.ToList%2A> method to immediately evaluate a sequence into a <xref:System.Collections.Generic.List%601>, where `T` is of type <xref:System.Data.DataRow>.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToList](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#tolist)]
 [!code-vb[DP L2E Examples#ToList](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#tolist)]  
  
## <a name="see-also"></a><span data-ttu-id="aeb81-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aeb81-115">See also</span></span>

- [<span data-ttu-id="aeb81-116">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="aeb81-116">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
