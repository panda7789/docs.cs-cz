---
title: 'Příklady syntaxe výrazů dotazů: Projekce'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 079926c5-e6b5-4fb9-b4cf-9c63886dd626
ms.openlocfilehash: 9c10c334ae2a10df1f75384ce042781b6f1bd43a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61614411"
---
# <a name="query-expression-syntax-examples-projection"></a><span data-ttu-id="163fd-102">Příklady syntaxe výrazů dotazů: Projekce</span><span class="sxs-lookup"><span data-stu-id="163fd-102">Query Expression Syntax Examples: Projection</span></span>
<span data-ttu-id="163fd-103">Příklady v tomto tématu ukazují, jak používat `Select` metoda a `From … From …` klíčová slova k dotazování [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="163fd-103">The examples in this topic demonstrate how to use the `Select` method and the `From … From …` keywords to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using query expression syntax.</span></span> <span data-ttu-id="163fd-104">`From … From …` je ekvivalentní dotaz založený `SelectMany` metody.</span><span class="sxs-lookup"><span data-stu-id="163fd-104">`From … From …` is the query based equivalent of the `SelectMany` method.</span></span> <span data-ttu-id="163fd-105">Prodeje společnosti AdventureWorks model používaný v těchto příkladech je sestaven z tabulky kontaktu, adresa, produktu, SalesOrderHeader a podrobnosti prodejní objednávky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="163fd-105">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="163fd-106">V příkladech v tomto tématu se používá následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="163fd-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="select"></a><span data-ttu-id="163fd-107">Vyberte</span><span class="sxs-lookup"><span data-stu-id="163fd-107">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="163fd-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="163fd-108">Example</span></span>  
 <span data-ttu-id="163fd-109">V následujícím příkladu <xref:System.Linq.Enumerable.Select%2A> metody, která vrátí všechny řádky z `Product` tabulky a zobrazení názvů produktů.</span><span class="sxs-lookup"><span data-stu-id="163fd-109">The following example uses the <xref:System.Linq.Enumerable.Select%2A> method to return all the rows from the `Product` table and display the product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP L2E Examples#SelectSimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="example"></a><span data-ttu-id="163fd-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="163fd-110">Example</span></span>  
 <span data-ttu-id="163fd-111">Následující příklad používá <xref:System.Linq.Enumerable.Select%2A> k vrácení sekvence pouze názvy produktů.</span><span class="sxs-lookup"><span data-stu-id="163fd-111">The following example uses <xref:System.Linq.Enumerable.Select%2A> to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple2)]
 [!code-vb[DP L2E Examples#SelectSimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple2)]  
  
### <a name="example"></a><span data-ttu-id="163fd-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="163fd-112">Example</span></span>  
 <span data-ttu-id="163fd-113">V následujícím příkladu <xref:System.Linq.Queryable.Select%2A> metoda do projektu `Product.Name` a `Product.ProductID` vlastnosti na sekvenci anonymních typů.</span><span class="sxs-lookup"><span data-stu-id="163fd-113">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to project the `Product.Name` and `Product.ProductID` properties into a sequence of anonymous types.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectAnonymousTypes](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectanonymoustypes)]
 [!code-vb[DP L2E Examples#SelectAnonymousTypes](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectanonymoustypes)]  
  
## <a name="from--from--selectmany"></a><span data-ttu-id="163fd-114">Z...</span><span class="sxs-lookup"><span data-stu-id="163fd-114">From …</span></span> <span data-ttu-id="163fd-115">Z...</span><span class="sxs-lookup"><span data-stu-id="163fd-115">From …</span></span> <span data-ttu-id="163fd-116">(Operátor SelectMany)</span><span class="sxs-lookup"><span data-stu-id="163fd-116">(SelectMany)</span></span>  
  
### <a name="example"></a><span data-ttu-id="163fd-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="163fd-117">Example</span></span>  
 <span data-ttu-id="163fd-118">V následujícím příkladu `From … From …` (ekvivalent <xref:System.Linq.Enumerable.SelectMany%2A> metoda) Chcete-li vybrat všechny objednávky where `TotalDue` je menší než 500,00.</span><span class="sxs-lookup"><span data-stu-id="163fd-118">The following example uses `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom)]  
  
### <a name="example"></a><span data-ttu-id="163fd-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="163fd-119">Example</span></span>  
 <span data-ttu-id="163fd-120">V následujícím příkladu `From … From …` (ekvivalent <xref:System.Linq.Enumerable.SelectMany%2A> metoda) Chcete-li vybrat všechny objednávky, kde byla provedena pořadí 1. října 2002 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="163fd-120">The following example uses `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom2)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom2)]  
  
### <a name="example"></a><span data-ttu-id="163fd-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="163fd-121">Example</span></span>  
 <span data-ttu-id="163fd-122">V následujícím příkladu `From … From …` (ekvivalent <xref:System.Linq.Enumerable.SelectMany%2A> metoda) Chcete-li vybrat všechny objednávky, kde je větší než 10000.00 a používá pořadí celkový počet `From` přiřazení žádosti o celkové dvakrát, aby.</span><span class="sxs-lookup"><span data-stu-id="163fd-122">The following example uses a `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order total is greater than 10000.00 and uses `From` assignment to avoid requesting the total twice.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyFromAssignment](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanyfromassignment)]
 [!code-vb[DP L2E Examples#SelectManyFromAssignment](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanyfromassignment)]  
  
## <a name="see-also"></a><span data-ttu-id="163fd-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="163fd-123">See also</span></span>

- [<span data-ttu-id="163fd-124">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="163fd-124">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
