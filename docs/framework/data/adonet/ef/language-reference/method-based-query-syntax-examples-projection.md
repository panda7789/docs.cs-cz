---
title: 'Příklady syntaxe dotazů založených na volání metody: Projekce'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 505491fa-5920-43ce-8a96-c25389e125d8
ms.openlocfilehash: 231fe6072d9a9a561aa91d3cb52fa6963f2d72dd
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250068"
---
# <a name="method-based-query-syntax-examples-projection"></a><span data-ttu-id="d98b9-102">Příklady syntaxe dotazů založených na volání metody: Projekce</span><span class="sxs-lookup"><span data-stu-id="d98b9-102">Method-Based Query Syntax Examples: Projection</span></span>
<span data-ttu-id="d98b9-103">Příklady v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Select%2A> metody a <xref:System.Linq.Enumerable.SelectMany%2A> k dotazování [modelu prodeje společnosti AdventureWorks](https://archive.codeplex.com/?p=msftdbprodsamples) pomocí syntaxe dotazu založeného na metodách.</span><span class="sxs-lookup"><span data-stu-id="d98b9-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using method-based query syntax.</span></span> <span data-ttu-id="d98b9-104">Model prodeje společnosti AdventureWorks použitý v těchto příkladech je sestaven z tabulek Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="d98b9-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="d98b9-105">Příklady v tomto tématu používají následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="d98b9-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="select"></a><span data-ttu-id="d98b9-106">Vyberte</span><span class="sxs-lookup"><span data-stu-id="d98b9-106">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="d98b9-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="d98b9-107">Example</span></span>  
 <span data-ttu-id="d98b9-108">Následující příklad používá <xref:System.Linq.Queryable.Select%2A> metodu pro `Product.Name` projektování vlastností a `Product.ProductID` , do sekvence anonymních typů.</span><span class="sxs-lookup"><span data-stu-id="d98b9-108">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to project the `Product.Name` and `Product.ProductID` properties into a sequence of anonymous types.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
### <a name="example"></a><span data-ttu-id="d98b9-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="d98b9-109">Example</span></span>  
 <span data-ttu-id="d98b9-110">Následující příklad používá <xref:System.Linq.Enumerable.Select%2A> metodu k vrácení posloupnosti pouze názvů produktů.</span><span class="sxs-lookup"><span data-stu-id="d98b9-110">The following example uses the <xref:System.Linq.Enumerable.Select%2A> method to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple2_mq)]
 [!code-vb[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple2_mq)]  
  
## <a name="selectmany"></a><span data-ttu-id="d98b9-111">Operátor SelectMany</span><span class="sxs-lookup"><span data-stu-id="d98b9-111">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="d98b9-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="d98b9-112">Example</span></span>  
 <span data-ttu-id="d98b9-113">Následující příklad používá <xref:System.Linq.Enumerable.SelectMany%2A> metodu pro výběr všech objednávek, kde `TotalDue` je méně než 500,00.</span><span class="sxs-lookup"><span data-stu-id="d98b9-113">The following example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom_mq)]  
  
### <a name="example"></a><span data-ttu-id="d98b9-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="d98b9-114">Example</span></span>  
 <span data-ttu-id="d98b9-115">Následující příklad používá <xref:System.Linq.Enumerable.SelectMany%2A> metodu pro výběr všech objednávek, kde byla objednávka vytvořena od 1. října 2002 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="d98b9-115">The following example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom2_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom2_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="d98b9-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d98b9-116">See also</span></span>

- [<span data-ttu-id="d98b9-117">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="d98b9-117">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
