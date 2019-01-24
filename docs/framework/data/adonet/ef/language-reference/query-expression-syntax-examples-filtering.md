---
title: 'Příklady syntaxe výrazů dotazů: Filtrování'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c27cb89c-1c1d-4988-9f38-950eda3cb275
ms.openlocfilehash: 53087a773f6a639a6f2b421a0b30133927e294f2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54675183"
---
# <a name="query-expression-syntax-examples-filtering"></a><span data-ttu-id="6a991-102">Příklady syntaxe výrazů dotazů: Filtrování</span><span class="sxs-lookup"><span data-stu-id="6a991-102">Query Expression Syntax Examples: Filtering</span></span>
<span data-ttu-id="6a991-103">Příklady v tomto tématu ukazují, jak používat `Where` a `Where…Contains` metody k dotazování [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="6a991-103">The examples in this topic demonstrate how to use the `Where` and `Where…Contains` methods to query the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using query expression syntax.</span></span> <span data-ttu-id="6a991-104">Všimněte si, kde...`Contains`</span><span class="sxs-lookup"><span data-stu-id="6a991-104">Note, Where…`Contains`</span></span> <span data-ttu-id="6a991-105">nelze použít jako součást [zkompilován dotaz](../../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md).</span><span class="sxs-lookup"><span data-stu-id="6a991-105">cannot be used as a part of a [compiled query](../../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md).</span></span>  
  
 <span data-ttu-id="6a991-106">Prodeje společnosti AdventureWorks model používaný v těchto příkladech je sestaven z tabulky kontaktu, adresa, produktu, SalesOrderHeader a podrobnosti prodejní objednávky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="6a991-106">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="6a991-107">V příkladech v tomto tématu se používá následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="6a991-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="where"></a><span data-ttu-id="6a991-108">Where</span><span class="sxs-lookup"><span data-stu-id="6a991-108">Where</span></span>  
  
### <a name="example"></a><span data-ttu-id="6a991-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="6a991-109">Example</span></span>  
 <span data-ttu-id="6a991-110">Následující příklad vrátí všechny online objednávky.</span><span class="sxs-lookup"><span data-stu-id="6a991-110">The following example returns all online orders.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where1)]
 [!code-vb[DP L2E Examples#Where1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where1)]  
  
### <a name="example"></a><span data-ttu-id="6a991-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="6a991-111">Example</span></span>  
 <span data-ttu-id="6a991-112">Následující příklad vrátí objednávky, kde je větší než 2 a méně než 6 množství objednávky.</span><span class="sxs-lookup"><span data-stu-id="6a991-112">The following example returns the orders where the order quantity is greater than 2 and less than 6.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where2)]
 [!code-vb[DP L2E Examples#Where2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where2)]  
  
### <a name="example"></a><span data-ttu-id="6a991-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="6a991-113">Example</span></span>  
 <span data-ttu-id="6a991-114">Následující příklad vrátí všechny produkty red barevný.</span><span class="sxs-lookup"><span data-stu-id="6a991-114">The following example returns all red colored products.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where3)]
 [!code-vb[DP L2E Examples#Where3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where3)]  
  
### <a name="example"></a><span data-ttu-id="6a991-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="6a991-115">Example</span></span>  
 <span data-ttu-id="6a991-116">V následujícím příkladu `Where` metody k vyhledání objednávky, které byly provedeny po 1. prosince 2003 a pak použije `order.SalesOrderDetail` vlastnosti navigace použít k získání podrobností každé objednávky.</span><span class="sxs-lookup"><span data-stu-id="6a991-116">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="wherecontains"></a><span data-ttu-id="6a991-117">Kde... Obsahuje</span><span class="sxs-lookup"><span data-stu-id="6a991-117">Where…Contains</span></span>  
  
### <a name="example"></a><span data-ttu-id="6a991-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="6a991-118">Example</span></span>  
 <span data-ttu-id="6a991-119">Následující příklad používá jako součást pole `Where…Contains` klauzule k vyhledání všech produktů, které mají `ProductModelID` odpovídající hodnotu v poli.</span><span class="sxs-lookup"><span data-stu-id="6a991-119">The following example uses an array as part of a `Where…Contains` clause to find all products that have a `ProductModelID` that matches a value in the array.</span></span>  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#1)]
 [!code-vb[DP L2E ArraysAndListsInQueries#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#1)]  
  
> [!NOTE]
>  <span data-ttu-id="6a991-120">Jako součást predikátu v `Where…Contains` klauzule, můžete použít <xref:System.Array>, <xref:System.Collections.Generic.List%601>, nebo libovolný typ, který implementuje kolekci <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6a991-120">As part of the predicate in a `Where…Contains` clause, you can use an <xref:System.Array>, a <xref:System.Collections.Generic.List%601>, or a collection of any type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="6a991-121">Můžete také deklarovat a inicializovat kolekci dotazu LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="6a991-121">You can also declare and initialize a collection within a LINQ to Entities query.</span></span> <span data-ttu-id="6a991-122">Podívejte se na další příklad pro další informace.</span><span class="sxs-lookup"><span data-stu-id="6a991-122">See the next example for more information.</span></span>  
  
### <a name="example"></a><span data-ttu-id="6a991-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="6a991-123">Example</span></span>  
 <span data-ttu-id="6a991-124">Následující příklad deklaruje a inicializuje pole ve `Where…Contains` klauzule k vyhledání všech produktů, které mají `ProductModelID` nebo `Size` odpovídající hodnoty v polích.</span><span class="sxs-lookup"><span data-stu-id="6a991-124">The following example declares and initializes arrays in a `Where…Contains` clause to find all products that have a `ProductModelID` or `Size` that match values in the arrays.</span></span>  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#2)]
 [!code-vb[DP L2E ArraysAndListsInQueries#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="6a991-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a991-125">See also</span></span>
- [<span data-ttu-id="6a991-126">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="6a991-126">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
