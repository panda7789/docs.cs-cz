---
title: 'Příklady syntaxe výrazů dotazů: Projekce'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 079926c5-e6b5-4fb9-b4cf-9c63886dd626
ms.openlocfilehash: 52681a4035ef55133c6191e7eac2cab7ed36c8fb
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249336"
---
# <a name="query-expression-syntax-examples-projection"></a><span data-ttu-id="1c8e0-102">Příklady syntaxe výrazů dotazů: Projekce</span><span class="sxs-lookup"><span data-stu-id="1c8e0-102">Query Expression Syntax Examples: Projection</span></span>
<span data-ttu-id="1c8e0-103">Příklady v tomto tématu ukazují, jak použít `Select` metodu `From … From …` a klíčová slova pro dotazování [modelu prodeje AdventureWorks](https://archive.codeplex.com/?p=msftdbprodsamples) pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="1c8e0-103">The examples in this topic demonstrate how to use the `Select` method and the `From … From …` keywords to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using query expression syntax.</span></span> <span data-ttu-id="1c8e0-104">`From … From …`je ekvivalentem `SelectMany` metody na základě dotazu.</span><span class="sxs-lookup"><span data-stu-id="1c8e0-104">`From … From …` is the query based equivalent of the `SelectMany` method.</span></span> <span data-ttu-id="1c8e0-105">Model prodeje společnosti AdventureWorks použitý v těchto příkladech je sestaven z tabulek Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="1c8e0-105">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="1c8e0-106">Příklady v tomto tématu používají následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="1c8e0-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="select"></a><span data-ttu-id="1c8e0-107">Vyberte</span><span class="sxs-lookup"><span data-stu-id="1c8e0-107">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="1c8e0-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="1c8e0-108">Example</span></span>  
 <span data-ttu-id="1c8e0-109">Následující příklad používá <xref:System.Linq.Enumerable.Select%2A> metodu k vrácení všech řádků `Product` z tabulky a zobrazení názvů produktů.</span><span class="sxs-lookup"><span data-stu-id="1c8e0-109">The following example uses the <xref:System.Linq.Enumerable.Select%2A> method to return all the rows from the `Product` table and display the product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP L2E Examples#SelectSimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="example"></a><span data-ttu-id="1c8e0-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="1c8e0-110">Example</span></span>  
 <span data-ttu-id="1c8e0-111">Následující příklad používá <xref:System.Linq.Enumerable.Select%2A> k vrácení posloupnosti pouze názvů produktů.</span><span class="sxs-lookup"><span data-stu-id="1c8e0-111">The following example uses <xref:System.Linq.Enumerable.Select%2A> to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple2)]
 [!code-vb[DP L2E Examples#SelectSimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple2)]  
  
### <a name="example"></a><span data-ttu-id="1c8e0-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="1c8e0-112">Example</span></span>  
 <span data-ttu-id="1c8e0-113">Následující příklad používá <xref:System.Linq.Queryable.Select%2A> metodu pro `Product.Name` projektování vlastností a `Product.ProductID` , do sekvence anonymních typů.</span><span class="sxs-lookup"><span data-stu-id="1c8e0-113">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to project the `Product.Name` and `Product.ProductID` properties into a sequence of anonymous types.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectAnonymousTypes](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectanonymoustypes)]
 [!code-vb[DP L2E Examples#SelectAnonymousTypes](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectanonymoustypes)]  
  
## <a name="from--from--selectmany"></a><span data-ttu-id="1c8e0-114">Z...</span><span class="sxs-lookup"><span data-stu-id="1c8e0-114">From …</span></span> <span data-ttu-id="1c8e0-115">Z...</span><span class="sxs-lookup"><span data-stu-id="1c8e0-115">From …</span></span> <span data-ttu-id="1c8e0-116">Operátor SelectMany</span><span class="sxs-lookup"><span data-stu-id="1c8e0-116">(SelectMany)</span></span>  
  
### <a name="example"></a><span data-ttu-id="1c8e0-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="1c8e0-117">Example</span></span>  
 <span data-ttu-id="1c8e0-118">Následující příklad používá `From … From …` (ekvivalent <xref:System.Linq.Enumerable.SelectMany%2A> metody) pro výběr všech objednávek, kde `TotalDue` je méně než 500,00.</span><span class="sxs-lookup"><span data-stu-id="1c8e0-118">The following example uses `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom)]  
  
### <a name="example"></a><span data-ttu-id="1c8e0-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="1c8e0-119">Example</span></span>  
 <span data-ttu-id="1c8e0-120">Následující příklad používá `From … From …` (ekvivalent <xref:System.Linq.Enumerable.SelectMany%2A> metody) pro výběr všech objednávek, kde byla objednávka vytvořena od 1. října 2002 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="1c8e0-120">The following example uses `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom2)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom2)]  
  
### <a name="example"></a><span data-ttu-id="1c8e0-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="1c8e0-121">Example</span></span>  
 <span data-ttu-id="1c8e0-122">Následující příklad používá `From … From …` (ekvivalent <xref:System.Linq.Enumerable.SelectMany%2A> metody) pro výběr všech objednávek, kde celková objednávka je větší než 10000,00, a používá `From` přiřazení, aby nevyžadovala součet dvakrát.</span><span class="sxs-lookup"><span data-stu-id="1c8e0-122">The following example uses a `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order total is greater than 10000.00 and uses `From` assignment to avoid requesting the total twice.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyFromAssignment](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanyfromassignment)]
 [!code-vb[DP L2E Examples#SelectManyFromAssignment](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanyfromassignment)]  
  
## <a name="see-also"></a><span data-ttu-id="1c8e0-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1c8e0-123">See also</span></span>

- [<span data-ttu-id="1c8e0-124">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="1c8e0-124">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
