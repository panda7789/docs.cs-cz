---
title: 'Příklady syntaxe dotazů založených na volání metody: projekce'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 505491fa-5920-43ce-8a96-c25389e125d8
ms.openlocfilehash: 81484f729b2282678b3fa1a92b5050cf7a502db5
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43739152"
---
# <a name="method-based-query-syntax-examples-projection"></a><span data-ttu-id="7015a-102">Příklady syntaxe dotazů založených na volání metody: projekce</span><span class="sxs-lookup"><span data-stu-id="7015a-102">Method-Based Query Syntax Examples: Projection</span></span>
<span data-ttu-id="7015a-103">Příklady v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Select%2A> a <xref:System.Linq.Enumerable.SelectMany%2A> methodsto dotaz [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) pomocí syntaxe dotazů založených na volání metody.</span><span class="sxs-lookup"><span data-stu-id="7015a-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methodsto query the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="7015a-104">Model prodeje AdventureWorks používá v těchto příkladech je sestaven z tabulky kontaktu, adresa, produktu, SalesOrderHeader a podrobnosti prodejní objednávky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="7015a-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="7015a-105">V příkladech v tomto tématu se používá následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="7015a-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="select"></a><span data-ttu-id="7015a-106">Vyberte</span><span class="sxs-lookup"><span data-stu-id="7015a-106">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="7015a-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="7015a-107">Example</span></span>  
 <span data-ttu-id="7015a-108">V následujícím příkladu <xref:System.Linq.Queryable.Select%2A> metoda do projektu `Product.Name` a `Product.ProductID` vlastnosti na sekvenci anonymních typů.</span><span class="sxs-lookup"><span data-stu-id="7015a-108">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to project the `Product.Name` and `Product.ProductID` properties into a sequence of anonymous types.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
### <a name="example"></a><span data-ttu-id="7015a-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="7015a-109">Example</span></span>  
 <span data-ttu-id="7015a-110">V následujícím příkladu <xref:System.Linq.Enumerable.Select%2A> metody k vrácení sekvence pouze názvy produktů.</span><span class="sxs-lookup"><span data-stu-id="7015a-110">The following example uses the <xref:System.Linq.Enumerable.Select%2A> method to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple2_mq)]
 [!code-vb[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple2_mq)]  
  
## <a name="selectmany"></a><span data-ttu-id="7015a-111">Operátor SelectMany</span><span class="sxs-lookup"><span data-stu-id="7015a-111">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="7015a-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="7015a-112">Example</span></span>  
 <span data-ttu-id="7015a-113">V následujícím příkladu <xref:System.Linq.Enumerable.SelectMany%2A> metody, chcete-li vybrat všechny objednávky where `TotalDue` je menší než 500,00.</span><span class="sxs-lookup"><span data-stu-id="7015a-113">The following example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom_mq)]  
  
### <a name="example"></a><span data-ttu-id="7015a-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="7015a-114">Example</span></span>  
 <span data-ttu-id="7015a-115">V následujícím příkladu <xref:System.Linq.Enumerable.SelectMany%2A> pro výběr všech objednávek, ve kterém bylo provedeno pořadí 1. října 2002 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="7015a-115">The following example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom2_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom2_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="7015a-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="7015a-116">See Also</span></span>  
 [<span data-ttu-id="7015a-117">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="7015a-117">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
