---
title: 'Příklady syntaxe dotazů metoda: filtrování'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e40e314c-eb30-4f44-a054-41e511e35832
ms.openlocfilehash: f4e9b6df45e13680a428d1524eaf1a1b9315185a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="method-based-query-syntax-examples-filtering"></a><span data-ttu-id="884d6-102">Příklady syntaxe dotazů metoda: filtrování</span><span class="sxs-lookup"><span data-stu-id="884d6-102">Method-Based Query Syntax Examples: Filtering</span></span>
<span data-ttu-id="884d6-103">V příkladech v tomto tématu ukazují, jak používat `Where` a `Where…Contains` metody k dotazování [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) pomocí syntaxe dotazu na základě metod.</span><span class="sxs-lookup"><span data-stu-id="884d6-103">The examples in this topic demonstrate how to use the `Where` and `Where…Contains` methods to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="884d6-104">Všimněte si, kam...`Contains`</span><span class="sxs-lookup"><span data-stu-id="884d6-104">Note, Where…`Contains`</span></span> <span data-ttu-id="884d6-105">nelze použít jako součást [zkompilován dotaz](../../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md).</span><span class="sxs-lookup"><span data-stu-id="884d6-105">cannot be used as a part of a [compiled query](../../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md).</span></span>  
  
 <span data-ttu-id="884d6-106">Model prodeje společnosti AdventureWorks použít v těchto příkladech je sestaven z kontaktu, adresu, produktu, SalesOrderHeader a podrobnosti prodejní objednávky tabulky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="884d6-106">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="884d6-107">V příkladech v tomto tématu použijte následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="884d6-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="where"></a><span data-ttu-id="884d6-108">Where</span><span class="sxs-lookup"><span data-stu-id="884d6-108">Where</span></span>  
  
### <a name="example"></a><span data-ttu-id="884d6-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="884d6-109">Example</span></span>  
 <span data-ttu-id="884d6-110">Následující příklad vrátí všechny online objednávky.</span><span class="sxs-lookup"><span data-stu-id="884d6-110">The following example returns all online orders.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where1_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where1_mq)]
 [!code-vb[DP L2E Examples#Where1_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where1_mq)]  
  
### <a name="example"></a><span data-ttu-id="884d6-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="884d6-111">Example</span></span>  
 <span data-ttu-id="884d6-112">Následující příklad vrátí objednávky, kde je větší než 2 a menší než 6 množství objednávky.</span><span class="sxs-lookup"><span data-stu-id="884d6-112">The following example returns the orders where the order quantity is greater than 2 and less than 6.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where2_mq)]
 [!code-vb[DP L2E Examples#Where2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where2_mq)]  
  
### <a name="example"></a><span data-ttu-id="884d6-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="884d6-113">Example</span></span>  
 <span data-ttu-id="884d6-114">Následující příklad vrátí všechny red barevnou produkty.</span><span class="sxs-lookup"><span data-stu-id="884d6-114">The following example returns all red colored products.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where3_mq)]
 [!code-vb[DP L2E Examples#Where3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where3_mq)]  
  
### <a name="example"></a><span data-ttu-id="884d6-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="884d6-115">Example</span></span>  
 <span data-ttu-id="884d6-116">Následující příklad používá `Where` metody k vyhledání objednávky, které byly provedeny po 1. prosince 2003 a pak používá `order.SalesOrderDetail` navigační vlastnost pro získání podrobností o pro každé pořadí.</span><span class="sxs-lookup"><span data-stu-id="884d6-116">The following example uses the `Where` method to find orders that were made after December 1, 2003 and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty_mq)]
 [!code-vb[DP L2E Examples#WhereNavProperty_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty_mq)]  
  
## <a name="wherecontains"></a><span data-ttu-id="884d6-117">Kde... Obsahuje</span><span class="sxs-lookup"><span data-stu-id="884d6-117">Where…Contains</span></span>  
  
### <a name="example"></a><span data-ttu-id="884d6-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="884d6-118">Example</span></span>  
 <span data-ttu-id="884d6-119">Následující příklad používá jako součást pole `Where…Contains` klauzule najít všechny produkty, které mají `ProductModelID` odpovídající hodnotu v poli.</span><span class="sxs-lookup"><span data-stu-id="884d6-119">The following example uses an array as part of a `Where…Contains` clause to find all products that have a `ProductModelID` that matches a value in the array.</span></span>  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#3)]
 [!code-vb[DP L2E ArraysAndListsInQueries#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#3)]  
  
> [!NOTE]
>  <span data-ttu-id="884d6-120">V rámci predikátu v `Where…Contains` klauzule, můžete použít <xref:System.Array>, <xref:System.Collections.Generic.List%601>, nebo kolekci žádný typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="884d6-120">As part of the predicate in a `Where…Contains` clause, you can use an <xref:System.Array>, a <xref:System.Collections.Generic.List%601>, or a collection of any type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="884d6-121">Můžete také deklarovat a inicializuje kolekci v dotazu LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="884d6-121">You can also declare and initialize a collection within a LINQ to Entities query.</span></span> <span data-ttu-id="884d6-122">Podívejte se na další příklad další informace.</span><span class="sxs-lookup"><span data-stu-id="884d6-122">See the next example for more information.</span></span>  
  
### <a name="example"></a><span data-ttu-id="884d6-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="884d6-123">Example</span></span>  
 <span data-ttu-id="884d6-124">Následující příklad deklaruje a inicializuje pole v `Where…Contains` klauzule najít všechny produkty, které mají `ProductModelID` nebo `Size` odpovídající hodnotu v poli.</span><span class="sxs-lookup"><span data-stu-id="884d6-124">The following example declares and initializes arrays in a `Where…Contains` clause to find all products that have a `ProductModelID` or a `Size` that matches a value in the arrays.</span></span>  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#4)]
 [!code-vb[DP L2E ArraysAndListsInQueries#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="884d6-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="884d6-125">See Also</span></span>  
 [<span data-ttu-id="884d6-126">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="884d6-126">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
