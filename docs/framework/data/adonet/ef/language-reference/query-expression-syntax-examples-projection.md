---
title: "Příklady syntaxe výrazu dotazu: projekce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 079926c5-e6b5-4fb9-b4cf-9c63886dd626
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a8339b02beb340709f4000a2373a4ce935fb6119
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="query-expression-syntax-examples-projection"></a><span data-ttu-id="e4a2f-102">Příklady syntaxe výrazu dotazu: projekce</span><span class="sxs-lookup"><span data-stu-id="e4a2f-102">Query Expression Syntax Examples: Projection</span></span>
<span data-ttu-id="e4a2f-103">V příkladech v tomto tématu ukazují, jak používat `Select` metoda a `From … From …` klíčová slova se dotázat [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="e4a2f-103">The examples in this topic demonstrate how to use the `Select` method and the `From … From …` keywords to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) using query expression syntax.</span></span> <span data-ttu-id="e4a2f-104">`From … From …`je ekvivalentní dotaz založený `SelectMany` metoda.</span><span class="sxs-lookup"><span data-stu-id="e4a2f-104">`From … From …` is the query based equivalent of the `SelectMany` method.</span></span> <span data-ttu-id="e4a2f-105">Model prodeje společnosti AdventureWorks použít v těchto příkladech je sestaven z kontaktu, adresu, produktu, SalesOrderHeader a podrobnosti prodejní objednávky tabulky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e4a2f-105">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="e4a2f-106">V příkladech v tomto tématu použijte následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="e4a2f-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="select"></a><span data-ttu-id="e4a2f-107">Vyberte</span><span class="sxs-lookup"><span data-stu-id="e4a2f-107">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="e4a2f-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="e4a2f-108">Example</span></span>  
 <span data-ttu-id="e4a2f-109">Následující příklad používá <xref:System.Linq.Enumerable.Select%2A> metody, která vrátí všechny řádky z `Product` tabulky a zobrazení názvy produktů.</span><span class="sxs-lookup"><span data-stu-id="e4a2f-109">The following example uses the <xref:System.Linq.Enumerable.Select%2A> method to return all the rows from the `Product` table and display the product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP L2E Examples#SelectSimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="example"></a><span data-ttu-id="e4a2f-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="e4a2f-110">Example</span></span>  
 <span data-ttu-id="e4a2f-111">Následující příklad používá <xref:System.Linq.Enumerable.Select%2A> vrátit posloupnost pouze názvy produktů.</span><span class="sxs-lookup"><span data-stu-id="e4a2f-111">The following example uses <xref:System.Linq.Enumerable.Select%2A> to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple2)]
 [!code-vb[DP L2E Examples#SelectSimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple2)]  
  
### <a name="example"></a><span data-ttu-id="e4a2f-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="e4a2f-112">Example</span></span>  
 <span data-ttu-id="e4a2f-113">Následující příklad používá <xref:System.Linq.Queryable.Select%2A> metoda do projektu `Product.Name` a `Product.ProductID` vlastnosti do posloupnost anonymní typy.</span><span class="sxs-lookup"><span data-stu-id="e4a2f-113">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to project the `Product.Name` and `Product.ProductID` properties into a sequence of anonymous types.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectAnonymousTypes](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectanonymoustypes)]
 [!code-vb[DP L2E Examples#SelectAnonymousTypes](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectanonymoustypes)]  
  
## <a name="from--from--selectmany"></a><span data-ttu-id="e4a2f-114">Z...</span><span class="sxs-lookup"><span data-stu-id="e4a2f-114">From …</span></span> <span data-ttu-id="e4a2f-115">Z...</span><span class="sxs-lookup"><span data-stu-id="e4a2f-115">From …</span></span> <span data-ttu-id="e4a2f-116">Označit (více)</span><span class="sxs-lookup"><span data-stu-id="e4a2f-116">(SelectMany)</span></span>  
  
### <a name="example"></a><span data-ttu-id="e4a2f-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="e4a2f-117">Example</span></span>  
 <span data-ttu-id="e4a2f-118">Následující příklad používá `From … From …` (ekvivalent <xref:System.Linq.Enumerable.SelectMany%2A> metoda) Chcete-li vybrat všechny řadí kde `TotalDue` je menší než 500,00.</span><span class="sxs-lookup"><span data-stu-id="e4a2f-118">The following example uses `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom)]  
  
### <a name="example"></a><span data-ttu-id="e4a2f-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="e4a2f-119">Example</span></span>  
 <span data-ttu-id="e4a2f-120">Následující příklad používá `From … From …` (ekvivalent <xref:System.Linq.Enumerable.SelectMany%2A> metoda) Chcete-li vybrat všechny objednávky, kde byla provedena pořadí na 1. října 2002 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="e4a2f-120">The following example uses `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom2)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom2)]  
  
### <a name="example"></a><span data-ttu-id="e4a2f-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="e4a2f-121">Example</span></span>  
 <span data-ttu-id="e4a2f-122">Následující příklad používá `From … From …` (ekvivalent <xref:System.Linq.Enumerable.SelectMany%2A> metoda) vyberete všechny objednávky, kde pořadí celkový počet je větší než 10000.00 a používá `From` přiřazení, aby se zabránilo požaduje celkový počet dvakrát.</span><span class="sxs-lookup"><span data-stu-id="e4a2f-122">The following example uses a `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order total is greater than 10000.00 and uses `From` assignment to avoid requesting the total twice.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyFromAssignment](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanyfromassignment)]
 [!code-vb[DP L2E Examples#SelectManyFromAssignment](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanyfromassignment)]  
  
## <a name="see-also"></a><span data-ttu-id="e4a2f-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="e4a2f-123">See Also</span></span>  
 [<span data-ttu-id="e4a2f-124">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="e4a2f-124">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
