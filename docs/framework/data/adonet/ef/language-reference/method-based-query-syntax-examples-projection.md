---
title: "Příklady syntaxe dotazů metoda: projekce"
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
ms.assetid: 505491fa-5920-43ce-8a96-c25389e125d8
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 10bc53be82e899bb9673f76474d9847eb94139a4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="method-based-query-syntax-examples-projection"></a><span data-ttu-id="61886-102">Příklady syntaxe dotazů metoda: projekce</span><span class="sxs-lookup"><span data-stu-id="61886-102">Method-Based Query Syntax Examples: Projection</span></span>
<span data-ttu-id="61886-103">V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Select%2A> a <xref:System.Linq.Enumerable.SelectMany%2A> methodsto dotaz [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) pomocí syntaxe dotazu na základě metod.</span><span class="sxs-lookup"><span data-stu-id="61886-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methodsto query the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="61886-104">Model prodeje společnosti AdventureWorks použít v těchto příkladech je sestaven z kontaktu, adresu, produktu, SalesOrderHeader a podrobnosti prodejní objednávky tabulky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="61886-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="61886-105">V příkladech v tomto tématu použijte následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="61886-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="select"></a><span data-ttu-id="61886-106">Vyberte</span><span class="sxs-lookup"><span data-stu-id="61886-106">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="61886-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="61886-107">Example</span></span>  
 <span data-ttu-id="61886-108">Následující příklad používá <xref:System.Linq.Queryable.Select%2A> metoda do projektu `Product.Name` a `Product.ProductID` vlastnosti do posloupnost anonymní typy.</span><span class="sxs-lookup"><span data-stu-id="61886-108">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to project the `Product.Name` and `Product.ProductID` properties into a sequence of anonymous types.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
### <a name="example"></a><span data-ttu-id="61886-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="61886-109">Example</span></span>  
 <span data-ttu-id="61886-110">Následující příklad používá <xref:System.Linq.Enumerable.Select%2A> metoda vrátí posloupnost pouze názvy produktů.</span><span class="sxs-lookup"><span data-stu-id="61886-110">The following example uses the <xref:System.Linq.Enumerable.Select%2A> method to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple2_mq)]
 [!code-vb[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple2_mq)]  
  
## <a name="selectmany"></a><span data-ttu-id="61886-111">Označit více</span><span class="sxs-lookup"><span data-stu-id="61886-111">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="61886-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="61886-112">Example</span></span>  
 <span data-ttu-id="61886-113">Následující příklad používá <xref:System.Linq.Enumerable.SelectMany%2A> metoda vyberte všechny řadí kde `TotalDue` je menší než 500,00.</span><span class="sxs-lookup"><span data-stu-id="61886-113">The following example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom_mq)]  
  
### <a name="example"></a><span data-ttu-id="61886-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="61886-114">Example</span></span>  
 <span data-ttu-id="61886-115">Následující příklad používá <xref:System.Linq.Enumerable.SelectMany%2A> metoda vyberete všechny objednávky, kde byla provedena pořadí na 1. října 2002 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="61886-115">The following example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom2_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom2_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="61886-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="61886-116">See Also</span></span>  
 [<span data-ttu-id="61886-117">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="61886-117">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
