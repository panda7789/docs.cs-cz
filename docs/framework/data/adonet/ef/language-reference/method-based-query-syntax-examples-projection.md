---
title: 'Příklady syntaxe dotazů založených na volání metody: Projekce'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 505491fa-5920-43ce-8a96-c25389e125d8
ms.openlocfilehash: 3a9203a51bbb61b32300919656084d7d95ddfa79
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397312"
---
# <a name="method-based-query-syntax-examples-projection"></a><span data-ttu-id="b91f8-102">Příklady syntaxe dotazů založených na volání metody: Projekce</span><span class="sxs-lookup"><span data-stu-id="b91f8-102">Method-Based Query Syntax Examples: Projection</span></span>
<span data-ttu-id="b91f8-103">Příklady v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Select%2A> metody a <xref:System.Linq.Enumerable.SelectMany%2A> k dotazování [modelu prodeje společnosti AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) pomocí syntaxe dotazu založeného na metodách.</span><span class="sxs-lookup"><span data-stu-id="b91f8-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="b91f8-104">Model prodeje společnosti AdventureWorks použitý v těchto příkladech je sestaven z tabulek Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="b91f8-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="b91f8-105">Příklady v tomto tématu používají následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="b91f8-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="select"></a><span data-ttu-id="b91f8-106">Vyberte</span><span class="sxs-lookup"><span data-stu-id="b91f8-106">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="b91f8-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="b91f8-107">Example</span></span>  
 <span data-ttu-id="b91f8-108">Následující příklad používá <xref:System.Linq.Queryable.Select%2A> metodu pro `Product.Name` projektování vlastností a `Product.ProductID` , do sekvence anonymních typů.</span><span class="sxs-lookup"><span data-stu-id="b91f8-108">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to project the `Product.Name` and `Product.ProductID` properties into a sequence of anonymous types.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
### <a name="example"></a><span data-ttu-id="b91f8-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="b91f8-109">Example</span></span>  
 <span data-ttu-id="b91f8-110">Následující příklad používá <xref:System.Linq.Enumerable.Select%2A> metodu k vrácení posloupnosti pouze názvů produktů.</span><span class="sxs-lookup"><span data-stu-id="b91f8-110">The following example uses the <xref:System.Linq.Enumerable.Select%2A> method to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple2_mq)]
 [!code-vb[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple2_mq)]  
  
## <a name="selectmany"></a><span data-ttu-id="b91f8-111">Operátor SelectMany</span><span class="sxs-lookup"><span data-stu-id="b91f8-111">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="b91f8-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="b91f8-112">Example</span></span>  
 <span data-ttu-id="b91f8-113">Následující příklad používá <xref:System.Linq.Enumerable.SelectMany%2A> metodu pro výběr všech objednávek, kde `TotalDue` je méně než 500,00.</span><span class="sxs-lookup"><span data-stu-id="b91f8-113">The following example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom_mq)]  
  
### <a name="example"></a><span data-ttu-id="b91f8-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="b91f8-114">Example</span></span>  
 <span data-ttu-id="b91f8-115">Následující příklad používá <xref:System.Linq.Enumerable.SelectMany%2A> metodu pro výběr všech objednávek, kde byla objednávka vytvořena od 1. října 2002 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="b91f8-115">The following example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom2_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom2_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="b91f8-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b91f8-116">See also</span></span>

- [<span data-ttu-id="b91f8-117">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="b91f8-117">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
