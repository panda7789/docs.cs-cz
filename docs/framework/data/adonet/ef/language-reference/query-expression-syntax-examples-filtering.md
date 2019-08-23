---
title: 'Příklady syntaxe výrazů dotazů: Filtrování'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c27cb89c-1c1d-4988-9f38-950eda3cb275
ms.openlocfilehash: b9e8cf238d35ec9a6fc9c6d013c4d92b00dced78
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955793"
---
# <a name="query-expression-syntax-examples-filtering"></a><span data-ttu-id="8c6df-102">Příklady syntaxe výrazů dotazů: Filtrování</span><span class="sxs-lookup"><span data-stu-id="8c6df-102">Query Expression Syntax Examples: Filtering</span></span>
<span data-ttu-id="8c6df-103">Příklady v tomto tématu ukazují, jak použít `Where` metody a `Where…Contains` k dotazování [modelu prodeje AdventureWorks](https://archive.codeplex.com/?p=msftdbprodsamples) pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="8c6df-103">The examples in this topic demonstrate how to use the `Where` and `Where…Contains` methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using query expression syntax.</span></span> <span data-ttu-id="8c6df-104">Poznámka, kde...`Contains`</span><span class="sxs-lookup"><span data-stu-id="8c6df-104">Note, Where…`Contains`</span></span> <span data-ttu-id="8c6df-105">nelze použít jako součást [zkompilovaného dotazu](../../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md).</span><span class="sxs-lookup"><span data-stu-id="8c6df-105">cannot be used as a part of a [compiled query](../../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md).</span></span>  
  
 <span data-ttu-id="8c6df-106">Model prodeje společnosti AdventureWorks použitý v těchto příkladech je sestaven z tabulek Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="8c6df-106">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="8c6df-107">Příklady v tomto tématu používají následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="8c6df-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="where"></a><span data-ttu-id="8c6df-108">Where</span><span class="sxs-lookup"><span data-stu-id="8c6df-108">Where</span></span>  
  
### <a name="example"></a><span data-ttu-id="8c6df-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="8c6df-109">Example</span></span>  
 <span data-ttu-id="8c6df-110">Následující příklad vrátí všechny online objednávky.</span><span class="sxs-lookup"><span data-stu-id="8c6df-110">The following example returns all online orders.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where1)]
 [!code-vb[DP L2E Examples#Where1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where1)]  
  
### <a name="example"></a><span data-ttu-id="8c6df-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="8c6df-111">Example</span></span>  
 <span data-ttu-id="8c6df-112">Následující příklad vrátí objednávky, kde je množství objednávky větší než 2 a menší než 6.</span><span class="sxs-lookup"><span data-stu-id="8c6df-112">The following example returns the orders where the order quantity is greater than 2 and less than 6.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where2)]
 [!code-vb[DP L2E Examples#Where2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where2)]  
  
### <a name="example"></a><span data-ttu-id="8c6df-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="8c6df-113">Example</span></span>  
 <span data-ttu-id="8c6df-114">Následující příklad vrátí všechny červené barevné produkty.</span><span class="sxs-lookup"><span data-stu-id="8c6df-114">The following example returns all red colored products.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where3)]
 [!code-vb[DP L2E Examples#Where3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where3)]  
  
### <a name="example"></a><span data-ttu-id="8c6df-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="8c6df-115">Example</span></span>  
 <span data-ttu-id="8c6df-116">Následující příklad používá `Where` metodu k vyhledání objednávek, které byly provedeny po 1. prosinci 2003, a poté `order.SalesOrderDetail` používá navigační vlastnost k získání podrobností pro každou objednávku.</span><span class="sxs-lookup"><span data-stu-id="8c6df-116">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="wherecontains"></a><span data-ttu-id="8c6df-117">Kde... Zobrazí</span><span class="sxs-lookup"><span data-stu-id="8c6df-117">Where…Contains</span></span>  
  
### <a name="example"></a><span data-ttu-id="8c6df-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="8c6df-118">Example</span></span>  
 <span data-ttu-id="8c6df-119">Následující příklad používá pole jako součást `Where…Contains` klauzule pro vyhledání všech produktů, které `ProductModelID` mají, které odpovídají hodnotě v poli.</span><span class="sxs-lookup"><span data-stu-id="8c6df-119">The following example uses an array as part of a `Where…Contains` clause to find all products that have a `ProductModelID` that matches a value in the array.</span></span>  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#1)]
 [!code-vb[DP L2E ArraysAndListsInQueries#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#1)]  
  
> [!NOTE]
> <span data-ttu-id="8c6df-120">Jako `Where…Contains` součást predikátu v klauzuli můžete <xref:System.Array>použít, <xref:System.Collections.Generic.List%601>nebo, nebo kolekci libovolného typu, který implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8c6df-120">As part of the predicate in a `Where…Contains` clause, you can use an <xref:System.Array>, a <xref:System.Collections.Generic.List%601>, or a collection of any type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="8c6df-121">Můžete také deklarovat a inicializovat kolekci v rámci LINQ to Entitiesho dotazu.</span><span class="sxs-lookup"><span data-stu-id="8c6df-121">You can also declare and initialize a collection within a LINQ to Entities query.</span></span> <span data-ttu-id="8c6df-122">Další informace najdete v dalším příkladu.</span><span class="sxs-lookup"><span data-stu-id="8c6df-122">See the next example for more information.</span></span>  
  
### <a name="example"></a><span data-ttu-id="8c6df-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="8c6df-123">Example</span></span>  
 <span data-ttu-id="8c6df-124">Následující příklad deklaruje a inicializuje pole v `Where…Contains` klauzuli pro vyhledání všech produktů, které `ProductModelID` mají nebo `Size` odpovídají hodnotám v polích.</span><span class="sxs-lookup"><span data-stu-id="8c6df-124">The following example declares and initializes arrays in a `Where…Contains` clause to find all products that have a `ProductModelID` or `Size` that match values in the arrays.</span></span>  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#2)]
 [!code-vb[DP L2E ArraysAndListsInQueries#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="8c6df-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c6df-125">See also</span></span>

- [<span data-ttu-id="8c6df-126">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="8c6df-126">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
