---
title: 'Příklady syntaxe dotazů založených na volání metody: Konverze'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 19f66872-d5ab-49f8-969f-e53f9632a13d
ms.openlocfilehash: a78588cb4bd09f8a8a8ce8ed4a60dd45fce1d386
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397484"
---
# <a name="method-based-query-syntax-examples-conversion"></a><span data-ttu-id="62036-102">Příklady syntaxe dotazů založených na volání metody: Konverze</span><span class="sxs-lookup"><span data-stu-id="62036-102">Method-Based Query Syntax Examples: Conversion</span></span>
<span data-ttu-id="62036-103">Příklady v tomto tématu <xref:System.Linq.Enumerable.ToArray%2A>ukazují, <xref:System.Linq.Enumerable.ToDictionary%2A> jak používat metody a <xref:System.Linq.Enumerable.ToList%2A> k dotazování [modelu prodeje společnosti AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) pomocí syntaxe dotazu založeného na metodách.</span><span class="sxs-lookup"><span data-stu-id="62036-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A> and <xref:System.Linq.Enumerable.ToList%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="62036-104">Model prodeje společnosti AdventureWorks použitý v těchto příkladech je sestaven z tabulek Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="62036-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="62036-105">Příklady v tomto tématu používají následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="62036-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="toarray"></a><span data-ttu-id="62036-106">ToArray –</span><span class="sxs-lookup"><span data-stu-id="62036-106">ToArray</span></span>  
  
### <a name="example"></a><span data-ttu-id="62036-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="62036-107">Example</span></span>  
 <span data-ttu-id="62036-108">Následující příklad používá <xref:System.Linq.Enumerable.ToArray%2A> metodu k okamžitému vyhodnocení sekvence do pole.</span><span class="sxs-lookup"><span data-stu-id="62036-108">The following example uses the <xref:System.Linq.Enumerable.ToArray%2A> method to immediately evaluate a sequence into an array.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToArray](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#toarray)]
 [!code-vb[DP L2E Examples#ToArray](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#toarray)]  
  
## <a name="todictionary"></a><span data-ttu-id="62036-109">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="62036-109">ToDictionary</span></span>  
  
### <a name="example"></a><span data-ttu-id="62036-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="62036-110">Example</span></span>  
 <span data-ttu-id="62036-111">Následující příklad používá <xref:System.Linq.Enumerable.ToDictionary%2A> metodu k okamžitému vyhodnocení sekvence a souvisejícího klíčového výrazu do slovníku.</span><span class="sxs-lookup"><span data-stu-id="62036-111">The following example uses the <xref:System.Linq.Enumerable.ToDictionary%2A> method to immediately evaluate a sequence and a related key expression into a dictionary.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#todictionary)]
 [!code-vb[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#todictionary)]  
  
## <a name="tolist"></a><span data-ttu-id="62036-112">ToList –</span><span class="sxs-lookup"><span data-stu-id="62036-112">ToList</span></span>  
  
### <a name="example"></a><span data-ttu-id="62036-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="62036-113">Example</span></span>  
 <span data-ttu-id="62036-114">Následující příklad používá <xref:System.Linq.Enumerable.ToList%2A> metodu pro okamžité vyhodnocení sekvence <xref:System.Collections.Generic.List%601>do, kde `T` je typu <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="62036-114">The following example uses the <xref:System.Linq.Enumerable.ToList%2A> method to immediately evaluate a sequence into a <xref:System.Collections.Generic.List%601>, where `T` is of type <xref:System.Data.DataRow>.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToList](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#tolist)]
 [!code-vb[DP L2E Examples#ToList](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#tolist)]  
  
## <a name="see-also"></a><span data-ttu-id="62036-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="62036-115">See also</span></span>

- [<span data-ttu-id="62036-116">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="62036-116">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
