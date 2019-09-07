---
title: 'Příklady syntaxe výrazů dotazů: Dělení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e41aed0-3be9-4f75-98de-860a85552a3c
ms.openlocfilehash: b845564c02b55b8729efc893d7eecc48bd60f710
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398552"
---
# <a name="query-expression-syntax-examples-partitioning"></a><span data-ttu-id="f338f-102">Příklady syntaxe výrazů dotazů: Dělení</span><span class="sxs-lookup"><span data-stu-id="f338f-102">Query Expression Syntax Examples: Partitioning</span></span>
<span data-ttu-id="f338f-103">Příklady v tomto tématu ukazují, jak použít <xref:System.Linq.Enumerable.Skip%2A> metody a <xref:System.Linq.Enumerable.Take%2A> k dotazování [modelu prodeje AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="f338f-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="f338f-104">Model prodeje společnosti AdventureWorks použitý v těchto příkladech je sestaven z tabulek Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="f338f-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="f338f-105">Příklady v tomto tématu používají následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="f338f-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="skip"></a><span data-ttu-id="f338f-106">Skip</span><span class="sxs-lookup"><span data-stu-id="f338f-106">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="f338f-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="f338f-107">Example</span></span>  
 <span data-ttu-id="f338f-108">Následující příklad používá <xref:System.Linq.Enumerable.Skip%2A> metodu k získání všech kromě prvních dvou adres v Praze.</span><span class="sxs-lookup"><span data-stu-id="f338f-108">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP L2E Examples#SkipNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="f338f-109">Take</span><span class="sxs-lookup"><span data-stu-id="f338f-109">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="f338f-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="f338f-110">Example</span></span>  
 <span data-ttu-id="f338f-111">Následující příklad používá <xref:System.Linq.Enumerable.Take%2A> metodu k získání prvních tří adres v Praze.</span><span class="sxs-lookup"><span data-stu-id="f338f-111">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takenested)]
 [!code-vb[DP L2E Examples#TakeNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="f338f-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f338f-112">See also</span></span>

- [<span data-ttu-id="f338f-113">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="f338f-113">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
